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

<div align="center">

<h1>⚡ Projeto Pokédex Inteligente</h1>
<h3>Python • API REST • Frontend Web • Consumo de API Pokémon</h3>

<img src="https://img.shields.io/badge/Python-3.10+-blue?style=for-the-badge&logo=python" />
<img src="https://img.shields.io/badge/API-REST-green?style=for-the-badge" />
<img src="https://img.shields.io/badge/Frontend-HTML%2FCSS%2FJS-orange?style=for-the-badge" />
<img src="https://img.shields.io/badge/Data-PokéAPI-red?style=for-the-badge" />

<br><br>

<img src="https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/25.png" width="120"/>
<img src="https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/6.png" width="120"/>
<img src="https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/1.png" width="120"/>

</div>

------------------------------------------------------------------------

<h2>📌 Visão Geral</h2>

Este projeto implementa uma <strong>Pokédex interativa</strong> que
consome dados da <strong>PokéAPI</strong> e exibe informações detalhadas
sobre os Pokémon.

### Funcionalidades

-   🔎 Busca por nome ou ID
-   📊 Exibição de tipos, habilidades e status
-   🖼 Renderização de sprites oficiais
-   ⚡ Interface dinâmica e responsiva

------------------------------------------------------------------------

<h2>🏗 Arquitetura</h2>

<img src="https://raw.githubusercontent.com/PokeAPI/media/master/logo/pokeapi_256.png" width="200"/>

### Backend

-   Consumo da PokéAPI
-   Tratamento de dados
-   Padronização de resposta

### Frontend

-   Interface HTML/CSS
-   Requisições assíncronas (fetch/axios)
-   Renderização dinâmica via JavaScript

------------------------------------------------------------------------

<h2>🚀 Como Executar</h2>

### 1️⃣ Clonar repositório

``` bash
git clone https://github.com/seuusuario/pokedex.git
cd pokedex
```

### 2️⃣ Instalar dependências (se houver backend)

``` bash
pip install -r requirements.txt
```

### 3️⃣ Executar

Se for apenas frontend:

``` bash
Abra o index.html no navegador
```

Se houver backend:

``` bash
uvicorn main:app --reload
```

------------------------------------------------------------------------

<h2>📂 Estrutura do Projeto</h2>

``` bash
/pokedex
 ├── index.html
 ├── style.css
 ├── script.js
 ├── /assets
 └── README.md
```

------------------------------------------------------------------------

<h2>🎯 Exemplo de Retorno da API</h2>

``` json
{
  "name": "pikachu",
  "types": ["electric"],
  "abilities": ["static", "lightning-rod"],
  "stats": {
    "hp": 35,
    "attack": 55,
    "speed": 90
  }
}
```

------------------------------------------------------------------------

<h2>🔮 Melhorias Futuras</h2>

-   🔍 Filtro por tipo
-   📱 Layout mobile aprimorado
-   🌙 Dark mode
-   ⭐ Sistema de favoritos
-   🧠 Integração com IA para descrição automática

------------------------------------------------------------------------

<div align="center">

<h2>🏁 Projeto Ideal para Portfólio</h2>
<strong>Consumo de API + Interface Dinâmica + Organização Modular</strong>

</div>
