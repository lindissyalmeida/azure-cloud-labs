# Azure Cloud Labs

Repositório dedicado à implementação e documentação de laboratórios práticos em **Microsoft Azure**, com foco no desenvolvimento de conhecimentos em **Cloud Infrastructure**.

O projeto reúne exercícios práticos de provisionamento, configuração, administração, segurança, redes, identidade, monitoramento e automação de recursos em ambiente de nuvem.

---

## Objetivo

Desenvolver experiência prática na implementação e administração de ambientes Azure, aplicando conceitos de infraestrutura de TI em cenários próximos aos encontrados em ambientes corporativos.

O laboratório também tem como objetivo documentar a evolução técnica por meio de implementações práticas e registros de decisões, configurações e aprendizados.

---

## Tecnologias

* Microsoft Azure
* Azure Portal
* Azure CLI
* Azure Resource Manager (ARM)
* Microsoft Entra ID
* Virtual Machines
* Virtual Networks
* Network Security Groups
* Storage Accounts
* Azure Monitor
* PowerShell
* Linux
* Terraform
* Git
* GitHub

---

## Laboratórios

| #  | Laboratório                                                      | Status      |
| -- | ---------------------------------------------------------------- | ----------- |
| 01 | [Azure Regions & Resource Groups](./01-regions-resource-groups/) | ✅ Concluído |
| 02 | Virtual Machines                                                 | ⏳           |
| 03 | Networking                                                       | ⏳           |
| 04 | Identity & RBAC                                                  | ⏳           |
| 05 | Storage                                                          | ⏳           |
| 06 | Monitoring                                                       | ⏳           |
| 07 | Automation                                                       | ⏳           |
| 08 | Infrastructure as Code                                           | ⏳           |

> A lista será atualizada conforme novos laboratórios forem implementados.

---

## Abordagem

Cada laboratório busca seguir o ciclo:

```text
Conceito
   ↓
Planejamento
   ↓
Implementação
   ↓
Validação
   ↓
Troubleshooting
   ↓
Documentação
```

O objetivo não é apenas reproduzir tutoriais, mas compreender **por que cada recurso é utilizado, como os componentes se relacionam e quais decisões de infraestrutura estão envolvidas**.

---

## Organização

```text
azure-cloud-labs/
│
├── README.md
│
├── 01-regions-resource-groups/
│   └── README.md
│
├── 02-virtual-machines/
│   └── README.md
│
├── 03-networking/
│   └── README.md
│
├── 04-identity-rbac/
│   └── README.md
│
└── ...
```

Cada laboratório possui sua própria documentação técnica.

---

## Boas práticas

Durante os laboratórios serão considerados princípios de:

* Segurança
* Menor privilégio
* Organização de recursos
* Padronização
* Governança
* Controle de custos
* Disponibilidade
* Monitoramento
* Automação
* Infrastructure as Code

Recursos utilizados exclusivamente para laboratório devem ser removidos quando não forem mais necessários, evitando custos desnecessários.

**Credenciais, chaves, tokens e outras informações sensíveis nunca devem ser armazenados neste repositório.**

---

## Status do projeto

🚧 **Em desenvolvimento**

Novos laboratórios e tecnologias serão adicionados progressivamente conforme a evolução dos estudos práticos em Cloud Infrastructure.

---

## Objetivo profissional

Este projeto faz parte do desenvolvimento prático de competências em **Infraestrutura de TI e Cloud Computing**, buscando consolidar conhecimentos aplicáveis à administração e engenharia de ambientes em nuvem.

O foco é transformar conhecimento teórico em **experiência prática, documentação técnica e capacidade de troubleshooting**.
