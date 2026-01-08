# 🚚 Dashboard de Logística - Controle de Malha Fina

Este é um painel interativo desenvolvido em Python com **Streamlit** para monitoramento de performance logística. O foco principal é a análise do fluxo de veículos, comparando volumes liberados versus veículos retidos para auditoria ("Malha Fina").

Desenvolvido por **Clayton S. Silva**.

## 📊 Funcionalidades

*   **KPIs em Tempo Real:** Visualização de fluxo total, veículos liberados, retidos e taxa de retenção global.
*   **Gráficos Interativos:**
    *   Rankings de Transportadoras (Volume e Retenção).
    *   Funil do Processo (Sorteio).
    *   Mapa de Calor (Risco por dia da semana).
    *   Análises temporais (Diária, Mensal e Anual).
*   **Gestão de Dados (CRUD):**
    *   Upload de arquivos (CSV, Excel, DB).
    *   Inserção manual de registros.
    *   Edição de dados diretamente na tabela (requer login).
*   **Persistência na Nuvem:** Integração com a API do GitHub para salvar e ler dados (funciona como um banco de dados remoto).
*   **Exportação:** Download de relatórios filtrados em Excel (.xlsx) e backup do banco de dados (.db).

## 🛠️ Tecnologias Utilizadas

*   [Streamlit](https://streamlit.io/) - Framework para Web Apps de Dados.
*   [Pandas](https://pandas.pydata.org/) - Manipulação e análise de dados.
*   [Plotly Express](https://plotly.com/python/plotly-express/) - Visualização de dados interativa.
*   [PyGithub](https://github.com/PyGithub/PyGithub) - Integração para salvar dados no repositório.
*   [SQLAlchemy](https://www.sqlalchemy.org/) - Manipulação de banco de dados SQL.

## 🚀 Como Rodar Localmente

1.  **Clone o repositório:**
    ```bash
    git clone https://github.com/SEU_USUARIO/NOME_DO_REPO.git
    cd NOME_DO_REPO
    ```

2.  **Instale as dependências:**
    ```bash
    pip install -r requirements.txt
    ```

3.  **Execute a aplicação:**
    ```bash
    streamlit run dashboard.py
    ```

## ☁️ Deploy no Streamlit Cloud

Para que a funcionalidade de **salvar dados no GitHub** funcione online, você precisa configurar as credenciais nos "Secrets" do Streamlit Cloud.

1.  Faça o deploy do app no [share.streamlit.io](https://share.streamlit.io/).
2.  Nas configurações do App, vá em **Settings** > **Secrets**.
3.  Adicione o seguinte conteúdo (ajuste com seus dados):

```toml
[github]
token = "ghp_SEU_TOKEN_PESSOAL_DO_GITHUB"
repo = "SEU_USUARIO/NOME_DO_REPO"
branch = "main"
file_path = "dados/dados.csv"
```


**Desenvolvido por:** Clayton S. Silva
**Desenvolvido por:** Clayton S. Silva
