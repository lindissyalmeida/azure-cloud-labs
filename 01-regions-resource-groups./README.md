Lab 01 — Azure Regions & Resource Groups
Objetivo

Compreender os conceitos fundamentais de organização e localização de recursos no Microsoft Azure, realizando uma implementação prática utilizando Azure Region, Resource Group e Storage Account.

Conceitos estudados
Azure Region

Uma Azure Region representa uma localização geográfica onde a Microsoft disponibiliza sua infraestrutura de Azure.

No laboratório foi utilizada a região:

Brazil South

A escolha da região pode considerar fatores como localização dos usuários, latência, disponibilidade dos serviços, requisitos de negócio e custos.

Resource Group

Um Resource Group é um contêiner lógico utilizado para organizar e gerenciar recursos relacionados dentro do Azure.

No laboratório foi criado:

RG-LAB-DIA01

O Resource Group não representa fisicamente um datacenter. Ele é utilizado para organização e gerenciamento lógico dos recursos.

Entre os benefícios estão:

Organização dos recursos;
Gerenciamento do ciclo de vida;
Controle de acesso;
Governança;
Acompanhamento e gerenciamento de custos.
Storage Account

O Storage Account é um recurso do Azure que fornece serviços de armazenamento.

Neste laboratório, um Storage Account foi criado e associado ao Resource Group RG-LAB-DIA01.

O objetivo principal nesta etapa foi compreender o Storage Account como um recurso pertencente ao ambiente Azure, sem aprofundar ainda suas diferentes funcionalidades de armazenamento.

Arquitetura do laboratório

A estrutura implementada foi:

Azure
│
└── Region: Brazil South
      │
      └── Resource Group: RG-LAB-DIA01
            │
            └── Storage Account
Implementação
1. Resource Group

Foi criado o Resource Group:

RG-LAB-DIA01

Região selecionada:

Brazil South
2. Storage Account

Foi criado um Storage Account dentro do Resource Group.

Após a criação, o recurso foi acessado pelo Azure Portal para validar sua associação ao Resource Group.

Relação entre os conceitos

A prática permitiu visualizar a diferença entre localização geográfica, agrupamento lógico e recurso:

REGION
Brazil South
    │
    ▼
RESOURCE GROUP
RG-LAB-DIA01
    │
    ▼
RESOURCE
Storage Account
Resumo
Conceito	Função
Region	Localização geográfica da infraestrutura utilizada pelo recurso
Resource Group	Agrupamento lógico para organização e gerenciamento
Storage Account	Recurso que fornece serviços de armazenamento
Aprendizados

Durante o laboratório, foram consolidados os seguintes conceitos:

Uma Region representa uma localização geográfica da infraestrutura Azure.
Um Resource Group é um agrupamento lógico de recursos.
Um Storage Account é um recurso do Azure.
Region e Resource Group possuem funções diferentes.
Recursos podem ser organizados dentro de Resource Groups.
A organização dos recursos pode contribuir para administração, governança e gerenciamento de custos.

Um ponto importante compreendido durante a prática foi que o Resource Group não determina a localização física dos recursos. Ele é utilizado para organização lógica e gerenciamento.

Ambiente utilizado

Cloud Provider: Microsoft Azure
Interface: Azure Portal
Region: Brazil South
Resource Group: RG-LAB-DIA01
Resource: Storage Account

Status

Concluído ✅
