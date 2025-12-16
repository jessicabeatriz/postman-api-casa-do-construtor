# 🧪 Automação de Testes de API - Casa do Construtor

Este projeto contém uma **Collection do Postman** criada para validar a API "Booster" da Casa do Construtor.

O cenário automatizado realiza um fluxo de **teste dinâmico**, onde dados extraídos da primeira requisição alimentam a segunda, garantindo a integridade do fluxo de dados.

🔗 **Swagger de Referência:** [API Booster Documentation](https://api-dev-oci.casadoconstrutor.com.br/api-booster/swagger-ui/index.html)

---

## 🎯 Objetivo do Desafio

Crie uma Collection no Postman contendo um cenário de teste automatizado que realize o seguinte fluxo:
1. **Consulta Geral:** Identifique no Swagger um endpoint que retorna uma listagem (pode ser de áreas, softSkilss, níveis ou similar).
2. **Extração de Dados:** Crie um script na aba "scrits" que capture dinamicamente o ID (ou identificador principal) do primeiro item retornado nessa lista e armazene-o em uma variável de ambiente ou de coleção.
3. **Consulta Específica:** Crie uma segunda requisição que utilize essa variável capturada para consultar os detalhes desse item específico.
4. **Validações (Assertions):** Em ambas as requisições, implemente testes para validar:
   - Status Code (ex: 200).
   - Tempo de resposta (ex: abaixo de 2s).
   - Validar se o corpo da resposta não está vazio.
     
---

## 🚀 Cenário Automatizado

A collection executa o seguinte fluxo de validação:

### 1. Listagem de Áreas (`GET /v1/areas`)
* **Objetivo:** Garantir que a lista de áreas está sendo retornada corretamente.
* **Validações:**
    * ✅ Status Code 200.
    * ✅ Tempo de resposta abaixo de 2000ms.
    * ✅ O corpo da resposta não está vazio e é um JSON válido.
* **Script Dinâmico:** Captura automaticamente o `idArea` do primeiro item da lista e armazena na variável de coleção `{{itemId}}`.

### 2. Detalhe da Área (`GET /v1/areas/{{itemId}}`)
* **Objetivo:** Consultar os detalhes de uma área específica utilizando o ID capturado no passo anterior.
* **Validações:**
    * ✅ Status Code 200.
    * ✅ Tempo de resposta abaixo de 2000ms.
    * ✅ **Contrato:** Valida se o `idArea` retornado no corpo da resposta é idêntico ao `{{itemId}}` solicitado.

---

## ▶️ Como Executar o Projeto

### Pré-requisitos
* [Postman](https://www.postman.com/downloads/) instalado.
* Arquivo da Collection (`.json`) presente neste repositório.

### Passo a Passo

1️⃣  **Clone o repositório:**

    git clone https://github.com/jessicabeatriz/postman-api-casa-do-construtor.git

    
2️⃣  **Importe no Postman:**
- Abra o Postman.
- Clique em **Import** (canto superior esquerdo).
- Selecione o arquivo `.json` da Collection que está na pasta do projeto.

3️⃣  **Rodar os Testes:**
- Abra a Collection importada.
- Clique no botão **Run** (ou "Run Collection").
- Acompanhe a execução dos testes na janela do *Collection Runner*.

---
📸 Evidências

<img width="1359" height="723" alt="image" src="https://github.com/user-attachments/assets/02f638e4-df8e-4e48-bc6e-b3c1f686aa8b" />

---

## 👩‍💻 Autora

Jéssica Beatriz da Silva

QA | Desenvolvedora Web

