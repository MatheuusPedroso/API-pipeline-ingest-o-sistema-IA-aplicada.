
# Wine Data API (Embrapa Data Pipeline)!


API com dados da produção vitivinícola brasileira, baseada em scraping da Embrapa. Foi desenvolvida para facilitar o consumo de informações por dashboards, modelos de machine learning ou aplicações front-end.

## 📚 Problema que resolve

A Embrapa disponibiliza os dados vitivinícolas em HTML de forma pouco acessível. Esta API oferece uma forma estruturada e filtrável de acesso a esses dados, com fallback local (cache) em caso de instabilidade do site.

## 🧰 Stack utilizada

- **Python 3.9**
- **FastAPI**
- **BeautifulSoup** (scraping)
- **Render** (deploy)
- **JWT** (autenticação)

## 🚫 Requisitos para executar localmente

```bash
python -m venv venv
source venv/bin/activate  # ou venv\Scripts\activate no Windows
pip install -r requirements.txt
uvicorn main:app --reload
```

Acesse: `http://127.0.0.1:8000/docs`

## 🌐 Link em produção (Render)

[https://api-tech-challenge.onrender.com/](https://api-tech-challenge.onrender.com/)

## 🌐 Link Github

https://github.com/MatheuusPedroso/api_tech_challenge

## 🔧 Como autenticar

Obtenha o token via:

```
POST /token
username: master
password: Master@123
```

Utilize o token retornado como `Bearer` nos endpoints protegidos.

## 🔠 Filtros disponíveis

Todos os endpoints aceitam o filtro de ano por path:

```
GET /producao/2022
GET /comercializacao/2020
GET /exportacao/2018
```

## 🔎 Endpoints principais

```
GET /producao/{ano}
GET /comercializacao/{ano}
GET /processamento/{ano}
GET /importacao/{ano}
GET /exportacao/{ano}
```

## 🌐 Documentação Swagger

[https://api-tech-challenge.onrender.com/docs](https://api-tech-challenge.onrender.com/docs)

## 📽️ Vídeo de apresentação

https://www.loom.com/share/b0149381373f474f957eadbd581a8a10?sid=b87bb8a9-06d2-4226-a3bb-4215dbff5e1d

## 🛀 Diagrama de arquitetura

+------------------+
|     Embrapa      |
+--------+---------+
         |
         v
 +-------+-------+
 |    Scraper     |
 +-------+-------+
         |
         v
 +---------------+     (fallback)
 |   cache/.json  | <-------------------+
 +-------+-------+                      |
         |                              |
         v                              |
 +----------------------+              |
 |     FastAPI App      |--------------+
 +----------------------+
         |
         v
+------------------------------+
| Swagger UI, BI Tools, etc... |
+------------------------------+
```

## 📄 Como rodar os testes (opcional)

```bash
pytest
```

## 📊 Boas práticas

- Estrutura modular (app/, separação de responsabilidades)
- Fallback com cache local
- Filtros por ano
- JWT Token
- Variáveis sensíveis ocultadas com `.env`
- `.gitignore` bem configurado
- Comentários e commits claros

