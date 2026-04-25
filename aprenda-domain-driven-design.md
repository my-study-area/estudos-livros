# Aprenda Domain Driven Design: Alinhando arquitetura de software e estratégia de negócio
Exemplos de código do livro: https://github.com/forks-projects/learning-ddd

Wolfdesk: gestão de tickets de help desk    
- cobra pelo número de tickets e não pelo número de usuários
- utiliza um algoritmo para fechar tickets automaticamente e tem sistema detecção de fraudes
- "suporte em piloto automático": tenta encontrar um solução adequada com base no histórico
- sistema de autenticação e autorização
- administração de categorias para o tickets
- permite inserção de cronogramas de turnos para equipe de suporte
- escala de forma elastica utilizando computação sem servidor (serverless)


## Parte I
### Capítulo 1
- design estratégico
  - domínio
    - subdomínio principal
    - subdomínio genérico
    - subdomínio suporte
- design tático

### Capítulo 2
- linguagem ubíqua: liguagem comum utilizada entre pessoas técnicas e de negócio. Como ferramentas podemos utilizar uma wiki, a linguagem gherkin e NDpend para verificar o uso de termos da linguagem ubíqua.
- modelo: representação do mundo real, por exemplo, todo mapa é um modelo. A representação de negócio dos especialistas têm como resultado um modelo de negócio.


### Capítulo 3
Inconsistência:
- lead no marketing: receber informações de um cliente
- lead no departamento de vendas: todo o ciclo do processo de vendas
- Uma solução é trazer o modelo simples do marketing para a vendas ou o complexo de vendas para o marketing, mas ambos trazem problemas. Outra solução é adicionar uma palavra no final de cada item: lead de marketing e lead de vendas. O lado ruim, é que aumenta a carga cognitiva e o modelo de negócio estará diferente da linguagem obiqua.
- Contexto delimitado: é a ferramenta do design estratégico que organiza a complexidade do software ao separar grandes problemas em "caixas" menores e independentes.
- uma equipe pode trabalhar com um ou mais contextos delimitados, mas duas equipes não podem trabalhar num mesmo contexto delimitado


### Capítulo 4
comunicação e integração de contexto delimitado
- cooperação
  - padrão parceria: equipes se cooperam e se adaptam - sem dramas ou conflitos
  - padrão de núcleo compartilhado: contextos delimitados compartilham um mesmo modelo compartilhado
- cliente-fornecedor:
  - conformista: O cliente aceita o modelo do fornecedor sem mudanças.
  - camada anti-corrupção: O cliente traduz o modelo do fornecedor para o seu próprio modelo para não se "sujar".
  - Serviço de host aberto - Open Host Service (OHS): O fornecedor expõe uma "Linguagem Publicada" (contrato estável) para que múltiplos clientes possam se integrar de forma uniforme.
- caminhos separados:

Mapa de contexto: é a representação visual das relações e integrações entre os diferentes Contextos Delimitados (Bounded Contexts) de um sistema. É a fotografia estratégica do sistema. Ele não mostra tabelas ou classes, mas sim como os Bounded Contexts estão ligados e qual o nível de acoplamento (técnico e organizacional) entre eles.

## Parte II
### Capítulo 5 - Implementando uma lógica de negócio simples
- script de tranasação (transcation script): organiza a lógica de negócio em que cada procedimento lida com uma única solicitação de apresentação (Martin Fowler). O comportamento do procedimento é manter consistente em caso de sucesso e falha, isso significa que no caso de falha, deve reverter ou executar ações compensatórias.
  - Focado no processo. Um método faz tudo (lógica + banco). Ideal para fluxos lineares em subdomínios de baixo valor.
  - utilizado em subdomínio genérico e subdomínio de suporte
```python
def criar_pedido(cliente_id, itens):
    cliente = db.buscar_cliente(cliente_id)
    
    if not cliente.ativo:
        raise Exception("Cliente inativo")

    pedido_id = db.inserir_pedido(cliente_id)

    for item in itens:
        db.inserir_item(pedido_id, item)

    return pedido_id


def criar_pedido():
    # tudo aqui dentro
```

- registro ativo: um objeto que envolve uma linha em uma tabela ou uma visão do banco de dados encapsula o acesso ao banco de dados e adiciona a lógica de domínio nesses dados (Martin Fowler)
  - Focado na estrutura. O objeto de dados tem métodos para persistência (Save, Update). Ideal para CRUDs em subdomínios de suporte onde a estrutura do banco é o espelho do negócio.
  - utilizado em subdomínio de suporte
  - Muito comum em frameworks (ex: ORM)
```python
class Pedido:
    def __init__(self, cliente):
        self.cliente = cliente
        self.itens = []

    def adicionar_item(self, item):
        self.itens.append(item)

    def salvar(self):
        if not self.cliente.ativo:
            raise Exception("Cliente inativo")

        db.inserir_pedido(self)

pedido = Pedido(cliente)
pedido.adicionar_item(item)
pedido.salvar()
```


## Capítulo 6 - Lidando com a Lógica de Negócio Complexa
- Modelo de domínio
  - invariantes: regras de negócio que devem ser cumpridas o tempo todo
  - padrões táticos do DDD: agregações, objetos de valor, eventos de domínio e serviços de domínio
### Blocos de construção
- objetos de valor: Não tem uma propriedade de identificação. O conjunto das propriedades combinadas, diferenciam um objeto de outro. Ao alterar uma das propriedades já torno um objeto de valores diferente de outros. Evite sempre usar tipos primitivos para todas as propriedades.
- entidades: Utiliza um identificador. A entidade é mutável.
- agregados: é uma entidade, uma hierarquia de entidades que compartilham um limite transacional. 
  - devem garantir as invariantes e regras de negócio
  - garantir a simultaneidade através de transações do banco de dados. No livro é apresentado o lock otimista, onde uma transação não é bloqueada ao utilizar uma coluna no banco de dados. Para isso, é realizado o versionamento do registro do banco dados utilizando uma coluna no banco de dados. Sempre que for realizada uma atualização, é necessário passar o identificador do agregado e um versionamento, normalmente recuperado em tempo de execução. O registro somente é atualizado quando atender a esta condição:
```sql
UPDATE tickets 
SET ticket_status = @new_status, 
    agg_version = agg_version + 1
WHERE ticket_id = @id AND agg_version = @expected_version;
```
  - transação atômica
  - hierarquia de entidades:
  - referência a outros agregados: dados eventualmente consistentes
  - raiz do agregado: é a entidade principal que esconde do mundo externo as entidades que fazem parte do agregado. Toda mudança deve passar pela raiz do agregado, protegendo que alterações não respeitem as invariantes e regras de negócio. Uma atualização de valor somente deve ocorrer passando pela raiz do agregado.
  - eventos de domínio: é uma mensagem que descreve um evento significativo que ocorreu no domínio de negócio: ticket atribuído, ticket escalonado e mensagem recebida.
- serviços de domínio: lógica de negócio que não pertence ao agregado e nem objetos de valor. Ou relevante para multiplos agregados. É um objeto sem estados que implementa lógica de negócios.
- administando a complexidade: os agregados e objetos de valor tratam a complexidade das regras de negócio. Uma estrutura de dados (classe) que possui mais elementos de dados (limites) é mais complexa. No livro apresenta duas classes, uma tem diversos atributos e outro somente 2. A classe com somente 2 atributos é menos complexa porque possui menos atributos (limites) mesmo que possua uma lógica maior devidos as invariantes, mas têm apenas 2 atributos (limites) que podem ser modificados.


> relembrando sobre o design estratégico, neste momento estamos falando de um subdomínio principal, onde existe uma lógica de negócio complexa e traz uma vantagem competitiva em relação a seus concorrentes. Neste cenário estamos trazendo a abordangem do design tático utilizando o modelo de domínio. Já passamos por outras duas lógicas de negócio simples: transação de scripts e registro ativo.

code smell: https://wiki.c2.com/?PrimitiveObsession



**Entidade não é um "bloco independente"?**    
Este é o "pulo do gato" do Khononov. Em outros livros de DDD, a Entidade é apresentada como algo que você cria sozinho. O Khononov diz que **não implementamos entidades sozinhas**, mas dentro de um **Agregado**.

**Por que isso?**    
Imagine uma Entidade `ItemPedido` e uma Entidade `Pedido`.
* Se você pudesse alterar o `ItemPedido` diretamente, sem passar pelo `Pedido`, você poderia corromper a regra de negócio (ex: o valor total do pedido ficaria errado).
* Portanto, a Entidade só faz sentido dentro de uma fronteira de consistência chamada **Agregado**. O Agregado é o "pai" que protege suas entidades filhas.



**Diferença entre invariante e regra de negócio**    
1. Invariante (O "Sempre" do Sistema)
Uma **invariante** é uma regra de negócio que **não pode ser violada em nenhum momento**. Ela define a integridade básica do Agregado. Se uma invariante for quebrada, o estado do objeto é considerado "corrompido" ou inválido.

* **Foco:** Consistência e Proteção.
* **Onde fica:** Dentro do Agregado
* **Exemplo:** "O saldo de uma conta nunca pode ser negativo" ou "Um pedido não pode ter zero itens". 
* **No código:** O método `AddMessage` na imagem deveria verificar se o `body` está vazio. Se estiver, ele lança uma exceção. Essa é uma proteção de invariante.

2. Regra de Negócio (A Lógica de Fluxo)
Uma **regra de negócio** é um conceito mais amplo. Ela descreve *como* o negócio funciona, as políticas e os cálculos. Algumas regras de negócio podem mudar dependendo do contexto ou do tempo, enquanto as invariantes costumam ser mais rígidas.

* **Foco:** Comportamento e Decisão.
* **Exemplo:** "Se o cliente for VIP, dê 10% de desconto" ou "Se o ticket não for resolvido em 24h, escalone para o gerente".
* **No código:** Na imagem, o método `Escalate` (linha 01 do segundo bloco) aplica uma regra de negócio de escalonamento baseada em uma razão.

Analogia para não esquecer (O Avião)

Imagine que estamos modelando um **Avião**:

* **Invariante:** "O avião não pode decolar com as portas abertas." (Se isso acontecer, o sistema está num estado perigoso/inválido. O Agregado `Aviao` garante isso no método `Decolar()`).
* **Regra de Negócio:** "O valor da passagem para crianças tem 50% de desconto." (É uma regra de como o negócio opera, mas se o desconto for aplicado errado, o avião ainda voa com segurança; o estado técnico do sistema não está corrompido, apenas a regra comercial falhou).



