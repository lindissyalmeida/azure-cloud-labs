# Azure Policy e Resource Lock — Laboratório de Governança

## 📌 Objetivo

Praticar conceitos de **governança e proteção de recursos no Microsoft Azure**, utilizando:

- Azure Policy
- Resource Lock
- Azure Portal
- Azure CLI

O laboratório teve como objetivo entender, na prática, a diferença entre uma **Policy**, que define regras para recursos e operações, e um **Resource Lock**, utilizado para proteger recursos contra exclusão ou alteração.

---

## 🧰 Ambiente utilizado

- Microsoft Azure
- Resource Group: `RG-LAB-DIA1`
- Região permitida: `brazilsouth`
- Azure CLI
- Azure Portal
- Storage Account

---

# 1. Azure Policy

## 📖 Conceito

Uma Azure Policy permite definir regras de governança para controlar ou avaliar recursos dentro de determinado escopo.

Neste laboratório foi utilizada a Policy:

**Allowed locations**

A regra foi configurada para permitir somente recursos localizados em:

```text
Brazil South (brazilsouth)
```

O efeito utilizado foi:

```text
Deny
```

Isso significa que uma implantação que não atender à regra será bloqueada.

---

## 🔎 Identificação da Policy

A definição utilizada foi:

```text
Allowed locations
```

ID:

```text
e56962a6-4747-49cd-b67b-bf8b01975c4c
```

A definição da Policy representa a regra disponível no Azure. Para que ela passe a atuar sobre recursos, é necessário criar uma **Policy Assignment**.

---

## 🎯 Escopo da Policy

A Policy foi aplicada ao Resource Group:

```text
RG-LAB-DIA1
```

Dessa forma, a regra passou a ser aplicada aos recursos criados nesse escopo.

---

## 💻 Aplicação utilizando Azure CLI

A atribuição foi realizada utilizando:

```powershell
az policy assignment create `
  --name "AllowedLocations-Lab" `
  --display-name "Allowed Locations - LAB" `
  --policy "e56962a6-4747-49cd-b67b-bf8b01975c4c" `
  --scope "/subscriptions/<SUBSCRIPTION_ID>/resourceGroups/RG-LAB-DIA1" `
  --params '{"listOfAllowedLocations":{"value":["brazilsouth"]},"effect":{"value":"Deny"}}'
```

> O Subscription ID foi omitido da documentação pública do GitHub.

---

# 2. Teste da Azure Policy

## ❌ Teste com região não permitida

Foi realizada uma tentativa de criação de um Storage Account utilizando uma região diferente de `brazilsouth`.

Exemplo:

```powershell
az storage account create `
  --name lindlabpolicytest `
  --resource-group RG-LAB-DIA1 `
  --location eastus `
  --sku Standard_LRS
```

### Resultado

A operação foi bloqueada pela Azure Policy.

O Azure retornou um erro indicando que a operação foi negada pela política.

```text
RequestDisallowedByPolicy
```

---

## ✅ Teste com região permitida

Em seguida, o Storage Account foi criado utilizando:

```text
brazilsouth
```

A criação foi realizada com sucesso.

### Resultado observado

```text
eastus       → ❌ Bloqueado
brazilsouth  → ✅ Permitido
```

---

# 3. Validação utilizando Azure Portal

A mesma regra foi validada diretamente pelo Portal do Azure.

Foi realizada uma tentativa de criação de um Storage Account em uma região não permitida.

O Portal apresentou:

```text
O recurso não foi permitido pela política.
```

Código:

```text
RequestDisallowedByPolicy
```

A mensagem também identificou a Policy responsável:

```text
Allowed Locations - LAB
```

Isso confirmou que a Policy criada via CLI também estava sendo aplicada às operações realizadas pelo Portal.

---

# 4. Resource Lock

## 📖 Conceito

O Resource Lock é utilizado para proteger recursos contra determinadas operações.

Neste laboratório foi utilizado o tipo:

```text
CanNotDelete
```

Esse tipo de Lock permite alterações no recurso, mas impede sua exclusão.

---

## 🔒 Criação do Resource Lock

Foi criado um Lock no Storage Account:

```text
lindlabpolicytest
```

Com o comando:

```powershell
az lock create `
  --name "Protecao-Lab" `
  --lock-type CanNotDelete `
  --resource-group RG-LAB-DIA1 `
  --resource-name lindlabpolicytest `
  --resource-type Microsoft.Storage/storageAccounts
```

---

# 5. Teste do Resource Lock

Foi realizada uma tentativa de exclusão do Storage Account:

```powershell
az storage account delete `
  --name lindlabpolicytest `
  --resource-group RG-LAB-DIA1 `
  --yes
```

### Resultado

A exclusão foi bloqueada.

O Azure retornou:

```text
Code: ScopeLocked
```

Indicando que o recurso estava protegido por um Resource Lock.

---

# 6. Remoção do Lock

Após o teste, o Lock foi removido:

```powershell
az lock delete `
  --name "Protecao-Lab" `
  --resource-group RG-LAB-DIA1 `
  --resource-name lindlabpolicytest `
  --resource-type Microsoft.Storage/storageAccounts
```

Depois da remoção do Lock, o Storage Account pôde ser excluído.

O Resource Group utilizado no laboratório também foi removido posteriormente para evitar a permanência de recursos desnecessários.

---

# 🧠 Azure Policy × Resource Lock

| Recurso | Função |
|---|---|
| **Azure Policy** | Define e aplica regras de governança |
| **Resource Lock** | Protege recursos contra determinadas operações |
| **Policy — Deny** | Pode impedir uma implantação/operação que viole uma regra |
| **CanNotDelete** | Impede a exclusão do recurso |
| **Portal** | Interface gráfica para gerenciamento |
| **Azure CLI** | Gerenciamento por comandos |

### Resumo mental

```text
Azure Policy
    ↓
"Essa operação atende às regras?"

Resource Lock
    ↓
"Esse recurso está protegido contra essa operação?"
```

---

# 🎯 Principais aprendizados

Durante o laboratório foi possível praticar:

- Criação e aplicação de Azure Policy
- Diferença entre Policy Definition e Policy Assignment
- Definição de escopo para uma Policy
- Utilização do efeito `Deny`
- Restrição de regiões para recursos
- Validação de Policy via Azure CLI
- Validação de Policy via Azure Portal
- Criação de Resource Lock
- Diferença entre governança e proteção de recursos
- Utilização do `CanNotDelete`
- Interpretação dos erros `RequestDisallowedByPolicy` e `ScopeLocked`
- Limpeza dos recursos após o laboratório

---

## Resultado

Laboratório concluído com sucesso, demonstrando na prática mecanismos básicos de **governança, conformidade e proteção de recursos no Azure**.
