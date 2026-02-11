# 🤖 Agente de Políticas Internas com LangChain, Gemini e LangGraph

## 📌 Visão Geral

Este projeto implementa um **Agente Inteligente Corporativo** capaz de:

-   🔎 Classificar solicitações automaticamente
-   📚 Consultar políticas internas via RAG (Retrieval Augmented
    Generation)
-   🎫 Abrir chamados quando necessário
-   🧠 Tomar decisões dinâmicas usando LangGraph

A arquitetura combina **LLM estruturado + busca vetorial + orquestração
por grafo de estados**, simulando um Service Desk corporativo
automatizado.

------------------------------------------------------------------------

## 🏗 Arquitetura

O sistema é dividido em três camadas principais:

### 1️⃣ Triagem (Classificação de Intenção)

Utiliza **Google Gemini 2.5 Flash** com saída estruturada via Pydantic.

Decisões possíveis: - `AUTO_RESOLVER` - `PEDIR_INFO` - `ABRIR_CHAMADO`

------------------------------------------------------------------------

### 2️⃣ Camada de Conhecimento (RAG)

Fluxo: 1. Carregamento de PDFs (Google Drive) 2. Divisão em chunks 3.
Geração de embeddings (Gemini) 4. Indexação com FAISS 5. Busca vetorial
6. Resposta baseada apenas no contexto encontrado

Se não houver contexto suficiente:

    Não sei.

------------------------------------------------------------------------

### 3️⃣ Orquestração (LangGraph)

Fluxo de estados:

    START → Triagem → (AUTO_RESOLVER | PEDIR_INFO | ABRIR_CHAMADO) → END

------------------------------------------------------------------------

## 🔁 Fluxo Completo

1.  Usuário envia pergunta\
2.  Agente classifica intenção\
3.  Se necessário, executa RAG\
4.  Retorna resposta contextualizada ou direciona ação

------------------------------------------------------------------------

## 🛠 Stack Tecnológica

-   Python
-   LangChain
-   LangGraph
-   Google Gemini (LLM + Embeddings)
-   FAISS
-   PyMuPDF
-   Pydantic
-   Google Colab + Drive

------------------------------------------------------------------------

## 🚀 Como Executar

### 1️⃣ Instalar dependências

``` bash
pip install langchain langgraph faiss-cpu pymupdf google-generativeai pydantic
```

### 2️⃣ Configurar variável de ambiente

``` bash
export GOOGLE_API_KEY="SUA_CHAVE_AQUI"
```

### 3️⃣ Executar o projeto

Rodar o notebook no Google Colab ou adaptar para script Python local.

------------------------------------------------------------------------

## 📂 Estrutura Recomendada

    /project
     ├── /data
     │    └── politicas.pdf
     ├── /vectorstore
     ├── agent.py
     ├── rag.py
     ├── triagem.py
     ├── graph.py
     └── README.md

------------------------------------------------------------------------

## 🎯 Casos de Uso

  Pergunta                Resultado
  ----------------------- ---------------
  Reembolso de internet   AUTO_RESOLVER
  Pedido de exceção       ABRIR_CHAMADO
  Pergunta vaga           PEDIR_INFO

------------------------------------------------------------------------

## 🔮 Melhorias Futuras

-   Persistência do vetorstore no Drive
-   API com FastAPI
-   Sistema real de abertura de chamados
-   Autenticação por usuário
-   Logs estruturados
-   Memória de conversação

------------------------------------------------------------------------

## 🏁 Resultado

Um agente corporativo completo com:

-   Classificação semântica
-   RAG com busca vetorial
-   Orquestração por grafo de estados
-   Controle de contexto e segurança de informação

------------------------------------------------------------------------

## 📜 Licença

Uso educacional e corporativo interno.
