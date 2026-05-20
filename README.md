# aws-foundations-dio-gft-project-1
Repositório criado como entregável do desafio da DIO, documentando os principais conceitos aprendidos sobre computação em nuvem na AWS, com foco em EC2, EBS e serviços relacionados.

Aqui vão alguns conceitos que aprendi durante as aulas do curso (fiz um mapa mental no arquivo 'AWS Foundations_light.png' que está no repositório)
---

## Modelo de Responsabilidade Compartilhada
Na AWS, as responsabilidades são divididas entre a AWS e o usuário:

- **On-premise**: você é responsável por tudo
- **IaaS (Infraestrutura)**: a AWS cuida do hardware; você gerencia o SO, rede e aplicações
- **PaaS (Plataforma)**: a AWS cuida da infraestrutura e plataforma; você foca na aplicação
- **SaaS (Software)**: a AWS entrega tudo pronto; você apenas usa

> **Analogia do churrasco**: em casa você faz tudo (on-premise); no clube você leva carne e bebida (IaaS); na casa do amigo só leva bebida (PaaS); no buffet você não leva nada (SaaS).

---

## Regiões e Zonas de Disponibilidade (AZs)

- **Regiões**: localizações geográficas ao redor do mundo onde a AWS opera
- **Availability Zones (AZs)**: data centers físicos dentro de cada região
- Algumas regiões são mais caras que outras dependendo da localização

---

## AWS IAM - Identity and Access Management

O IAM é responsável pelo gerenciamento de acessos na AWS.

**Principais conceitos:**
- Usar a conta **root** apenas para o primeiro login; após isso, criar um usuário com permissões de administrador
- Ativar o **MFA** (autenticação multifator) para maior segurança
- Criar **grupos** com permissões específicas e atribuir usuários a esses grupos — isso facilita o gerenciamento em escala
- É uma das etapas mais importantes pois se relaciona diretamente com **governança e segurança**
- OBS.: como os vídeos do curso foram feitos em 2024, algumas coisas estavam diferentes, hoje o fluxo de cadastro de usuários está bem mais fácil, é possível atribuir/criar um grupo e tambéma dar permissões no mesmo fluxo de criação do usuário. 

---

##  AWS Budgets

Serviço para controle financeiro da conta AWS:

- Permite definir **metas e limites de gastos**
- Possibilita configurar **alertas personalizados** quando os gastos se aproximam do limite definido
- OBS.: para um user ter acesso aos dados de billing é preciso adicionar a permissão ao criar o usuário, diferente do que foi mostrado na aulas provavelmente devido as atualizações da AWS

---

## AWS EC2 - Elastic Compute Cloud

O EC2 é basicamente o **servidor virtual** da AWS (VM - Virtual Machine).

**Características principais:**
- Ao criar uma instância EC2, é possível escolher: sistema operacional, CPU, memória RAM e tipo de instância
- Os **tipos de instância** possuem categorias diferentes, com custos variados — vale estudar e identificar a melhor opção para cada caso.
- É possível **mudar o tipo de instância** enquanto o EC2 está rodando (ex: T2 General Purpose é uma das mais baratas)

**Modelos de pagamento:**
- **Instância Spot**: capacidade ociosa da AWS com desconto; pode ser interrompida
- **On Demand**: pague pelo que usar, sem compromisso
- **Compute Saving Plans**: compromisso de uso por 1 ou 3 anos com desconto
- **EC2 Instance Savings Plans**: similar ao anterior, mas vinculado a uma família de instância e região

---

## AWS EBS - Elastic Block Store

O EBS funciona como um **HD externo** anexado a uma instância EC2.

**Características:**
- Permite escolher e alterar o tamanho do disco
- **Baixa latência**
- Suporta **snapshots** (backups pontuais do volume)
- Suporta **volumes e partições**
- É atrelado especificamente a instâncias EC2
- Para utilizar o EBS em outra AZ, é necessário tirar um snapshot e restaurá-lo na AZ de destino

> **Ponto importante**: o EBS persiste de forma independente do EC2. Se uma instância for encerrada ou destruída, os dados no EBS continuam disponíveis.

---

## AWS AMI - Amazon Machine Image

A AMI é um **template de servidor** que contém tudo necessário para lançar uma instância EC2:

- Sistema operacional
- Softwares pré-instalados
- Configurações e aplicativos necessários para iniciar a máquina virtual

> **Analogia**: assim como uma imagem Docker contém tudo para subir um container, a AMI contém tudo para lançar um EC2.

A AMI é o **ponto de partida** - ela origina o EC2. Em diagramas de arquitetura, ela pode ser representada como um elemento externo apontando para a instância EC2.
- Tal como fiz no diagrama presente no repositório 'AWS - EC2.drawio.pdf'
---

## AWS S3 - Simple Storage Service

O S3 é um serviço de **armazenamento de objetos**.

- Os containers onde os objetos são armazenados se chamam **Buckets**
- Tipos de armazenamento S3:
  - **S3 Standard**: acesso frequente
  - **S3 Intelligent-Tiering**: move objetos automaticamente entre camadas conforme o acesso
  - **S3 Express One Zone**: altíssima performance em uma única AZ
  - **S3 Standard-Infrequent Access**: acesso infrequente, mas recuperação rápida
  - **S3 One Zone-Infrequent Access**: igual ao anterior, mas em uma única AZ
  - **S3 Glacier Instant Retrieval**: arquivamento com recuperação em milissegundos
  - **S3 Glacier Deep Archive**: arquivamento de longo prazo, menor custo
- no diagrama que anexei faço o uso do S3 com WhatsApp e Lambda 'AWS - S3.drawio.pdf'.

---

## AWS Lambda

- Serviço de computação **serverless** (sem servidor)
- Executa código em resposta a **eventos**
- Suporta linguagens: Python, Node.js, Java, Go, Ruby, C#

---

Até agora o aprendizado tem sido incrível! Seguimos em frente!🚀
