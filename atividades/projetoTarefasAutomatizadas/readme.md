# Automação com AWS Lambda, S3 e DynamoDB ☁️

## 📘 Contexto
Este repositório documenta o que foi aprendido em um **projeto guiado** sobre **tarefas automatizadas na AWS**, desenvolvido em aula com orientação do professor.  
O foco é compreender **como os serviços se integram** para criar um fluxo de processamento automatizado utilizando a arquitetura **serverless**.

---

## 🧩 Conceitos aprendidos

### 🗂️ Amazon S3
O **Amazon S3 (Simple Storage Service)** é um serviço de **armazenamento em nuvem** da AWS.  
Permite armazenar e acessar dados (como arquivos e imagens) de forma escalável, durável e segura.

### 🧠 AWS Lambda
O **AWS Lambda** é um serviço de **computação serverless** que executa código em resposta a eventos, **sem necessidade de gerenciar servidores**.  
Com o Lambda, você paga apenas pelo tempo de execução do código, o que torna o modelo eficiente e escalável.

### 🗃️ Amazon DynamoDB
O **Amazon DynamoDB** é um **banco de dados NoSQL totalmente gerenciado**, ideal para aplicações que exigem alta disponibilidade e desempenho.  
Foi utilizado para armazenar os dados processados pela função Lambda.

### 🌐 API Gateway
O **Amazon API Gateway** permite expor **APIs RESTful**, conectando serviços serverless e facilitando o acesso aos dados processados.

---

## ⚙️ Arquitetura estudada

O projeto guiado apresentou um fluxo de automação **100% serverless**, composto por:

1. 🧍‍♀️ O usuário faz upload de um arquivo para um bucket S3.  
2. ☁️ O evento de upload aciona uma **função Lambda (Python)**.  
3. ⚙️ A Lambda processa o arquivo e grava os dados em uma tabela **DynamoDB**.  
4. 🔍 Outra função Lambda é acionada via **API Gateway** para consultar e exibir as informações do DynamoDB.

---

## 🧰 Ferramentas utilizadas
- **AWS Lambda**  
- **Amazon S3**  
- **Amazon DynamoDB**  
- **Amazon API Gateway**  
- **LocalStack** (para emulação local dos serviços AWS)  
- **Python** (para as funções Lambda)

---

## 🎯 Objetivo do aprendizado
O objetivo foi **entender como os serviços AWS se integram** em uma arquitetura serverless e como **eventos automatizados** podem ser usados para criar fluxos de processamento completos — desde o upload de arquivos até a exposição dos dados por uma API.

---

## ✍️ Observação
> ⚠️ Este repositório não contém o código original do projeto guiado.  
> Ele foi criado apenas para documentar o aprendizado adquirido durante as aulas, com base nas práticas e explicações do professor.

---

## 📚 Principais aprendizados
- Criar e configurar buckets no **Amazon S3**.  
- Configurar funções **AWS Lambda** com permissões específicas.  
- Integrar **Lambda e DynamoDB** para persistência de dados.  
- Disparar funções via **eventos S3**.  
- Expor dados via **API Gateway**.  
- Testar tudo localmente com **LocalStack**.

---

> 💡 Este estudo reforçou a importância da **automação**, **integração entre serviços** e **infraestrutura como código (IaC)** em soluções modernas na nuvem.
