# Aprenda Domain Driven Design: Alinhando arquitetura de software e estratégia de negócio

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
### Capítulo 5
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


