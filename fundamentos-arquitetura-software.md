# fundamentos-arquitetura-software
Escrito por Mark Richards e Neal Ford

- Material complementar: https://fundamentalsofsoftwarearchitecture.com/

# Capítulo 1 : Introdução
Citação de Martin Fowler sobre a definição da profissão de arquiteto de software:
> Arquitetura é sobre algo importante… seja lá o que for. — Ralph Johnson

Por que não existe uma trajetória para os arquitetos de software?
- Primeiro: não existe uma boa definição
- Segundo: de acordo com o mapa mental demostrado no livro, o profissional incorpora uma enorme quantidade de dominos e responsabilidades e continua a expandir
- Terceiro: devido a evolução rápida do ecossistema de desenvolvimento de software, ficará desatualiza futuramente
- Quarto: grande parte do material tem apenas relevância histórica


## Definindo a arquitetura de software
Ao pergunta para um arquiteto para descrever uma arquitetura, ele responde:
> "É uma arquitetura de microserviços"
- arquitetura do sistema e estrutura do sistema são diferentes: a frase está dizendo somente da estrtura

### Estruturas
Tipos de estruturas:
- microsserviços
- arquitetura em camadas
- microkernel


### Características
São os atributos que o sistema deve suportar como:
- Disponibilidade
- Confiabilidade
- Testabilidade
- Escalabilidade
- Segurança
- Agilidade
- Tolerância a falhas
- Elasticidade
- Recuperabilidade
- Desempenho
- Implementabilidade
- Capacidade de aprendizagem

<details>
    <summary>Gerado por IA</summary>

    ### Diferença entre Arquitetura e Estrutura
    De acordo com o texto explicativo dos autores:

    * **Estrutura (O "Como se organiza"):** É apenas o **estilo de arquitetura** no qual o sistema está sendo implementado. Ela dita a disposição física e lógica dos componentes. Exemplos de estruturas comuns citados são: *microsserviços, arquitetura em camadas (layered)* ou *microkernel (plug-ins)*. O texto enfatiza que se você perguntar a um arquiteto sobre a arquitetura e ele responder apenas "é uma arquitetura de microsserviços", ele está descrevendo **apenas a estrutura**, e não a arquitetura em sua totalidade.
    * **Arquitetura (A "Visão Holística"):** É o conjunto completo. A arquitetura engloba a **estrutura**, mas a ela soma-se obrigatoriamente o conhecimento das **características da arquitetura** (as necessidades de negócio e atributos de qualidade do sistema), as **decisões arquiteturais** (as restrições técnicas impostas) e os **princípios de design** (as diretrizes de desenvolvimento).

    **Em resumo:** A estrutura é uma parte contida dentro da arquitetura. Descrever um sistema unicamente por sua estrutura (ex: "é orientado a microsserviços") é um erro comum, pois falha em exibir a arquitetura em sua totalidade e o contexto real de funcionamento e decisões do sistema.
</details>



### Decisões de arquitetura
- restrições de como um sistema deve ser construído, por exemplo, somente camadas de serviço devem acessar o banco de dados

> uma restrição (regra) pode ser quebrada por uma **variância**


### Princípios de design
- Princípio: utilizado para orientar
- diretriz: é obrigatória, uma regra


<details>
  <summary>Gerado por IA</summary>

  ### O Conceito em Linhas Gerais
  Pense nas decisões de arquitetura como as **leis** de um país (regras rígidas que precisam ser seguidas) e nos princípios de design como os **manuais de boas maneiras** ou **diretrizes** (orientações que mostram o caminho preferencial, mas dão margem para adaptação).

  Um princípio de design não dita exatamente *como* fazer algo com uma regra de ferro, mas define uma *intenção clara* para guiar os desenvolvedores no dia a dia, permitindo que eles escolham a melhor ferramenta para o contexto específico.

  ---

  ### A Visão dos Autores (Richards & Ford)
  Como mostramos na **Figura 1-6**, a arquitetura de software é sustentada por quatro pilares fundamentais: a estrutura, as características de arquitetura (os "ilities"), as decisões de arquitetura e, finalmente, os **princípios de design**.

  Para nós, a diferença crucial está na flexibilidade:

  * **Decisão de Arquitetura (Regra):** É mandatória. Se a regra diz "cada microsserviço deve ter seu próprio banco de dados", o desenvolvedor não pode criar um banco compartilhado.
  * **Princípio de Design (Diretriz):** É orientador. Como no exemplo da imagem: *"Sempre que possível, utilize a mensageria assíncrona entre os serviços para aumentar o desempenho"*.
</details>


## Expectativas de um arquiteto
- No lugar de focar na função de um arquiteto de software, é recomendado focar nas expectativas de um arquiteto:
- Tomar decisões de arquitetura 
- Analisar continuamente a arquitetura 
- Manter-se atualizado com as últimas tendências 
- Assegurar a conformidade com as decisões 
- Exposição e experiência diversificadas 
- Ter conhecimento sobre o domínio do negócio 
- Ter habilidades interpessoais 
- Entender e lidar bem com questões políticas



### Tomar decisões de arquitetura
> Um arquiteto deve estabelecer as decisões (regras) da arquitetura e os princípios (orientações) do design usados para orientar as decisões de tecnologia dentro da equipe, do departamento ou em toda a empresa.


<details>
  <summary>Gerado por IA</summary>

  ### O Conceito em Linhas Gerais
  Em termos simples, o papel do arquiteto de software não é ditar rigidamente cada ferramenta que os desenvolvedores devem usar, mas sim criar as **regras do jogo** e dar uma **direção clara**.

  Pense no arquiteto como um planejador urbano: ele define as zonas residenciais e as vias expressas (a estrutura e os princípios), mas deixa os construtores escolherem os tijolos e acabamentos específicos (as escolhas técnicas do dia a dia).

  ---

  ### A Visão dos Autores (Richards & Ford)

  Mark Richards e Neal Ford defendem que a principal missão do arquiteto nesta primeira expectativa é **orientar, não especificar**.

  * **Decisão Técnica vs. Decisão Arquitetural:** Escolher uma biblioteca específica (como o *React.js*) de forma isolada é apenas uma decisão técnica. A decisão arquitetural ideal é definir uma diretriz genérica — por exemplo, exigir o uso de um *framework reativo para o front-end* — dando autonomia para a equipe escolher a melhor ferramenta (React, Angular, Vue, etc.) dentro desse limite.
  * **O Segredo da Decisão Eficiente:** Os autores propõem uma pergunta-chave para testar suas decisões: *Esta regra está ajudando a guiar o time a fazer a escolha certa ou está simplesmente tirando o poder de escolha deles?*
  * **A Exceção Justificável:** Há momentos em que o arquiteto precisa, sim, cravar uma tecnologia específica. No entanto, isso só deve acontecer se essa ferramenta for estritamente necessária para garantir uma **característica de arquitetura** vital (os chamados "-ilidades"), como garantir alta escalabilidade, desempenho crítico ou disponibilidade do sistema. Nesse cenário, vira uma decisão de arquitetura legítima.
</details>




### Analisar continuamente a arquitetura
> Um arquiteto deve analisar continuamente a arquitetura e o ambiente de tecnologia atual, para então recomendar soluções de melhorias.


<details>
  <summary>Gerado por IA</summary>

  ### O Conceito em Linhas Gerais
  Sistemas de software envelhecem. Analisar continuamente a arquitetura significa que o trabalho do arquiteto não termina quando o sistema vai para o ar. Trata-se do esforço constante de olhar para o ecossistema atual e garantir que a estrutura criada no passado ainda faça sentido hoje, evitando que o sistema se degrade e se torne obsoleto diante de novas tecnologias ou mudanças no negócio.

  ---

  ### A Visão dos Autores (Richards & Ford)

  * **Vitalidade da Arquitetura:** Uma arquitetura definida há alguns anos pode perder a validade devido a novas demandas de mercado ou evoluções tecnológicas. Avaliar essa vitalidade garante que o software continue viável e funcional.
  * **Prevenção da Decadência Estrutural:** Alterações diárias feitas no código ou no design pelos desenvolvedores podem, sem querer, destruir características cruciais do sistema (como desempenho, disponibilidade e escalabilidade). O arquiteto precisa monitorar isso de perto para evitar que a estrutura colapse.
  * **Olhar Além do Código:** A análise contínua também exige atenção aos ambientes de teste e de implantação (*deployment*). Não adianta o código ser flexível se o time leva semanas para testar ou meses para lançar uma nova versão; a agilidade deve ser integrada e de ponta a ponta.
  * **Manutenção da Relevância:** O arquiteto deve estudar de forma integral as mudanças técnicas e o domínio do problema para manter as aplicações robustas e competitivas no mercado.
</details>




### Manter-se Atualizado com as Últimas Tendências
- desenvolvedores devem ficar atualizados para se manterem relevantes
- arquitetos devem se atualizar com tendência técnica e do setor



### Assegurar a conformidade com as decisões
- conformidade é verificar/fiscalizar se o que foi decidido continua sendo obedecido/respeitado

<details>
  <summary>Gerado por IA</summary>

  ### O Conceito em Linhas Gerais

  Assegurar a conformidade significa garantir que o código construído no dia a dia esteja alinhado com as regras estruturais que foram combinadas para o projeto. Em um paralelo simples, o arquiteto cria a planta e as regras de segurança de um prédio; assegurar a conformidade é fiscalizar a obra para garantir que ninguém derrube uma parede mestre ou use materiais que coloquem a estrutura em risco.

  ---

  ### A Visão dos Autores (Richards & Ford)

  * **Verificação Contínua:** O arquiteto precisa acompanhar constantemente se os times de desenvolvimento estão seguindo as decisões de arquitetura e os princípios de design previamente documentados e comunicados.
  * **Visão de Curto Prazo vs. Longo Prazo:** É comum que desenvolvedores queiram quebrar regras arquiteturais por motivos imediatos (como acessar o banco de dados direto da tela para poupar tempo ou ganhar desempenho pontual). Porém, o arquiteto foca no longo prazo, isolando camadas para garantir que mudanças futuras no banco não quebrem a interface.
  * **Consequência das Violações:** Permitir o descumprimento dessas regras faz com que o sistema perca os atributos fundamentais planejados (como manutenibilidade ou segurança), resultando em uma aplicação que não funciona como esperado.

</details>




### Exposição e experiência diversificadas
- estar familiarizado com diversas tecnologias
- concentrar na amplitude, não na profundidade técnica
- amplitude é o que você sabe, mas não quer dizer que domina profundamente
- para um arquiteto, a especialidade numa tecnologia é algo negativo




### Ter conhecimento sobre o domínio do negócio
- ajuda na comunicação com os usuários do negócio e os stakeholders
- arquiteto bem sucedido tem conhecimento técnico, prático e um bom conhecimento no domínio
- consegue se comunicar com executivos da diretoria e usuários comerciais



### Ter habilidades interpessoais
- habilidade de liderança é metade do que é necessário para se tornar um arquiteto eficiente
- essa característica ajuda a se diferenciar dentro de um conjunto de profissionais
- ajuda a liderar, treinar e aconselhar desenvolvedores e de comunicar com eficiência ideias, decisões e princípios.



### Entender e lidar com questões políticas
<details>
  <summary>Gerado por IA</summary>

  ## O Conceito em Linhas Gerais

  No dia a dia do desenvolvimento de software, quem programa costuma ter autonomia para tomar decisões técnicas locais (como escolher um padrão de projeto ou organizar as classes) sem precisar de aprovação superior. No entanto, quando passamos para o papel de **arquitetura de software**, o cenário muda drasticamente.

  Neste nível, quase todas as decisões técnicas impactam custos, prazos, outras equipes e o próprio negócio. Por isso, gerenciar expectativas significa entender que as suas decisões serão constantemente questionadas e que você precisará navegar pela **política corporativa** e dominar a **negociação** para conseguir implementar o que o sistema precisa.

  ---

  ### A Visão dos Autores (Richards & Ford)

  De acordo com a nossa abordagem na obra, a capacidade de lidar com as expectativas e com a política da empresa baseia-se nos seguintes pilares fundamentais:

  * **Toda Decisão Será Questionada:** Diferente do desenvolvedor, cujas escolhas de código passam quase invisíveis pela diretoria, as decisões do arquiteto afetam o ecossistema da empresa. Stakeholders, gerentes de projeto e desenvolvedores vão questionar suas propostas devido ao aumento de custos, tempo ou mudanças no fluxo de trabalho.
  * **O Clima Político da Empresa:** O arquiteto precisa entender o cenário político em que está inserido. Mudar a estrutura de um banco de dados ou isolar uma aplicação (criando silos para maior segurança, por exemplo) gera atritos com outros times que dependem daquele recurso. Saber lidar com essas tensões é parte essencial do papel.
  * **Negociação como Habilidade Vital:** Como você terá que justificar e lutar por praticamente cada decisão arquitetural importante, as habilidades de negociação e liderança tornam-se tão essenciais quanto o conhecimento técnico de código. É preciso argumentar e buscar aprovação de forma estratégica para mitigar as frustrações do cargo.




  ### O Exemplo dos Silos de Aplicação

  Imagine que um arquiteto cuida de um grande sistema de CRM e percebe que o acesso direto ao banco de dados por outros sistemas externos está a comprometer a segurança, o controlo e a flexibilidade para futuras mudanças no esquema.

  Para resolver este problema de engenharia, o arquiteto decide adotar uma estratégia de **silos de aplicação**, onde:

  * **Isolamento dos Dados:** Cada base de dados passa a ser acessível *única e exclusivamente* através da aplicação que a possui.
  * **Barreira de Acesso:** Qualquer outro sistema que precise de dados do CRM já não pode fazer consultas diretas à base de dados; agora é obrigado a solicitar as informações através de chamadas de acesso remoto (como APIs REST ou SOAP).

  ### O Impacto Político da Decisão

  Embora a criação de silos de aplicação traga benefícios claros de segurança e governança para o arquiteto, ela gera um impacto negativo imediato nas outras equipas da empresa.

  Essa decisão será fortemente questionada por quase todos porque:

  1. **Aumento de Esforço e Tempo:** As outras equipas de desenvolvimento terão de reescrever os seus códigos para substituir as consultas diretas por chamadas de API complexas.
  2. **Conflito de Interesses:** O que resolve o problema do arquiteto (segurança e controlo) cria novos problemas para os gestores e donos do produto (atrasos nas entregas e aumento de custos).

  Este cenário ilustra exatamente por que razão o arquiteto não pode ser apenas um técnico: ele precisa de usar a **política** e a **negociação** para justificar a necessidade do isolamento dos dados (os silos) e convencer os *stakeholders* de que o benefício a longo prazo supera o desconforto e o custo imediato.
</details>





## Inserçao da arquitetura e ...
<details>
  <summary>Gerado por IA</summary>

  Olá! Que excelente trecho para analisarmos. O que você acabou de trazer toca em uma das mudanças mais profundas que a nossa área sofreu nos últimos anos: a união definitiva entre o desenho do sistema (**Arquitetura**) e como ele roda de verdade (**Operações/DevOps**).

  Vamos desmistificar esse ponto crucial do livro.

  ---

  ### O Conceito em Linhas Gerais

  Antigamente, o arquiteto de software desenhava o sistema em um papel e "jogava o código por cima do muro" para a equipe de infraestrutura se virar para manter o sistema online. Era uma relação puramente burocrática e baseada em contratos.

  Hoje, com o avanço da nuvem e de modelos como os microserviços, as barreiras caíram. O arquiteto precisa projetar o software já pensando em como ele vai escalar, falhar e se recuperar automaticamente em produção. **Arquitetura e DevOps agora andam de mãos dadas.**

  ---

  ### A Visão dos Autores (Richards & Ford)

  Nós defendemos que o escopo do arquiteto moderno expandiu drasticamente. Não dá mais para ignorar o ambiente de execução.

  * **A Era Contratual (O Passado):** As empresas terceirizavam a infraestrutura para evitar dor de cabeça. A arquitetura se limitava a exigir metas em contratos (como *"o sistema precisa aguentar 99% de tempo de atividade"*), sem se preocupar em *como* o código ajudaria nisso.
  * **A Era DevOps e Microserviços (O Presente):** Características arquiteturais complexas (como **escala elástica** — a capacidade do sistema de aumentar ou diminuir de tamanho sozinho conforme o número de acessos) agora são resolvidas diretamente no código e nas configurações de deploy, de forma automatizada.
  * **Responsabilidade Compartilhada:** Para que uma arquitetura moderna funcione, arquitetos e engenheiros de DevOps precisam trabalhar juntos desde o primeiro dia. Preocupações operacionais tornaram-se decisões de design de software.
</details>




## Práticas da engenharia
- processo: fluxo de trabalho de uma organização, como empresas são formadas, como reuniões são feitas
- práticas: integração contínua (CI), práticas idependentes do processo
- práticas da XP (Extreme programming)
  a. teste
  b. integração contínua (CI)
  c. automação
  d. continuos delivery (CD)

> "... como sabemos, existem conhecimentos conhecidos; existem coisas que sabemos que sabemos. Também sabemos que existem incógnitas conhecidas, ou seja, sabemos que existem coisas que não sabemos. Mas também existem as incógnitas desconhecidas, aquelas que não sabemos que não sabemos."
> — Ex-secretário de Defesa dos EUA, Donald Rumsfeld

- adotar práticas de engenharia ágil, como a integração contínua, o provisionamento de máquina automatizado e práticas semelhantes, facilita criar arquiteturas resilientes, além de mostrar o quanto a arquitetura se torna interligada com as práticas de engenharia.



## Operações/DevOps
> Um axioma é uma verdade evidente por si mesma que não precisa de prova, servindo como base ou ponto de partida indiscutível para a construção de qualquer raciocínio, teoria ou sistema.

Exemplos:
- "o software deve ser manutenível"
- "a segurança não é opcional"

- Há alguns anos, questões arquiteturais que envolviam questões operacionais lidavam com a escala elástica. A complexidade de adição ou remoção de processamento era cuidar internamente gerando **uma arquitetura muito mais complexa**.
- Os criadores do estilo de microsserviços perceberam que questões operacionais eram melhores para tratar esses problemas. Arquitetor e profissionais de operações se juntaram para criar os microsserviços.



## Processo
- alguns anos atrás, o processo de criação de software tem pouco impacto na arquitetura de software (estrutura)
- no desenvolvimento moderno, provou o contrário: a forma como você trabalha impacta diretamente a flexibilidade e a evolução da sua arquitetura.


<details>
  <summary>Gerado por IA</summary>

  ### O Conceito em Linhas Gerais

  Historicamente, as pessoas acreditavam que o método usado para gerenciar um projeto (seja ele uma metodologia tradicional/Cascata ou Ágil) não mudava a estrutura final do código. Dizia-se que o processo era **ortogonal** (independente) à arquitetura.

  No entanto, o desenvolvimento moderno provou o contrário: a forma como você trabalha impacta diretamente a flexibilidade e a evolução da sua arquitetura.

  ---

  ### A Visão dos Autores (Richards & Ford)

  Como autores do livro, defendemos que essa separação total é uma ilusão. O processo molda a arquitetura de duas formas principais:

  * **Ciclos de Feedback Rápidos:** Em metodologias ágeis, o desenvolvimento iterativo permite que os arquitetos testem decisões arquiteturais mais cedo. Se uma escolha der errado, o feedback rápido permite corrigir a rota sem um custo catastrófico.
  * **Suporte a Mudanças e Reestruturação:** Mudar de uma arquitetura para outra (como migrar de um Monolítico para Microsserviços) é muito mais viável com processos ágeis. Eles incentivam práticas de engenharia modernas, como:
  * **Padrão de Estrangulamento (Strangler Fig Pattern):** Substituir partes do sistema antigo gradativamente, em vez de refazer tudo do zero.
  * **Alternância de Recursos (Feature Toggles):** Ativar ou desativar funcionalidades em tempo de execução para testar o comportamento do sistema de forma segura.



  > **Resumo da ópera:** Toda arquitetura se torna iterativa com o tempo. Processos que abraçam o feedback contínuo ajudam a criar arquiteturas mais resilientes e adaptáveis a mudanças.
</details>




## Dados
- código fonte e dados tem uma relação simbiótica: um não é útil sem o outro
- quantum arquitetural: (Architectural Quantum): Este é um conceito central do nosso livro. O quantum é a menor unidade de uma arquitetura que pode funcionar de forma independente. Como os bancos de dados costumam ligar várias partes do sistema, eles determinam fortemente o acoplamento e o tamanho desse quantum



## Leis da arquitetura de software
> Tudo na arquitetura de software é uma concessão. — Primeira Lei da Arquitetura de Software

- concessão é, essencialmente, o ato de ceder, permitir ou dar algo a alguém, mas o seu significado exato muda dependendo do contexto em que é usada. Na engenharia de software, uma concessão (frequentemente chamada pelo termo em inglês, trade-off) é a decisão consciente de abrir mão de uma qualidade ou benefício do sistema para obter outro que é mais crítico para o projeto no momento.

> Se um arquiteto pensa que descobriu algo que não é uma concessão, muito provavelmente ele ainda não a identificou. — Corolário 1


> O porquê é mais importante do que o como. — Segunda Lei da Arquitetura de Software


## Resumo
### Pilares fundamentais
> Quatro pilares fundamentais: a estrutura, as características de arquitetura (os "ilities"), as decisões de arquitetura e, finalmente, os **princípios de design**.
- estrutura: microsserviços, arquitetura em camadas etc
- características: escalabilidade, desempenho, resiliência e disponibilidade. Também conhecido como "ilities" plural no inglês que vêm de "ility" (scalability, availability, maintainability)
- decisões: é restrita. Ex: "Toda a nossa infraestrutura deve rodar exclusivamente na nuvem AWS"
- princípios: é flexível. Ex: "Prefira bancos de dados NoSQL orientados a documentos quando o esquema dos dados for altamente dinâmico.". O engenheiro tem a flexibilidade de escolher entre MongoDB, Couchbase, DynamoDB ou outro.

### Expectativas
É tudo o que se espera de um arquiteto de software
- Tomar decisões de arquitetura 
- Analisar continuamente a arquitetura 
- Manter-se atualizado com as últimas tendências 
- Assegurar a conformidade com as decisões 
- Exposição e experiência diversificadas 
- Ter conhecimento sobre o domínio do negócio 
- Ter habilidades interpessoais 
- Entender e lidar bem com questões políticas

### Leis da arquitetura de software:
1. Tudo na arquitetura de software é uma concessão. — Primeira Lei da Arquitetura de Software
2. O porquê é mais importante do que o como. — Segunda Lei da Arquitetura de Software



# PARTE I: Fundamentos
Para entender trade-offs, os desenvolvedores dever compreender conceits e componentes relacionados:
- terminomologia
- modularidade
- acomplamento
- conascência

> conascência: relacionado a acoplamento. A conascência (connascence) é uma métrica e conceito de arquitetura de software que mede o grau de dependência entre diferentes partes ou componentes de um sistema. Ela indica que, se uma mudança em um componente exige a modificação de outro para que o sistema continue funcionando, esses componentes são conascentes

> A conascência é um conceito que ajuda a entender e gerenciar o grau de dependência entre diferentes partes de um sistema de software. Se você já lidou com sistemas complexos, provavelmente já experimentou os desafios de manter componentes sincronizados em mudanças ou de evitar falhas causadas por pequenas alterações em módulos interdependentes. Conascência é sobre como partes do sistema estão “cientes” umas das outras — e quanto mais entendemos isso, mais controlamos a complexidade e melhoramos a manutenção do sistema

Fontes: 
- https://www.youtube.com/watch?v=dRlaLUkt7Wc&t=668s
- https://medium.com/@gustavoeyros/conasc%C3%AAncia-em-arquitetura-de-software-o-que-%C3%A9-e-por-que-importa-af84750e17fa


# Capítulo 2: Pensamento arquitetônico
- pensamento arquitetônico: o que pensa um dev e um arquiteto é diferente
Os quatro aspectos:
1. diferença de arquitetura e design
2. grande variedade de conhecimento técnico
3. entender, analisar e reconciliar  os trade-offs
4. entender motivação comercial e como se traduz em preocupação arquitetônica



## Arquitetura Versus Design
Arquitetura:
- identificar as características
- selecionar os padrões
- criar componentes

Design:
- criar diagrama de classes para cada componente
- criar telas de interface
- desenvolver
- testar

![](./assets/livro-fundamentos-arquitetura/cap-2-arquitetura-versus-design-2026-07-10_22-16.png)

- o modelo acima tem vários problemas como a separação de arquitetura do desenvolvedor que causam problemas na arquitetura
- decisões que algumas vezes os arquitetos tomam, não funcionam. Decisões que os desenvolvedores tomam, dificilmente voltam para o arquiteto.
- a solução é quebrar as barreiras entre eles e formar uma relação bidirecional 
![](./assets/livro-fundamentos-arquitetura/cap-2-fazendo-arq-funcionar-2026-07-10_22-25.png)

> não existe onde começa a arquitetura ou termina o design. Num projeto de software, sempre devem estar em sincronia.




## Amplitude técnica
- desenvolvedores devem ter _profundidade técnica_
- arquitetos devem uma grande _amplitude técnica_
![](./assets/livro-fundamentos-arquitetura/cap-2-piramide-conhecimento-2026-07-11_15-11.png)

- o que você sabe, o que você não sabe e o que você não sabe que não sabe
  a. o que você sabe: tecnologias, frameworks, liguagens de programação etc
  b. o que você não sabe: o que tem pouco conhecimento, ou conhecimento superficial
  c. o que você não sabe que não sabe: o conjunto das tecnologias e conhecimento que ele não sabe que existe e poderia resolver um problema
  - **profundidade**: é o que você domina, é o que você se especializa e tem um grande conhecimento. É o topo da pirâmide abaixo:
  ![](./assets/livro-fundamentos-arquitetura/cap2-2-piramide-desenvolvedor-2026-07-11_15-19.png)

- Para um arquiteto é vantajoso saber que existem 3 soluções do que ser especialista em uma solução.
![](./assets/livro-fundamentos-arquitetura/cap-2-piramide-arquiteto-2026-07-11_15-25.png)


- arquitetos devem ter mais amplitude e menos aprofundamento
![](./assets/livro-fundamentos-arquitetura/cap-2-amplitude-aprofundamento-arquiteto-2026-07-11_15-28.png)





## Analisando os trade-offs
- Pensar como arquiteto é identificar os trade-offs para determinar a melhor solução
- Tudo na arquitetura é um trade-off que gera aquela famosa resposta: "DEPENDE"
![](./assets/livro-fundamentos-arquitetura/cap-2-tradeoff-sistema-leilao-2026-07-11_15-49.png)

Tópico:

![](./assets/livro-fundamentos-arquitetura/cap-2-tradeoff-topico-2026-07-11_15-53.png)


Fila:

![](./assets/livro-fundamentos-arquitetura/cap-2-tradeoff-fila-2026-07-11_15-54.png)

No tópico, a solução se conecta com uma conexão. Na fila se conecta com 3 conexões.

trade-offs identificados entre as soluções:
- segurança: no tópico "qualquer pessos pode acessar". Na fila, só pode ser acessado pelos consumidores
- contrato homogêneos: no tópico, uma alteração afeta todos os consumidores. Na fila, somente o consumidor daquela fila sofre o impacto
- monitoramenteo e escalabilidade: no tópico, é complexo o controle de monitoramento e escalonamento devido ao uso genérico para diversos consumidores. Na fila, através do AMQP, permite o moniotoramento e escalagem de forma independente

> AMQP (Advanced Message Queuing Protocol)

<details>
  <summary>Gerado por IA</summary>

  Com base nas análises fundamentais que discutimos sobre as decisões de design, vamos estruturar o entendimento desse cenário clássico de mensageria: **Tópicos (Publish-Subscribe) vs. Filas (Point-to-Point)**.

  ---

  ## O Conceito em Linhas Gerais

  Imagine que você quer dar um aviso para várias pessoas.

  * **Abordagem de Tópico (Pub/Sub):** É como usar um alto-falante. Você fala uma vez só (publica) e qualquer um que estiver interessado pode sintonizar e ouvir (assinar). Se uma nova pessoa chegar, ela só precisa começar a escutar, sem que você precise falar diretamente com ela.
  * **Abordagem de Fila (Ponto a Ponto):** É como enviar cartas individuais. Se você precisa avisar três serviços, você escreve e envia três cartas diferentes, postando uma em cada caixa postal (fila) específica.

  ---

  ## A Visão dos Autores (Richards & Ford)

  Como arquitetos, não existe "solução perfeita", existem **trade-offs** (compensações). Vamos analisar o peso de cada escolha segundo os princípios do livro:

  ### 1. Vantagens do Modelo de Tópicos

  * **Extensibilidade Arquitetural:** Adicionar um novo serviço (como um histórico) é extremamente simples. O serviço produtor não precisa sofrer nenhuma modificação ou saber da existência do novo componente; o novo serviço apenas "assina" o tópico existente.
  * **Desacoplamento:** O emissor da mensagem é completamente agnóstico em relação a quem consome as informações ou como elas são usadas.

  ### 2. Desvantagens e Riscos do Modelo de Tópicos

  * **Segurança e Controle de Acesso:** Como o canal é aberto para assinantes, torna-se mais fácil para um serviço não autorizado "grampear" o tópico e ler os dados. Nas filas, o canal é restrito e exclusivo entre o produtor e aquele consumidor específico.
  * **Contratos Homogêneos:** Todos os consumidores do tópico precisam aceitar exatamente o mesmo formato de dados (o mesmo contrato). Se um novo serviço exigir um dado extra, o contrato de todos os outros serviços terá de mudar. Com filas individuais, cada canal pode ter seu próprio contrato customizado.
  * **Monitoramento e Escalabilidade Dinâmica:** Protocolos como o AMQP permitem monitorar o volume de mensagens de cada fila de forma independente e escalar os consumidores sob demanda. Em tópicos genéricos, esse controle granular e o auto-dimensionamento (auto-scaling) se tornam bem mais complexos.

  > **Frase de Impacto do Livro:** *"Os programadores conhecem os benefícios de tudo e os trade-offs de nada. Os arquitetos precisam entender ambos."* — Rich Hickey. A decisão final sempre dependerá de qual fator (extensibilidade ou segurança/contratos flexíveis) é a maior prioridade para o seu sistema atual.
</details>




## Entendendo as motivações comerciais
- traduzir requisitos das motivações comerciais em características como escalabilidade, disponibilidade, desempenho etc.

<details>
  <summary>Explicação sobre o termo motivação comercial</summary>

  No contexto da arquitetura de software, **motivação comercial** (ou *business driver*) refere-se aos objetivos estratégicos, metas financeiras e necessidades de negócio que uma empresa possui e que justificam a existência de um sistema.

  Em termos simples: o software não existe para ser tecnologicamente elegante; ele existe para resolver um problema de negócio ou gerar valor para a empresa.

  Abaixo, detalho como esse conceito funciona na prática:

  ### 1. O que são essas Motivações Comerciais?

  Elas partem do nível estratégico da empresa (os acionistas e diretores) e costumam responder a perguntas como:

  * **"Qual é a meta da empresa?"** (Ex: "Queremos expandir nossa operação para mais três países este ano").
  * **"Qual é o problema atual?"** (Ex: "Estamos perdendo vendas porque o sistema cai durante a Black Friday").
  * **"Como a empresa monetiza?"** (Ex: "Nosso lucro vem de transações rápidas em alta escala").

  ### 2. A Tradução: Negócio $\rightarrow$ Arquitetura

  O papel do arquiteto é pegar essa meta comercial (que está em linguagem de negócios) e traduzi-la em requisitos técnicos (as características da arquitetura). Por exemplo:

  | Motivação Comercial (Negócio) | Característica da Arquitetura (Técnico) |
  | --- | --- |
  | "Precisamos lançar novas funcionalidades toda semana para vencer a concorrência." | **Agilidade e Modulabilidade** (ex: arquitetura de microsserviços para deploys independentes). |
  | "A empresa vai investir muito em marketing e esperamos o triplo de acessos no próximo mês." | **Escalabilidade** (o sistema precisa aguentar o aumento de carga sem travar). |
  | "Somos um aplicativo de banco; se ficarmos fora do ar por 5 minutos, seremos multados pelo Banco Central." | **Disponibilidade e Tolerância a Falhas** (infraestrutura redundante para nunca cair). |
  | "O usuário desiste da compra se a página demorar mais de 2 segundos para carregar." | **Desempenho/Performance** (uso de cache, otimização de consultas). |

  ### Por que isso é desafiador?

  Porque os recursos são limitados (tempo e dinheiro). Se o arquiteto tenta criar um sistema que é perfeitamente escalável, ultra seguro, disponível 100% do tempo e extremamente rápido, o projeto se torna financeiramente inviável ou demora anos para ser entregue.

  Por isso, o arquiteto precisa colaborar de perto com os acionistas para entender quais motivações comerciais são as **reais prioridades** no momento, equilibrando os custos técnicos com o retorno financeiro que o sistema trará.
</details>




## Equilibrando arquitetura e codificação
- armadilha do gargalo: ocorre quando um arquiteto assume a codificação no caminho crítico de um projeto
- delegar o caminho crítico para a equipe de desenvolvimento e codificar funcionalidade de negócio que estão longe da parte crítica
- nos casos que o arquiteto não consiga escrever código fonte, é possível criar provas de conceito (POC). Neste caso é importante gerar código de produção com qualidade e não deixar que esse código seja utilizado como referência e ser levado para produção. Essa prática ajuda a manter a prática contínua e com boas práticas de programação.
- Outra oportunidade de códificação é resolver alguma história de deficits técnicos ou de arquitetura
- Automação de processos e ferramentas é outra forma de manter o contato com o desenvolvimentos de software. Desenvolvendo CLI para alguma validação ou tarefa repetitiva.
- Revisão é outra opção, além de não ser uma prática, ajuda a manter o contatos com as boas práticas e ajudar a identificar ponto de melhorias e indicar treinamentos para as equipes




## Resumo
- Arquitetura vs design: 
  a. Arquitetura: identificar as características, selecionar os padrões e criar componentes
  b. Design: criar diagrama de classes para cada componente, criar telas de interface, desenvolver e testar
- Amplitude técnica: para um arquiteto ter um conhecimento amplo é preferencial em relação a um conhecimento profundo (ser especialista numa tecnologia). Conhecer uma quantidade maior de tecnologias para resolver um mesmo problemas ajuda a tomar as melhores decisões ao se basear nas característica de arquitetura de acordo com as decisões de negócio.
- Analisando trade-offs:
  a. exemplo de solução para consumer de informação usando tópico ou fila
- Entendendo as motivações comerciais: Exemplo: uma empresa está perdendo vendas num marketplace porque o sistema está muito lento. Isso é uma necessidade de negócio que deve ser refletida a arquitetura para reduzir o tempo de resposta de reuiqsição da API
- Equilibrando arquitetura e codificação: estar próximo do código, mesmo não desenvolvendo com a equipe de desenvolvedores, ajuda a manter a qualidade técnica e apoiar/identificar gargalos técnicos nas equipes



# Capítulo 3: modularidade
> Noventa e cinco por cento das palavras [sobre arquitetura de software] são usadas enaltecendo os benefícios da “modularidade” e poucas, se algumas, tratam de como alcançá-la. — Glenford J. Myers (1978)
- modularidade é um princípio organizacional




## Definição
- No dicionário a definição é: "cada conjunto de partes padronizadas ou unidades independentes que podem ser usadas para construir uma estrutura mais complexa"
- Na linguagem de programação são usados:
  a. classes
  b. métodos/funções
  c. pacotes/namespace
  d. visibilidade e regras de escopos diferentes




## Medindo a modularidade
Pesquisadores criaram 3 conceitos principais:
- coesão
- acoplamento
- conascência


### Coesão
- se diz coeso quando as parte de um módulo devem estar contidas num mesmo módulo
> Tentar dividir um módulo coeso apenas resultaria em maior acoplamento e menor legibilidade. — Larry Constantine

Medidas de coesão:
- **coesão funcional**: uma parte está relacionada a outra parte, assim como o módulo tem tudo necessário para funcionar
- **coesão sequêncial**: quando temos dois módulos e a saída de um, é a entrada de outro
- **coesão comunicacional**: Exemplo prático: Um módulo que recebe os dados de uma compra, adiciona esse registro ao banco de dados e usa esses mesmos dados para gerar um e-mail de confirmação.
- **coesão procedural**: dois módulo devem executar o código numa determinada ordem
- **coesão temporal**: relacionado ao tempo, por exemplo, sistemas que precisam de algo na inicialização do sistema (configurar banco, carregar cache, carregar propriedades).
- ** coesão lógica**: uma agrupamento de métodos numa classes que realizam funcionalidades diferentes e que não tem relação. No java são conhecidas como módulo/pacote chamado utils. Lembre-se daquela frase: "não sei onde coloco isso" e resposta é "coloque no pacote utils".
- **coesão coincidental**: Os elementos estão no mesmo módulo por pura conveniência ou coincidência, sem qualquer relação lógica, temporal ou de dados. É o nível mais prejudicial para a manutenção do software.


<details>
    <summary>Sobre o trade-off sobre a separação de classes ou manter juntas</summary>

    ### O Conceito em Linhas Gerais

    Decidir o tamanho e a responsabilidade de um módulo não é uma ciência exata matemática. Na teoria, a alta coesão diz que devemos separar tudo o que faz coisas diferentes. Na prática, se separarmos *demais* (criando micromódulos para absolutamente tudo), corremos o risco de criar um problema oposto e igualmente grave: o **alto acoplamento**, onde os módulos ficam tão dependentes uns dos outros que não conseguem funcionar sozinhos.

    ---

    ### A Visão dos Autores (Richards & Ford)

    No livro, enfatizamos que a coesão é uma métrica subjetiva, "menos precisa do que o acoplamento", e que a estrutura correta **"sempre depende"** de trade-offs (compensações).

    Analisando o exemplo que você trouxe sobre a manutenção de clientes (`Customer Maintenance`) e pedidos (`Order Maintenance`), propomos três perguntas fundamentais que você, como arquiteto, deve se fazer para decidir se separa ou une esses comportamentos:

    * **1. O escopo do módulo de pedidos é muito pequeno?**
    Se as operações de obter e cancelar pedidos forem as únicas que existirão para sempre sobre "Pedidos", separá-las em um módulo `Order Maintenance` pode ser preciosismo. Talvez faça mais sentido mantê-las simplificadas dentro de `Customer Maintenance`.
    * **2. Há potencial de crescimento desordenado?**
    Se a tendência é que o módulo de clientes (`Customer Maintenance`) cresça muito no futuro com dezenas de novas funções, misturar regras de pedidos ali vai gerar uma bagunça difícil de manter. Nesse caso, a extração preventiva para um módulo próprio (`Order Maintenance`) é encorajada para preservar a coesão.
    * **3. Qual é o nível de dependência de dados (Acoplamento)?**
    Esta é a chave de ouro baseada na famosa citação de Larry Constantine (que diz que o acoplamento ideal é aquele que minimiza as conexões entre os módulos). Se para gerenciar pedidos o módulo `Order Maintenance` precisa consultar tantas regras internas e dados íntimos de `Customer` a ponto de os dois precisarem conversar freneticamente a cada segundo, separá-los criará um **acoplamento nocivo**. Se eles são altamente interdependentes, às vezes é melhor mantê-los juntos.
</details>


![](./assets/livro-fundamentos-arquitetura/cap-3-metrica-lcom-2026-07-14_19-13.png)

_A imagem acima ilustra a métrica LCOM onde os campos são octagonos e os métodos são quadrados._


A interpretação das classes da imagem é a seguinte:
- classe X: boa coesa
- classe Y: não tem coesão. Cada campo/método poderia ser uma classe separada porque não existe dependências entre um mesmo campo em diversas classes.
- classe Z: coesão mista

Classe utilitárias compartilhadas. 

A LCOM tem deficiências, assim como em muitas métricas. É possível encontrar uma falta de coesão estrutural, mas não tem como determinar quando certas partes se encaixam entre si logicamente.
Isso reflete:
> Segunda Lei da Arquitetura de Software: preferir por que acima de como.




### Acoplamento
- acoplamento **aferente**: mede o número de conexões de entrada para um artefato do código (componente, classe, função etc.).
- acoplamento **eferente**: mede as conexões de saída para outros artefatos do código.

<details>
  <summary>Gerado por IA</summary>

  É super normal achar esses termos confusos de início! Eles foram "emprestados" da biologia e da medicina (onde se fala de vasos sanguíneos e neurônios aferentes e eferentes) e aplicados à arquitetura de software por Robert C. Martin (o famoso "Uncle Bob").

  Para nunca mais esquecer, pense na direção do fluxo. Vamos traduzir isso de forma simples:

  ---

  ## 🧠 A Analogia Biológica (Para fixar na mente)

  * **Aferente (Entrada):** Os neurônios aferentes levam o estímulo sensorial da pele **para dentro** do cérebro.
  * **Eferente (Saída):** Os neurônios eferentes levam a resposta do cérebro **para fora**, em direção aos músculos.

  ---

  ## 💻 No Desenvolvimento de Software

  Quando falamos de acoplamento entre classes, pacotes ou componentes, a lógica é exatamente a mesma.

  ### 1. Acoplamento Aferente ($C_a$ - Afferent Coupling)

  Representa as dependências de **Entrada**. É a métrica que diz: **"Quantos componentes externos dependem de mim?"**

  * **O que significa:** Se o seu módulo `Autenticacao` é usado por outros 10 módulos do sistema, ele tem um acoplamento aferente alto ($C_a = 10$).
  * **Impacto:** Módulos com alto acoplamento aferente são **estáveis e responsáveis**. Como muita gente depende deles, você não pode alterá-los de qualquer jeito, ou vai quebrar o sistema inteiro. Eles devem ser muito bem testados e difíceis de mudar.

  ### 2. Acoplamento Eferente ($C_e$ - Efferent Coupling)

  Representa as dependências de **Saída**. É a métrica que diz: **"De quantos componentes externos eu dependo?"**

  * **O que significa:** Se o seu módulo `GeradorDeRelatorios` precisa importar 8 bibliotecas ou outras classes diferentes para funcionar, ele tem um acoplamento eferente alto ($C_e = 8$).
  * **Impacto:** Módulos com alto acoplamento eferente são **instáveis**. Se qualquer uma das 8 dependências mudar, o seu módulo corre um risco enorme de quebrar. Eles são altamente dependentes do mundo exterior.

  ---

  ## 📊 Tabela Comparativa

  | Característica | Acoplamento Aferente ($C_a$) | Acoplamento Eferente ($C_e$) |
  | --- | --- | --- |
  | **Direção das setas** | Setas apontando **para** o seu módulo ($\rightarrow$ Módulo) | Setas saindo **do** seu módulo (Módulo $\rightarrow$) |
  | **Pergunta-chave** | "Quem me usa?" | "Quem eu uso?" |
  | **Foco** | Responsabilidade | Dependência |
  | **Comportamento** | Tende a ser mais **estável** (difícil de mudar) | Tende a ser mais **instável** (sensível a mudanças externas) |

  ---

  ## 🛠️ Um Exemplo Prático em Código

  Imagine a classe `ProcessadorDePagamentos`:

  ```csharp
  // Exemplo de alto acoplamento EFERENTE (Ce)
  // Esta classe depende de TRÊS outras classes para funcionar.
  public class ProcessadorDePagamentos {
      private BancoDeDados _db;        // Dependência 1
      private GatewayDeCartao _cartao; // Dependência 2
      private ServicoDeEmail _email;   // Dependência 3

      public void Processar() {
          // ... usa as três dependências
      }
  }

  ```

  > O `ProcessadorDePagamentos` tem acoplamento eferente ($C_e$) igual a 3. Se o `ServicoDeEmail` mudar sua assinatura, o processador quebra.

  Agora, imagine a classe `Log`:

  ```csharp
  // Exemplo de alto acoplamento AFERENTE (Ca)
  // Esta classe não depende de ninguém, mas TODOS dependem dela.
  public class Log {
      public void Gravar(string mensagem) {
          Console.WriteLine(mensagem);
      }
  }

  ```

  > Se o `ProcessadorDePagamentos`, o `CarrinhoDeCompras` e o `CadastroUsuario` utilizam a classe `Log`, ela tem um acoplamento aferente ($C_a$) de 3. Ela é altamente responsável; se você alterar o método `Gravar`, precisará ajustar esses três outros lugares.
</details>




### Abstração, Instabilidade e distância da sequência principal
- acomplamento: uma parte do sistema depende de outra
- abstração
- instabilidade 

<details>
  <summary>Gerado por IA</summary>

  Entender as métricas de arquitetura de software pode parecer desafiador no início, mas elas se tornam simples quando usamos analogias do nosso dia a dia. Vamos desmistificar esses três conceitos fundamentais.

  ---

  ## O Conceito em Linhas Gerais

  Imagine que estamos construindo uma cozinha de restaurante. Vamos entender os termos por meio dessa analogia:

  * **Acoplamento (Dependência):** É o quanto uma parte do sistema precisa de outra para funcionar.
  * *Analogia:* Se o cozinheiro só consegue preparar o prato usando exatamente a faca da marca *X*, o trabalho dele está fortemente **acoplado** a essa faca específica. Se a faca sumir, o trabalho para.


  * **Instabilidade (Facilidade de Mudar):** É a probabilidade de um componente sofrer impacto ou precisar ser alterado.
  * *Analogia:* Um garçom é **instável** (no bom sentido arquitetural) porque ele se adapta rapidamente: se o cardápio muda, ele apenas decora os novos pratos. Já a tubulação de gás da cozinha é extremamente **estável** (rígida): se você quiser mudar o fogão de lugar, terá um trabalho enorme para alterar os canos.


  * **Abstração (Ideia vs. Prática):** É a separação entre *o que* deve ser feito e *como* isso é feito detalhadamente.
  * *Analogia:* O cardápio é uma **abstração**. Ele diz "Filé com fritas". Você não precisa saber a marca do óleo ou a temperatura exata da fritadeira (isso é a **implementação concreta**). Você só precisa saber o conceito do prato.



  ---

  ## A Visão dos Autores (Richards & Ford)

  No livro, nós abordamos essas métricas de forma matemática e matemática-visual para ajudar o arquiteto a avaliar a saúde e a flexibilidade do sistema.

  ### 1. Acoplamento: Entradas e Saídas

  Dividimos o acoplamento em duas direções para entender o fluxo de dependência de um componente (ou classe):

  * **Acoplamento Aferente ($C^a$):** São as conexões que **chegam** ao componente. Ou seja, quantos outros componentes dependem dele.
  * **Acoplamento Eferente ($C^e$):** São as conexões que **saem** do componente. Ou seja, de quantos outros componentes ele depende para funcionar.

  ### 2. Instabilidade ($I$)

  A instabilidade mede o quão fácil é alterar um componente sem causar um efeito dominó de erros. Ela é calculada pela fórmula:

  $$I = \frac{C^e}{C^e + C^a}$$

  * **Instabilidade Próxima de 1 (Máxima):** O componente depende de muitos outros ($C^e$ alto), mas ninguém depende dele ($C^a$ zero). Ele é muito fácil de mudar, pois qualquer alteração nele não quebra o restante do sistema.
  * **Instabilidade Próxima de 0 (Mínima / Estável):** Muitos dependem dele, mas ele não depende de ninguém. Ele é difícil de mudar, pois qualquer alteração nele pode quebrar vários outros pontos do sistema.

  ### 3. Abstração ($A$)

  Mede a proporção de elementos abstratos (como interfaces e contratos que definem *o que* fazer) em relação aos elementos concretos (código real que executa a tarefa).

  $$A = \frac{\sum m^a}{\sum m^c}$$

  * **Se a abstração é 1:** O componente é puramente abstrato (só contém definições, nenhuma implementação prática).
  * **Se a abstração é 0:** O componente é puramente concreto (código direto, sem interfaces).

  > **A Regra de Ouro dos Autores:** > Componentes que são muito **estáveis** (difíceis de mudar) devem ser altamente **abstratos** (fáceis de estender por meio de contratos). Componentes que são muito **instáveis** (fáceis de mudar) podem ser totalmente **concretos**. O equilíbrio perfeito entre essas forças é o que chamamos de **Sequência Principal** da arquitetura.
</details>




### Distância da sequência principal
- uma métrica derivada com base na instabilidade e na abstração
- instabilidade: mede quando um componente não depende de ninguém para mudar. Mudança no componente não afeta outros componentes do sistema
- abastração: mede a proporção de regras teóricas em relação ao código. Na programação seria a relação de uma classe abstrata e um classe concreta

<details>
  <summary>Gerado por IA</summary>

  ## O Conceito em Linhas Gerais

  * **Instabilidade ($I$):** Mede a facilidade ou a probabilidade de um componente mudar. Se um componente depende de muitas coisas e ninguém depende dele, ele é considerado **instável** (fácil de alterar, pois sua mudança não quebra o resto do sistema). Se todo mundo depende dele, ele é **estável** (difícil de alterar, pois qualquer modificação gera um efeito dominó).
  * **Abstração ($A$):** Mede a proporção de regras teóricas (contratos e interfaces) em relação ao código prático (implementação detalhada). Um componente altamente **abstrato** apenas dita as regras do que deve ser feito, enquanto um componente **concreto** executa o trabalho bruto.

  ---

  ## A Visão dos Autores (Richards & Ford)

  Nesta obra, avaliamos a saúde da arquitetura combinando essas duas métricas, que sempre resultam em valores entre $0$ e $1$:

  * **O Equilíbrio Necessário:** Nós defendemos que a estabilidade e a abstração devem andar de forma inversamente proporcional. Isso é calculado pela fórmula da Distância da Sequência Principal:

  $$D = \vert{}A + I - 1\vert{}$$


  * **Componentes Estáveis devem ser Abstratos ($I = 0$ e $A = 1$):** Se um componente é muito difícil de ser alterado porque todo o sistema depende dele, ele precisa ser composto por interfaces abstratas. Assim, novas funcionalidades podem ser adicionadas estendendo essas interfaces, sem a necessidade de modificar o código original que já está consolidado.
  * **Componentes Instáveis podem ser Concretos ($I = 1$ e $A = 0$):** Se ninguém depende daquele componente, ele é flexível e livre para sofrer modificações diretas na implementação prática a qualquer momento, sem risco de quebrar outras partes do software.
</details>

![](./assets/livro-fundamentos-arquitetura/cap-3-abstracao-instabilidade-2026-07-17_21-51.png)

![](./assets/livro-fundamentos-arquitetura/cap-3-distancia-sequencia-principal-2026-07-17_22-14.png)

![](./assets/livro-fundamentos-arquitetura/cap-3-zona-inutilidade-2026-07-17_22-15.png)




### Conascência
> Dois componentes são conascentes se uma mudança em um requer que o outro seja modificado para manter a correção geral do sistema. — Meilir Page-Jones

Dois tipos de conascência: 
- estática
- dinâmica

#### Conascência estática
- é o acoplamento no nível de código-fonte
  - Conascência de nome
  - Conascência de tipo
  - Conascência de significado ou Conascência de convenção
  - Conascência de posição
  - Conascência de algoritmo


#### Conascência dinâmica
- analisa a chamada durante a execução
  - Conascência de execução
  - Conascência de tempo
  - Conascência de valores
  - Conascência de identidade


#### Propriedades da Conascência
- a Conascência é uma ferramenta para arquitetos e desenvolvedores
- algumas propriedades ajudam os desenvolvedores a usar com sabedoria

**Força**  
![](./assets/livro-fundamentos-arquitetura/cap-3-guia-refatoracao-2026-07-18_21-20.png)

**Localização**  

**Grau**  



### Unificando as métricas de acoplamento e conascência

![](./assets/livro-fundamentos-arquitetura/cap-3-unificando-acoplamento-conascencia-2026-07-19_10-36.png)


#### Problemas com a conascência dos anos 1990
<details>
  <summary>Gerado por IA</summary>

  ## O Conceito em Linhas Gerais
  A **conascência** é um conceito que serve para medir o grau de dependência entre diferentes partes de um sistema. Se a alteração em um componente exigir que outro componente também seja modificado para manter a integridade do software, dizemos que eles estão em conascência.

  No entanto, as definições tradicionais desse termo criadas na década de 1990 possuem limitações quando aplicadas ao cenário moderno de desenvolvimento. Elas costumam focar demais em detalhes minuciosos e de baixo nível do código (como a qualidade e a limpeza das linhas de programação), deixando de lado as grandes decisões estruturais que definem a arquitetura do sistema.

  ---

  ## A Visão dos Autores (Richards & Ford)

  Em nossa obra, apontamos que as métricas tradicionais dos anos 1990 falham em dois pontos centrais para o arquiteto moderno:

  * **Foco no Grau vs. Modo de Acoplamento:** As métricas antigas olham muito para o *grau* do acoplamento em nível de código. Nós, como arquitetutos, nos importamos mais com o **como** os módulos estão acoplados (a natureza dessa ligação), focando em decisões mais amplas do que na implementação detalhada.
  * **Decisões de Arquitetura Distribuída:** A conascência tradicional não ajuda a resolver dilemas arquiteturais complexos e modernos, como escolher entre **comunicação síncrona ou assíncrona** em um ambiente de microsserviços.
  * **A Regra dos Trade-offs:** Reafirmamos a Primeira Lei da Arquitetura de Software: *tudo é um trade-off* (uma escolha onde há perdas e ganhos). Avaliar o acoplamento hoje exige ponderar essas escolhas estruturais, e não apenas analisar linhas de código isoladas.
</details>






### De módulos a componentes
- módulo: nome genérico para grupo de código
- componente: é a materialização do módulo que você pode instalar, executrar ou conectar no seu sistema.

<details>
  <summary>Gerado por IA</summary>

  ## O Conceito em Linhas Gerais

  * **Módulo:** É uma forma genérica de organizar e agrupar códigos que possuem propósitos parecidos ou que trabalham juntos. Pense nele como as pastas do seu computador onde você guarda arquivos do mesmo assunto para não deixar tudo bagunçado.
  * **Componente:** É a materialização física ou lógica desse grupo de códigos dentro de uma plataforma. Se o módulo é a ideia de organizar as coisas juntas, o componente é o bloco real de construção que você consegue instalar, executar ou conectar no seu sistema.

  ---

  ## A Visão dos Autores (Richards & Ford)

  * **Terminologia Abrangente:** Em nossa obra, usamos o termo "módulo" como um conceito lógico para nos referirmos a um agrupamento de código afim.
  * **Blocos de Construção Práticos:** Já os "componentes" são tratados por nós como os blocos reais e fundamentais que os arquitetos utilizam para desenhar a estrutura do software. A maioria das linguagens e ferramentas modernas oferece suporte para empacotar esses módulos na forma de componentes físicos.
  * **O Desafio da Separação:** Embora o conceito de separar o código em partes menores exista desde o início da computação, nós destacamos que desenvolvedores e arquitetos ainda enfrentam muitas dificuldades práticas para definir bem os limites de cada componente e obter bons resultados de design.
</details>




## Resumo
- Modularidade é como organizamos o nosso código. Na orientação é objetos é representada a partir de classes, métodos e propriedades.
- Na nodularidade temos 3 conceitos:
  - coesão
  - acoplamento
  - conascência
- Coesão: se diz que um código é coeso quando as propriedades de uma classe na orientação a objetos utiliza todos os seus atributos na maioria dos métodos.
- Acoplamento: se diz que um código é acoplado quando ele depende fortemente de outros componentes do sistema
  - acomplamento eferente: o seu sistema não dependende de outros sistema. Os outros sistemas dependem do seu sistema.
  - acomplamento aferente: o seu sistema depende de um ou mais sistemas externos. Qualquer alteração no sistema externo pode quebrar o seu sistema
- Conascência: se diz que existe um componete conascente quando uma alteração em um componete afete um segundo componente. TEmos dois tipos:
  - estática: código fonte
  - dinâmica: o componente em execução. Código-fonte é execução
- Módulo é o agrupamento de código
- Componente é materialização de um módulo






