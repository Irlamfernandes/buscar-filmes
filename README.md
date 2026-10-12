# BuscarFilmes

Aplicação web para buscar filmes, ver detalhes e descobrir onde assistir. Feita com **Django**, consumindo a API do **TMDb** e com busca por descrição usando **IA (Google Gemini)**.

Projeto acadêmico feito em grupo na faculdade, entre agosto e outubro de 2025. Ele valeu a nota das duas provas da disciplina (P1 e P2).

## Funcionalidades

- **Busca por título**: resultados ordenados por popularidade, com pôster, sinopse e as plataformas de streaming onde o filme está disponível
- **Busca por descrição com IA**: o usuário descreve o filme ("aquele em que um homem fica preso em Marte...") e o Gemini identifica o título mais provável antes de buscar no TMDb
- **Detalhes do filme**: trailer, gêneros, duração, avaliação, elenco, imagens, críticas e recomendações
- **Listas de filmes**: populares, mais bem avaliados, próximos lançamentos e em cartaz, com botão "Carregar mais" via AJAX
- **Sobre**: página com a proposta do projeto e a equipe

## Tecnologias

- Python e Django 5
- [API do TMDb](https://developer.themoviedb.org/) para os dados dos filmes e provedores de streaming
- Google Gemini (`google-genai`) para a busca por descrição
- PostgreSQL
- Docker, Docker Compose e Makefile

## Como executar

Pré-requisitos: [Docker](https://docs.docker.com/get-docker/) e Docker Compose, além de uma chave da [API do TMDb](https://www.themoviedb.org/settings/api) e uma do [Google AI Studio](https://aistudio.google.com/apikey).

1. Clone o repositório:

   ```bash
   git clone https://github.com/Irlamfernandes/buscar-filmes.git
   cd buscar-filmes
   ```

2. Crie o arquivo `env_file/.env` com as chaves:

   ```env
   TMDB_API_KEY=sua_chave_tmdb
   GEMINI_API_KEY=sua_chave_gemini
   ```

3. Suba os containers:

   ```bash
   make build
   make up
   ```

   Sem `make`, use `docker compose up --build`.

4. Acesse em [http://localhost:8000](http://localhost:8000).

Outros comandos do Makefile: `make up-detached`, `make down`, `make rebuild` e `make bash`.

## Estrutura

```
├── core/                  # configurações do Django (settings, urls)
├── coreapp/
│   ├── views.py           # busca, detalhes, filmes populares e sobre
│   ├── services.py        # cliente da API do TMDb
│   ├── ia_services.py     # integração com o Google Gemini
│   └── rotas_streaming.py # links das plataformas de streaming
├── templates/coreapp/     # páginas HTML
├── static/                # CSS e imagens
├── Dockerfile
├── docker-compose.yml
└── Makefile
```

## Equipe

O projeto foi organizado com branches e pull requests no GitHub (mais de 40 PRs).

- Bruno Almeida da Silva
- Emanuel Rosa Franco
- Irlam da Silva Fernandes ([@Irlamfernandes](https://github.com/Irlamfernandes))
- Josué Luis dos S. P. de Barros
- Natan Jordão Pedroso
- Paulo Vitor Leal Lavinas
- Rafael Ferreira Lima
