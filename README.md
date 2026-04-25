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

* Matheus
* Artur 
* Max
* Diego
* Gabriel

---

## 📚 Referência

https://github.com/otavianosilverio/Api-Produtos-Python

---

## 📌 Observações finais

* Todos os integrantes possuem acesso ao repositório
* O projeto segue o padrão REST
* O versionamento foi feito com Git

## 🖥️ Implantação de API FastApi na Máquina EC2
### 1. Fazer Login na controle AWS: aws.amazon.com

### 2. Clicar no "EC2" no Canto Esquerdo da tela.

### 3. Clicar no botão Laranja "Launch Instances" no canto direito superior.

### 4. Colocar nome, imagem da máquina (Linux), e a versão.

### 5. Instance Type
Escolher o t2.micro (gratuito)

### 6. Key Pair (Login)
1) Create new Key pair: Escolher um nome --> Create
   Deve aparecer uma chave na pasta de Downloads
   
### 7. Network Settings
1) Deixar marcado a opção "Allow SSH traffic from" e do lado disso "Anywhere"
2) Deixar marcado a opção "Allow HTTP traffic from the internet" e "Allow HTTPs traffic from the internet"
   
### 8.Checagem Final
Depois de conferir todas as configurações selecionadas, clicar no botão laranja "Launch Instance"

### 9. Ver funcionando
Ir ao "EC2 Dashboard" e ver as Instâncias funcionando, "Instance State" tem que estar Running✅
Obs.: Se não estiver Running pode estar pendente, é só esperar.
(CLicar no ID da Instância vê o resumo da instância, incluindo o seu endereço, IP público

### 10. Conectar-se à instância
1) Clicar em "Connect" no canto superior direito
2) Clicar na opção de "SSH client", se estiver usando Linux ou Mac as instruções devem estar corretas. Se for Windows pesquisar "como fazer SSH a partir do Windows"

### 11. Usar o arquivo de chave privada SSH ".pem" criado anteriormente, alterar as permissões para que não seja visível publicamente, e então conectar à instância usando o comando escrito no " Example:"
1) (Deve estar no diretório onde copiou a chave ".pem"). Dar um "ls" no console, deve aparecer a chave ".pem"
2) Dar o comando "chmod 400 "nomedachave.pem""
3) Copiar o comando SSH do "Example:" (Já está preenchido com o nome do arquivo .pem e o endereço da instânci EC2.)
4) Colar o comando no console.
5) Fará uma pergunta, responder "yes". Agora estará conectado à instância.

### 12. Atualizar e instalar as dependências na máquina
1) Escrever no console "sudo apt-get update". (Vai atualizar todos os repositórios que temos acesso a todos os softwares mais recentes)
2) Escrever no console "sudo apt install -y python3-pip nginx".
   
### 13. Direcionar o tráfego depois de iniciar o software NGINX
1) Criar um novo arquivo dentro deste diretório, dar o comando "sudo vim /etc/nginx/sites-enabled/fastapi_nginx" no console.
2) Preencher o arquivo de configuração do NGINX, escrevendo no console o comando abaixo:
   server {
           listen 80;
           server_name "copiar o Public IPv4 adress e colar aqui";
           location / {
                   proxy_pass http://127.0.0.1:8000;
           }
3) Salvar o arquivo e sair
4) Reiniciar o servidor NGINX, dando o comando "sudo service nginx restart".

### 15. Clonar o projeto FastAPI neste host
1) Voltar ao projeto GitHub, ir para "code" e depois "Clone"
2) Com o HTTPS selecionado, copiar o comando que está abaixo e voltar para o terminal
3) Digitar "git clone " e colar o link que copiou na etapa anterior
4) Digitar "ls", deve aparecer o nome do diretório
5) Entrar no diretório digitando "cd "nome do diretório"/"
6) Checar se os arquivos estão lá, digitando "ls". (Deve aparecer o main.py e requirements.txt, por exemplo)

### 16. Instalar os requisitos
1) Entrar no arquivo de requisitos digitando "cat requirements.txt". (Há apenas o "fastapi" e o "uvicorn")
2) Digitar "pip3 install -r requirements.txt".

### 17. Iniciar o servidor FastAPI
1) Dar "clear" no console
2) Digitar "python3 -m uvicorn main:app"
3) Se voltar ao Public IPv4 adress na instância e clicar em "open adress" e ao invés de HTTPS ficar HTTP e dar Enter conseguirá ver que a API pode realmente ser chamada a partir deste endereço

### 18. Comandos para testar junto ao IP
1) "númerodoip"/list-books
2) "númerodoip"/docs

### 19. Encerramento
Antes de encerrar, deve voltar ao console e realmente terminar esta instância. Caso contrário, pode ser cobrado por ele rodando mesmo se tiver na camada gratuita.
1) Na aba "Instances", clique na caixa para marcar a FastAPI que está em funcionamento, botão direito em cima dela e clicar em "Terminate Instance".


