# 📦 API de Produtos

## 📖 Sobre o projeto

Esta aplicação consiste em uma API REST desenvolvida em Python para gerenciamento de produtos. O sistema permite realizar operações básicas de CRUD (Create, Read, Update, Delete), permitindo o controle de um catálogo de produtos.

O projeto foi desenvolvido a partir de um modelo base disponibilizado em aula, com adaptações realizadas pelo grupo.

---

## 🎯 Objetivo

Desenvolver uma API funcional seguindo boas práticas de organização, versionamento e documentação, garantindo colaboração entre os integrantes.

---

## 🛠️ Tecnologias utilizadas

* Python
* Flask
* SQLite
* Git e GitHub

---

## 📁 Estrutura do projeto

```
api-produtos/
│── app.py
│── database.py
│── models/
│   └── produto.py
│── routes/
│   └── produto_routes.py
│── requirements.txt
│── README.md
```

---

## ⚙️ Como executar

### 1. Clone o repositório

```
git clone https://github.com/seu-usuario/api-produtos.git
cd api-produtos
```

### 2. Crie um ambiente virtual

```
python -m venv venv
```

### 3. Ative o ambiente

Windows:

```
venv\Scripts\activate
```

Linux/Mac:

```
source venv/bin/activate
```

### 4. Instale as dependências

```
pip install -r requirements.txt
```

### 5. Execute a aplicação

```
python app.py
```

A API estará disponível em:

```
http://localhost:5000
```

---

## 🔗 Endpoints

### Listar todos os produtos

```
GET /produtos
```

### Buscar produto por ID

```
GET /produtos/{id}
```

### Criar novo produto

```
POST /produtos
```

Exemplo de JSON:

```json
{
  "nome": "Produto Exemplo",
  "preco": 99.90,
  "descricao": "Descrição do produto"
}
```

### Atualizar produto

```
PUT /produtos/{id}
```

### Remover produto

```
DELETE /produtos/{id}
```

---

## 🧪 Testes

A API pode ser testada utilizando ferramentas como Postman ou Insomnia.

---

## 👥 Equipe

* Nome do Integrante 1
* Nome do Integrante 2
* Nome do Integrante 3

---

## 📚 Referência

https://github.com/otavianosilverio/Api-Produtos-Python

---

## 📌 Observações finais

* Todos os integrantes possuem acesso ao repositório
* O projeto segue o padrão REST
* O versionamento foi feito com Git
