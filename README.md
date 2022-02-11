# AWS Resumes

In this repository i'll resume in PT-BR what i've learned from AWS skillbuilder courses.

## Authors

- [@algteixeira](https://www.github.com/algteixeira)

# Sumário

* [AWS CPE](#aws-cloud-practitioner-essentials)

* [Módulo 1](#módulo-1)

* [Módulo 2](#módulo-2)

* [Módulo 3](#módulo-3)

* [Módulo 4](#módulo-4)

* [Módulo 5](#módulo-5)

* [Módulo 6](#módulo-6)

* [Módulo 7](#módulo-7)

* [Módulo 8](#módulo-8)

* [Módulo 9](#módulo-9)

* [Módulo 10](#módulo-10)

# AWS Cloud Practitioner Essentials

## Módulos

### Módulo 1
Sobre AWS cloud services:
Principal vantagem que pode ser observada de início é que você possui elasticidade na capacidade de uso (EC2), assim, se a demanda for por mais ou menos processamento/capacidade de servidor isso será reajustado de acordo com a sua necessidade e você paga apenas por aquilo que consumir, não sendo necessário fazer uso de um servidor super potente, do qual você extrai o desempenho dele em apenas 10% do tempo e nos 90% restante paga de forma desnecessária.

Existe basicamente 3 modelos de implantação: Baseada em nuvem, local e híbrida. A baseada em nuvem possui todos os componentes do sistemas hospedados na AWS, GCloud ou serviços semelhantes. A implantação no local é muito parecida com a implantação que ocorria há 15-20 anos atrás, a diferença reside no fato de que hoje em dia faz-se uma espécie de "nuvem privada" utilizando tecnologias de virtualização e gerenciamento das aplicações. Já o modelo híbrido seria uma união dos anteriores.

### Módulo 2
#### Sobre EC2:
Existem diferentes tipos de instâncias EC2 para atender diferentes necessidades. Tais instâncias acabam sendo agrupadas por família, existindo assim as não-especializadas (de uso geral) e as otimizadas para diferentes funções, como computação, memória, armazenamento.
**Instâncias de uso geral:** Possuem recursos balanceados e são "pau pra toda obra". Geralmente são essas as utilizadas para serviços web comuns.
**Otimizadas para computação:** São as utilizadas para serviços de jogos, modelagem científica, etc.
**Otimizadas para memória:** São boas para tarefas que demandam muita memória.
**Otimizadas para computação acelerada:** São boas para tarefas como visão computacional e outras subvertentes do Machine Learning que utilizam muito cálculo de ponto flutuante baseado em GPU.
**Otimizadas para armazenamento:** Utilizadas para aplicações que necessitam alta performance na busca e armazenamento de dados locais.

Existem diferentes formas de pagamento em relação ao EC2, cada uma possuindo diferentes vantagens. Tais formas seriam:
**sob demanda:** Geralmente é por aqui que se inicia a jornada de pessoas e empresas no AWS cloud. Aqui você paga apenas pelo que usar, podendo pausar o uso à qualquer momento.
**saving plans:** Aqui você consegue descontos nos valores de uso ao se comprometer em manter um uso mínimo X de computação por uma quantidade Y de tempo.
**instâncias reservadas:** Você economiza por ignorar o fator "imprevisibilidade de uso". Já que nesse modelo você utiliza aplicações estacionárias, cuja necessidade de computação não varia ou varia muito pouco.
**instâncias spot:** Você economiza devido à possibilidade de interrupção na sua instância para transferir mais poder de computação para outras pessoas. É uma boa opção para servidores que realizam tarefas em lotes.
**Host dedicado:** É o modelo mais caro, já que aqui você possui um servidor físico e não compartilha a máquina do servidor com ninguém.

#### EC2 Auto Scaling
O EC2 auto scaling é um mecanismo que permite que você não se preocupe em alocar/reduzir recursos manualmente, podendo assim, segundo regras pré-estabelecidas, deixar isso por conta da AWS.
Existem dois tipos de scaling: dinâmico e preditivo.
**Dinâmico:** Aqui o scaling responde de acordo com as requisições.
**Preditivo:** Aqui o número de instâncias à serem utilizadas é pré-programado e segue como base a demanda.

#### Elastic Load Balancing
O ELB basicamente é um sistema de distribuição de recursos entre instâncias, é ele quem avisa que instância X está sobrecarregada e portanto as requisições seguintes devem ser distribuidas pra instância Y.

#### SNS
Serviço de assinatura e envio de mensagens. Você pode utilizá-lo para enviar as novidades da sua loja para todos clientes que assinam sua newsletter, por exemplo.

#### SQS
Sistema de fila da AWS, onde se uma parte do sistema travar, não danifica a aplicação, já que as requisições ficam em fila até que a parte que estava inoperante voltar a funcionar.

#### LAMBDAS
Os lambdas são basicamente uma função que obedece ao código designado à ela e que será executada de acordo com um trigger pré-definido. Os lambdas são utilizados para computação serverless, que é quando diferente do EC2, você não precisa se preocupar em setar o servidor. Ex: Quando existirem menos de 50 pessoas acessando o site simultâneamente, manda um e-mail com essa informação para o responsável.

### Módulo 3

Deve-se sempre levar algumas coisas em conta na hora de escolher a região na qual estará hospedado o seu servidor.
**Requisitos legais:** Se sua empresa precisa manter os dados dentro de um país X, então escolha a hospedagem nessa região.
**Proximidade com clientes:** Se quem usa seu serviço mora nos EUA, escolha a hospedagem lá, para reduzir o tempo da requisição.
**Disponibilidade de serviços:** Nem todos serviços AWS estão disponíveis em todas regiões já, então leve isso sempre em consideração.
**Custos:** Algumas regiões pagam mais impostos e tem custo de operação maior, logo, isso é refletido no valor que você paga.

#### Zonas de disponibilidade
São zonas que possuem um ou vários datacenters distribuidos. Elas são uma forma de divisão de datacenters importante pois se, por exemplo, um desastre natural afetar uma zona, ainda assim existem outras nas redondezas para efetuar seu serviço.

#### Amazon Cloudfront
É a CDN da AWS, que faz com que um cliente não tenha que fazer uma requisição no outro lado do mundo para solicitar um dado, assim, ele consegue buscar o dado na região mais próxima possível onde ele está disponível. Isso acontece por meio de um site que funcionará como cache, mantendo cópias dos dados do conteúdo.

### Módulo 4

#### VPC
É uma funcionalidade onde você consegue dividir sua rede em sub-redes, das quais algumas podem ser públicas e outras privadas. As públicas podem se comunicar com o cliente que faz requests. Já as privadas são onde você irá manter funcionalidades que você não gostaria que o cliente tentasse se comunicar com. Exemplo de rede privada: A aplicação do RH da sua empresa ou o seu BD.

O que torna tais conexões possíveis é o gateway, que no caso de gateways privados funciona como uma porta com identificação biométrica, onde só aqueles que tem a devida permissão podem abri-la.

A ACL seria o firewall que controle entrada e saída de uma sub-rede e é stateless.
Já o grupo de segurança é um firewall interno que é stateful, ou seja, se lembra de decisões anteriormente tomadas

### Módulo 5

Armazenamento na AWS é eficiente pois na hora de salvar, salva apenas os dados que foram atualizados, o que não foi modificado é mantido como está. Segue algumas tecnologias da AWS citadas no módulo:

**Armazenamento de instâncias:** É um tipo de armazenamento que serve para aplicações cujos dados não acarretarão em problemas se perdidos, já que ao dar stop na estância, quando iniciá-la novamente provavelmente ela estará em outro host e portanto, não terá mais os dados anteriores disponíveis.
**EBS:** Sistema que possui volumes de dados que podem ser anexados às instâncias, assim, quando pausar e voltar uma instância, ela utilizará o volume sem problemas. Esse sistema se baseia em snapshots, que seriam backups que tem seu refresh de x em x tempos (dias, horas, etc...), afim de manter o dado sempre atualizado.
**EFS:** Permite que várias instâncias acessem o mesmo dado ao mesmo tempo de forma segura, redimensionando automaticamente, que permite que qualquer instancia da região acesse-o.
**RDS:** Serviço perfeito para armazenas bancos de dados relacionados, já que aplica patches automaticamente, tem sistema de recuperação de desastres, faz backups e muito mais.
**Redshift:** Solução perfeita para trabalhar com big data, com uma única query consegue buscar em petabytes de dados simultaneamente.
**AWS Database Migration Service:** Serve para você migrar seus DB's para uma estrutura cloud com a vantagem de manter ele operante antes de finalizar a migração. Também consegue migrar realizando uma união de diversos databases, além de replicar os dados de forma contínua.

### Módulo 6

A responsabilidade quanto à segurança é compartilhadada na AWS. Ou seja, você é responsável pela segurança que dos seus serviços na nuvem enquanto à AWS é responsável por lhe fornecer uma nuvem segura.
Na AWS, ao criar a conta vem o usuário root, com permissões totais na conta, porém, ao criar outros usuários, pode-se, por meio de um arquivo JSON administrar permissões em diferentes recursos para eles. Cada usuário pode possuir uma ou mais roles também, que possuem diferentes níveis de acesso à diferentes serviços. Você pode organizar os diferentes tipos de acessos para diferentes personagens utilizando o serviço chamado de **AWS Organizations**, centralizando o gerenciamento em apenas um lugar. Assim, contas com permissões semelhantes podem ser colocadas na mesma unidade organizacional, lhes concedendo os mesmos acessos. 
A AWS é naturalmente um pouco resistente à ataques DDOS devido às partes elastic de sua arquitetura, já que, por exemplo, o load balancer é algo muito dificil de ser sobrecarregado (porém não impossivel). Além disso, ainda é possivel contratar serviços adicionais de segurança fornecidos pela empresa.

### Módulo 7

**CloudWatch:** Sistema de monitoramento próprio da AWS que faz o constante monitoramento do seu sistema onde você pode implementar triggers para ser notificado ou executar algo no seu sistema caso o trigger X seja acionado. Por ter acesso a todas as métricas do seu sistema, você pode gerar insights das suas aplicações por meio dele.
**Cloudtrail:** Serviço de auditoria da AWS, onde cada solicitação é registrada nele, registrando também quem fez a chamada, onde o IP estava, se houve alteração em algo, etc. Os logs são salvos por longos tempos e de forma segura, mantendo a auditoria do seu sistema sempre em dia.
**Trusted Advisor:** Serviço que checa possíveis melhorias no seu sistema de forma automática, ajudando a melhorá-lo conforme o uso. Ele faz avaliações com base em: otimização de custo, performance, segurança, tolerância a falhas e limites de serviço. Sua execução é real time.

### Módulo 8

**Quanto ao nível gratuito da AWS:** Nem todos serviços "gratuitos" da AWS são gratuitos para sempre. Alguns tem duração x de gratuidade (ex: 12 meses) enquanto outros lhe permitem testes gratuitos, com número X de usos. Ex: Lambdas, permite 1 milhão de invocações por mês. ES3: gratuito por 12 meses para até 5gb de armazenamento.
Os custos que estão sendo gastos com serviços podem ser acessados facilmente por meio do painel de cobrança.
Você pode pagar seus custos de contas AWS da empresa em apenas uma conta se quiser, assim sendo, não é necessário pagar conta por conta seus gastos gerais de operações cloud.

#### AWS Budgets

Permite que a empresa possa realizar orçamentos para se guiar melhor no seu consumo de serviços e assim não venha a pagar mais do que gostaria. Quando houver previsão de ultrapassar o orçamento ou até mesmo caso você o exceda, o budgets pode lhe notificar quanto à isso.

#### Cost Explorer

Serve para você acompanhar os dados que compõe os valores de suas faturas, assim você pode ver qual serviço custou mais caro ou mais barato para que, então, você possa lidar melhor com seus gastos.

Existem diferentes níveis de suporte na AWS, todas contas iniciam com o básico, porém existe o suporte ao desenvolvedor, suporte business e suporte enterprise. Todos vão incrementalmente herdando as qualidades do anterior. O plano enterprise possui um TAM, que é um funcionário AWS que te ajuda a melhorar a arquitetura dos seus serviços cloud, se identificar pontos de melhora.


A AWS também possui um marketplace, onde você pode comprar softwares de terceiros que funcionem na AWS. Assim, você não necessariamente precisa construir softwares para realizar certas funções na AWS, já que, se quiser (e existir), você pode comprar tal funcionalidade no marketplace.

### Módulo 9

#### AWS CAF

É um framework que auxilia na migração de sistemas locais para a nuvem com base em diferentes perspectivas, tais como: negócios, pessoas, governança, plataforma, segurança e operações.

#### Sobre as 6 estratégias de migração

**Lift-and-shift:** Redefine a hospedagem do aplicativo para facilitar a migração cloud.

**Replatform:** Realiza otimizações na nuvem de forma à obter reais benefícios na migração sem mudar a arquitetura central do app.

**Refatoração:** Refatora o app utilizando os recursos que já são nativos da nuvem, diminuindo a preocupação com manter diferentes padrões de serviço.

**Recompra:** Envolve a troca de softwares que a empresa utilizava no sistema local para outros que se adaptem melhor ao sistema de nuvem.

**Retenção:** Trata-se de manter fora da nuvem tudo aquilo cujo funcionamento ideal ocorra fora dela ou que ainda não estejam prontos para ir pra nuvem.

**Inativação:** Envolve remover tudo aquilo que já não é mais necessário ou que os serviços de nuvem tornarão obsoletos.

#### AWS Snow Family

É um conjunto de dispositivos que realizam o transporte físico de dados para dentro e pra fora da AWS, eles tem diferentes tamanhos e capacidades, sendo que alguns possuem recursos de computação já neles integrados. A responsabilidade pela gestão e segurança deles fica por conta da AWS, que mantém criptografia SHA-256 (de ponta) para garantir que o transito de dados acontece de forma segura. O Snowball é o menorzinho deles, possuindo menor capacidade. Depois tem o snowcone, que é um pouco maior e pode ser voltado para computação ou armazenamento. Já o último é o snowmobile, que é um container que realiza alto processamento de dados e é conduzido por um caminhão que o reboca.

### Módulo 10

#### WELL-ARCHITECTED FRAMEWORK

Um framework da AWS que auxilia a construir boas arquiteturas cloud, assegurando a qualidade do seu serviço. Ele possui 5 pilares, e eles são:

**Excelência Operacional:** Consiste em monitorar os sistemas afim de garantir que as operações seguem os devidos padrões a elas designadas.

**Segurança:** Verifica a integridade dos dados e protege o sistema, por exemplo, usando criptografia.

**Confiabilidade:** Confirma a integridade dos dados do DB, por exemplo, além de garantir a qualidade da operação como um todo.

**Performance:** Confirma o uso eficiente de processamento/armazenamento, por exemplo, usando o tipo correto de AWS EC2 baseado em carga de trabalho, etc.

**Otimização de custos:** Verifica se o gasto total planejado é desnecessário ou se os custos deveriam ser realocados em outras partes do sistema.

Para auxiliar no uso do framework, a AWS possui o **Well-Architected Tools**, uma subplataforma onde você pode conferir as informações à respeito dos 5 pilares acima.

#### Principais benefícios de utilizar a AWS

**Troca de despesas fixas por variáveis**

**Economia em escalas massivas**

**Não precisar se preocupar com a capacidade**

**Aumento de velocidade e agilidade**

**Ausência de gastos com construção e manutenção de datacenters**a

**Ter alcance global rapidamente**


