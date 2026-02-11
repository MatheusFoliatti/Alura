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

------------------------------------------------------------------------

<div align="center">

<h1>📊 Pokédex Automatizada com Google Sheets + IA</h1>

<h3>Python • Google Colab • PokéAPI • Google Sheets API • Gemini AI</h3>

<br>

<img src="https://raw.githubusercontent.com/PokeAPI/media/master/logo/pokeapi_256.png" width="140"/>

<br><br>

<img src="https://img.shields.io/badge/Python-3.10+-blue?style=for-the-badge&logo=python" />
<img src="https://img.shields.io/badge/Google%20Sheets-API-green?style=for-the-badge" />
<img src="https://img.shields.io/badge/PokeAPI-REST-red?style=for-the-badge" />
<img src="https://img.shields.io/badge/Gemini-AI-orange?style=for-the-badge" />

</div>

------------------------------------------------------------------------

<h2>🚀 Visão Geral do Projeto</h2>

Este projeto cria uma <strong>Pokédex inteligente automatizada dentro do
Google Sheets</strong>, utilizando:

<ul>
<li>📡 Consumo da PokéAPI</li>
<li>📊 Escrita automatizada no Google Sheets</li>
<li>🎨 Organização por tipo com cores</li>
<li>🤖 IA (Gemini) para montar um time estratégico</li>
<li>🧠 Geração automática de estratégia para cada Pokémon</li>
</ul>

Tudo executado via <strong>Google Colab</strong>.

------------------------------------------------------------------------

<h2>📌 Fluxo do Projeto</h2>

<h3>1️⃣ Coleta de Dados</h3>

-   Busca Pokémon de múltiplas Pokédex
-   Remove duplicatas
-   Seleciona 20 Pokémon aleatórios
-   Obtém tipos, sprite oficial e nome formatado

------------------------------------------------------------------------

<h3>2️⃣ Organização por Tipo</h3>

Formato na planilha:

<pre>
Tipo | Nome do Pokémon | Sprite
</pre>

✔️ Aplicação automática de cores por tipo  
✔️ Uso da fórmula <code>=IMAGE()</code> no Sheets  
✔️ Limpeza automática antes de reescrever

------------------------------------------------------------------------

<h3>3️⃣ Escrita na Aba "Pokedex"</h3>

| Tipo | Nome | Sprite |
|------|------|--------|

-   Limpa conteúdo antigo
-   Mantém cabeçalho
-   Aplica formatação automática

------------------------------------------------------------------------

<h2>🤖 Integração com IA (Gemini)</h2>

Modelo utilizado:

<pre>
gemini-1.5-flash-latest
</pre>

A IA:

-   Analisa os 20 Pokémon disponíveis
-   Avalia equilíbrio de tipos
-   Sugere o melhor time com 6 Pokémon
-   Explica estratégia individual
-   Explica sinergia do time

------------------------------------------------------------------------

<h2>⚔️ Criação da Aba "Time"</h2>

Estrutura:

| Nome | Tipo(s) | Sprite | Estratégia |
|------|---------|--------|------------|

✔️ Extração automática da resposta da IA  
✔️ Busca novamente tipos e sprites  
✔️ Aplicação de cores baseadas no tipo primário  
✔️ Cabeçalho formatado

------------------------------------------------------------------------

<h2>🏗 Arquitetura Técnica</h2>

<h3>📦 Dependências</h3>

<pre>
pip install requests gspread google-auth-oauthlib google-generativeai
</pre>

<h3>🔐 Autenticação</h3>

-   Conta de Serviço Google
-   credentials.json
-   Permissões:
    -   spreadsheets
    -   drive

------------------------------------------------------------------------

<h2>🧠 Inteligência Aplicada</h2>

Este projeto demonstra:

-   Integração entre múltiplas APIs
-   Processamento estruturado de dados
-   Manipulação avançada do Google Sheets
-   Engenharia de Prompt
-   Parsing de resposta de LLM
-   Automação completa de pipeline

------------------------------------------------------------------------

<h2>📊 Resultado Final</h2>

O usuário obtém:

✅ Uma Pokédex organizada por tipo  
✅ Um time competitivo sugerido por IA  
✅ Estratégias detalhadas  
✅ Planilha visualmente organizada  
✅ Processo 100% automatizado

------------------------------------------------------------------------

<h2>🎯 Possíveis Melhorias Futuras</h2>

-   🔄 Atualização automática diária
-   📈 Inclusão de estatísticas base
-   🏆 Simulação de batalha entre times
-   🌐 Interface Web conectada à planilha
-   🤖 Comparação entre múltiplos modelos de IA

------------------------------------------------------------------------

<div align="center">

<h2>🔥 Projeto de Integração API + IA + Automação</h2>

<strong>Perfeito para portfólio de Backend, Automação e IA
Aplicada</strong>

</div>
