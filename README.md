# 🚀 gRPC Server com Golang e Evans

Este projeto implementa um servidor **gRPC** utilizando **Golang** e permite interações com ele através do **Evans**, uma ferramenta de cliente universal para serviços gRPC.

---

## 📋 **Índice**
1. [Pré-requisitos](#pré-requisitos)
2. [Tecnologias Utilizadas](#tecnologias-utilizadas)
3. [Estrutura do Projeto](#estrutura-do-projeto)
4. [Instalação e Configuração](#instalação-e-configuração)
5. [Rodando o Servidor gRPC](#rodando-o-servidor-grpc)
6. [Testando o Servidor com Evans](#testando-o-servidor-com-evans)
7. [Contribuição](#contribuição)
8. [Licença](#licença)

---

## ✅ **Pré-requisitos**

Certifique-se de ter as seguintes ferramentas instaladas na sua máquina:
- **Go** (versão 1.18 ou superior): [Download aqui](https://golang.org/dl/)
- **gRPC** e **Protocol Buffers**: Instalado no seu ambiente Go.
- **Evans** (para testar o servidor): [Evans GitHub](https://github.com/ktr0731/evans)

---

## 🛠️ **Tecnologias Utilizadas**

- **Golang**: Linguagem principal para o desenvolvimento do servidor.  
- **gRPC**: Framework de comunicação eficiente e de alto desempenho.  
- **Protocol Buffers**: Definição das mensagens e serviços.  
- **Evans**: Ferramenta de linha de comando para interagir com servidores gRPC.

---

## 📂 **Estrutura do Projeto**

```plaintext
📦 grpc-server-go
│
├── cmd/
│   └── grpcServer/
│       └── main.go       # Arquivo principal para iniciar o servidor gRPC
│
├── internal/
│   ├── database/         # Simulação de banco de dados
│   ├── pb/               # Arquivos gerados pelo Protocol Buffers
│   └── service/          # Implementação dos serviços gRPC
│
├── proto/
│   └── category.proto    # Definição do serviço gRPC (protos)
│
├── go.mod                # Módulo Go
├── go.sum                # Dependências do Go
└── db.sqlite             # Banco de dados SQLite (exemplo)
```

---

## 🚀 **Instalação e Configuração**

1. **Clone o repositório:**
   ```bash
   git clone https://github.com/ThiagolFPereira/gRPC-golang.git
   cd gRPC-golang
   ```

2. **Instale as dependências do projeto:**
   ```bash
   go mod tidy
   ```

3. **Gere os arquivos a partir do `.proto` (caso não tenha):**
   ```bash
   protoc --go_out=. --go-grpc_out=. proto/category.proto
   ```

---

## ▶️ **Rodando o Servidor gRPC**

Execute o seguinte comando para iniciar o servidor:

```bash
go run cmd/grpcServer/main.go
```

Por padrão, o servidor será iniciado na porta **50051**.

---

## 🥯 **Testando o Servidor com Evans**

Após iniciar o servidor, você pode usar o **Evans** para interagir com os serviços gRPC. Execute os comandos abaixo:

1. **Inicie o Evans na porta do servidor:**
   ```bash
   evans -r repl
   ```

2. **Conecte-se ao serviço `CategoryService`:**
   ```bash
   service CategoryService
   ```

3. **Chame um método, por exemplo, `CreateCategory`:**
   ```bash
   call CreateCategory
   ```

   **Exemplo de input:**
   ```plaintext
   name (TYPE_STRING) => Thiago
   description (TYPE_STRING) => gRPC Golang
   ```

4. **Saída esperada:**
   ```json
   {
     "description": "gRPC Golang",
     "id": "f656904-4ab3-463a-b7b1-a5aaa8fd49bf",
     "name": "Thiago"
   }
   ```

---