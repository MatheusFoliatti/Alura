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

::: {align="center"}
```{=html}
<h1 style="font-size:42px;">
```
⚡ Projeto Pokédex Inteligente
```{=html}
</h1>
```
```{=html}
<h3>
```
Python • API REST • Frontend Web • Consumo de API Pokémon
```{=html}
</h3>
```
`<img src="https://img.shields.io/badge/Python-3.10+-blue?style=for-the-badge&logo=python" />`{=html}
`<img src="https://img.shields.io/badge/API-REST-green?style=for-the-badge" />`{=html}
`<img src="https://img.shields.io/badge/Frontend-HTML%2FCSS%2FJS-orange?style=for-the-badge" />`{=html}
`<img src="https://img.shields.io/badge/Data-PokéAPI-red?style=for-the-badge" />`{=html}

`<br>`{=html}`<br>`{=html}

`<img src="https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/25.png" width="150"/>`{=html}
`<img src="https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/6.png" width="150"/>`{=html}
`<img src="https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/1.png" width="150"/>`{=html}
:::

------------------------------------------------------------------------

```{=html}
<h2 style="font-size:32px;">
```
📌 Visão Geral
```{=html}
</h2>
```
Este projeto implementa uma `<strong>`{=html}Pokédex
interativa`</strong>`{=html} que consome dados da
`<strong>`{=html}PokéAPI`</strong>`{=html} e exibe informações
detalhadas sobre os Pokémon.

Funcionalidades principais:

```{=html}
<ul>
```
```{=html}
<li>
```
🔎 Busca por nome ou ID
```{=html}
</li>
```
```{=html}
<li>
```
📊 Exibição de tipos, habilidades e status
```{=html}
</li>
```
```{=html}
<li>
```
🖼 Renderização de sprites oficiais
```{=html}
</li>
```
```{=html}
<li>
```
⚡ Interface dinâmica e responsiva
```{=html}
</li>
```
```{=html}
</ul>
```

------------------------------------------------------------------------

```{=html}
<h2 style="font-size:32px;">
```
🏗 Arquitetura
```{=html}
</h2>
```
`<img src="https://miro.medium.com/v2/resize:fit:1400/1*api_architecture_example.png" width="650"/>`{=html}

```{=html}
<h3 style="font-size:24px;">
```
Backend
```{=html}
</h3>
```
-   Consumo da PokéAPI\
-   Tratamento de dados\
-   Padronização de resposta

```{=html}
<h3 style="font-size:24px;">
```
Frontend
```{=html}
</h3>
```
-   Interface HTML/CSS\
-   Requisições assíncronas (fetch/axios)\
-   Renderização dinâmica via JavaScript

------------------------------------------------------------------------

```{=html}
<h2 style="font-size:32px;">
```
🚀 Como Executar
```{=html}
</h2>
```
```{=html}
<h3>
```
1️⃣ Clonar repositório
```{=html}
</h3>
```
```{=html}
<pre>
git clone https://github.com/seuusuario/pokedex.git
cd pokedex
</pre>
```
```{=html}
<h3>
```
2️⃣ Instalar dependências (caso tenha backend)
```{=html}
</h3>
```
```{=html}
<pre>
pip install -r requirements.txt
</pre>
```
```{=html}
<h3>
```
3️⃣ Executar
```{=html}
</h3>
```
Se for apenas frontend:

```{=html}
<pre>
Abra o index.html no navegador
</pre>
```
Se houver backend:

```{=html}
<pre>
uvicorn main:app --reload
</pre>
```

------------------------------------------------------------------------

```{=html}
<h2 style="font-size:32px;">
```
📂 Estrutura do Projeto
```{=html}
</h2>
```
```{=html}
<pre>
/pokedex
 ├── index.html
 ├── style.css
 ├── script.js
 ├── /assets
 └── README.md
</pre>
```

------------------------------------------------------------------------

```{=html}
<h2 style="font-size:32px;">
```
🎯 Exemplo de Retorno da API
```{=html}
</h2>
```
```{=html}
<pre>
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
</pre>
```

------------------------------------------------------------------------

```{=html}
<h2 style="font-size:32px;">
```
🔮 Melhorias Futuras
```{=html}
</h2>
```
-   🔍 Filtro por tipo\
-   📱 Layout mobile aprimorado\
-   🌙 Dark mode\
-   ⭐ Sistema de favoritos\
-   🧠 Integração com IA para descrição automática

------------------------------------------------------------------------

::: {align="center"}
```{=html}
<h2 style="font-size:34px;">
```
🏁 Projeto Ideal para Portfólio
```{=html}
</h2>
```
`<strong>`{=html}Consumo de API + Interface Dinâmica + Organização
Modular`</strong>`{=html}

`<br>`{=html}`<br>`{=html}
:::
