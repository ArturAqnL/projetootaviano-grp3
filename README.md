# 📦 Serviço de Orders

## 📖 Sobre o Projeto

O Serviço de Orders foi desenvolvido pelo Grupo 3 como parte de uma arquitetura de marketplace baseada em microserviços. Sua principal responsabilidade é receber solicitações de compra realizadas pelos clientes, validar informações dos produtos e verificar a disponibilidade em estoque antes de confirmar um pedido.

O sistema foi desenvolvido utilizando Python e FastAPI, seguindo os princípios de APIs REST para garantir comunicação eficiente entre os serviços que compõem o marketplace.

---

# 🎯 Objetivo

Desenvolver uma API REST capaz de processar pedidos de forma organizada e segura, aplicando conceitos de microserviços, integração entre APIs, versionamento de código, computação em nuvem e implantação em ambiente Linux.

---

# 🛠️ Tecnologias Utilizadas

* 🐍 Python
* ⚡ FastAPI
* 📋 Pydantic
* 🔄 REST API
* 📄 JSON
* 🆔 UUID
* ☁️ AWS EC2
* 🌐 NGINX
* 🚀 Uvicorn
* 🔧 Git
* 📂 GitHub

---

# 🏗️ Arquitetura do Sistema

O Serviço de Orders integra-se aos demais serviços do marketplace.

## 📚 Serviço de Catálogo (Grupo 1)

Responsável por fornecer informações detalhadas dos produtos cadastrados.

Endpoint utilizado:

```http
GET /v1/products/{sku}
```

Retorna:

* Product ID
* Nome do produto
* SKU
* Preço unitário
* Desconto
* Preço final

---

## 📦 Serviço de Estoque (Grupo 2)

Responsável por verificar a disponibilidade dos produtos.

Endpoint utilizado:

```http
GET /v1/stock/{product_id}
```

Retorna:

* Product ID
* Quantidade disponível

---

# 📁 Estrutura do Projeto

```text
orders-service/
│
├── main.py
├── requirements.txt
├── README.md
│
├── models/
├── services/
├── routes/
└── tests/
```

---

# ⚙️ Como Executar o Projeto

## 1. Clonar o Repositório

```bash
git clone <repositorio>
cd orders-service
```

## 2. Criar Ambiente Virtual

```bash
python -m venv venv
```

## 3. Ativar Ambiente Virtual

Windows:

```bash
venv\Scripts\activate
```

Linux/Mac:

```bash
source venv/bin/activate
```

## 4. Instalar Dependências

```bash
pip install -r requirements.txt
```

## 5. Executar Aplicação

```bash
uvicorn main:app --reload
```

A API ficará disponível em:

```text
http://localhost:8000
```

---

# 🔗 Endpoints

## ➕ Criar Order

```http
POST /v1/orders
```

## 📋 Listar Orders

```http
GET /v1/orders
```

## 🔍 Buscar Order por ID

```http
GET /v1/orders/{order_id}
```

## 🗑️ Remover Order

```http
DELETE /v1/orders/{order_id}
```

## ❤️ Health Check

```http
GET /health
```

---

# 📨 Exemplo de Requisição

```json
{
  "items": [
    {
      "sku": "DELL-XPS13-2024",
      "quantity": 1
    }
  ]
}
```

---

# 📬 Exemplo de Resposta

```json
{
  "success": true,
  "data": {
    "order_id": "550e8400-e29b-41d4-a716-446655440000",
    "items": [
      {
        "sku": "DELL-XPS13-2024",
        "quantity": 1,
        "unit_price": 5499.99,
        "discount": 10.00
      }
    ],
    "total_price": 4949.99,
    "status": "confirmed"
  }
}
```

---

# 🔄 Fluxo de Funcionamento

### 1️⃣ Recebimento da Requisição

O cliente envia uma requisição para criação de uma nova order.

### 2️⃣ Consulta ao Serviço de Catálogo

O serviço consulta o catálogo para obter os dados do produto solicitado.

### 3️⃣ Consulta ao Serviço de Estoque

O sistema verifica se existe quantidade disponível para venda.

### 4️⃣ Validação

São realizadas verificações de produto existente e estoque suficiente.

### 5️⃣ Criação da Order

A order é criada utilizando um identificador UUID único.

### 6️⃣ Confirmação

O pedido é registrado e retornado ao cliente.

---

# 📊 Estrutura da Entidade Order

| Campo        | Tipo      |
| ------------ | --------- |
| order_id     | UUID      |
| sku          | VARCHAR   |
| product_name | VARCHAR   |
| quantity     | INTEGER   |
| unit_price   | NUMERIC   |
| discount     | NUMERIC   |
| total_price  | NUMERIC   |
| status       | VARCHAR   |
| created_at   | TIMESTAMP |

---

# 🧪 Testes

A API pode ser validada utilizando:

* Postman
* Insomnia
* Swagger UI

Documentação automática:

```text
/docs
```

---

# 🔧 Controle de Versão

O versionamento do projeto foi realizado utilizando Git.

Principais comandos utilizados:

```bash
git init
git add .
git commit -m "primeiro commit"
git push origin main
```

Benefícios:

* Controle das alterações
* Histórico do projeto
* Trabalho colaborativo
* Backup do código

---

# 📂 GitHub

O GitHub foi utilizado como plataforma de hospedagem do código-fonte.

Principais funcionalidades utilizadas:

* Armazenamento remoto
* Compartilhamento do projeto
* Controle de versões
* Colaboração entre integrantes

---

# 🖥️ Implantação de API FastAPI na Máquina EC2

## ☁️ Criação da Instância

O deploy do Serviço de Orders foi realizado utilizando Amazon EC2.

Configurações:

* Ubuntu Linux
* Instância t2.micro
* Camada gratuita AWS

---

## 🔐 Criação da Chave SSH

Foi criada uma chave privada para acesso remoto seguro:

```text
arquivo.pem
```

Permissão aplicada:

```bash
chmod 400 arquivo.pem
```

Conexão:

```bash
ssh -i arquivo.pem ubuntu@IP_PUBLICO
```

---

## 🌐 Configuração da Rede

Foram habilitadas as opções:

✅ SSH

✅ HTTP

✅ HTTPS

---

## 📦 Atualização da Máquina

```bash
sudo apt-get update
```

---

## 🛠️ Instalação das Dependências

```bash
sudo apt install -y python3-pip nginx
```

---

## 🌐 Configuração do NGINX

Arquivo:

```bash
sudo vim /etc/nginx/sites-enabled/fastapi_nginx
```

Configuração:

```nginx
server {
    listen 80;

    server_name IP_PUBLICO;

    location / {
        proxy_pass http://127.0.0.1:8000;
    }
}
```

Reiniciar serviço:

```bash
sudo service nginx restart
```

---

## 📥 Clonagem do Projeto

```bash
git clone URL_DO_REPOSITORIO
```

```bash
cd orders-service
```

---

## 📦 Instalação dos Requisitos

```bash
pip3 install -r requirements.txt
```

---

## 🚀 Inicialização da API

```bash
python3 -m uvicorn main:app
```

A aplicação passou a responder na porta:

```text
8000
```

---

## 🔍 Testes em Produção

Após o deploy, foi possível acessar:

```text
http://IP_PUBLICO/docs
```

Documentação automática do FastAPI.

Também foi realizado o teste do endpoint:

```text
http://IP_PUBLICO/health
```

Resposta esperada:

```json
{
  "status": "ok"
}
```

---

## ✅ Resultado Obtido

A implantação permitiu disponibilizar o Serviço de Orders na internet utilizando infraestrutura real de nuvem.

A solução foi composta por:

* FastAPI
* Uvicorn
* Linux Ubuntu
* Amazon EC2
* NGINX
* GitHub

---

## 🛑 Encerramento da Instância

Após os testes, a instância EC2 foi encerrada para evitar cobranças desnecessárias.

Passos realizados:

1. Acessar EC2 Dashboard
2. Selecionar a instância
3. Clicar em **Terminate Instance**
4. Confirmar encerramento

---

# 👥 Equipe

* Matheus
* Artur
* Max
* Diego
* Gabriel

---

# 📌 Observações Finais

✅ API REST desenvolvida com FastAPI

✅ Arquitetura baseada em microserviços

✅ Integração com Serviço de Catálogo

✅ Integração com Serviço de Estoque

✅ Operações de Orders implementadas

✅ Comunicação utilizando JSON

✅ Versionamento com Git

✅ Hospedagem do código no GitHub

✅ Deploy realizado em ambiente Linux

✅ Utilização de NGINX como proxy reverso

✅ Execução da aplicação através do Uvicorn

✅ Testes realizados localmente e em ambiente de nuvem

---

# 🎯 Conclusão

O desenvolvimento do Serviço de Orders permitiu aplicar conceitos fundamentais de APIs REST, FastAPI, integração entre microserviços e comunicação baseada em JSON. Além disso, a implantação utilizando Amazon EC2 proporcionou experiência prática com servidores Linux, configuração de NGINX, acesso remoto via SSH e publicação de aplicações em ambiente de produção.

O projeto atingiu seus objetivos ao disponibilizar uma API funcional para gerenciamento de pedidos, demonstrando na prática conceitos amplamente utilizados no mercado de desenvolvimento de software e computação em nuvem.
