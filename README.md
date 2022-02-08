# AWS Resumes

In this repository i'll resume in PT-BR what i've learned from AWS skillbuilder courses.

## Authors

- [@algteixeira](https://www.github.com/algteixeira)

# Sumário

* [Módulo 1](#módulo-1)

* [Módulo 2](#módulo-2)

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