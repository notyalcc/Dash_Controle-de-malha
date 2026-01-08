# 🚚 Dashboard de Controle de Malha Logística

Este é um painel interativo desenvolvido em **Python** e **Streamlit** para monitoramento de performance logística. O foco principal é a análise comparativa entre veículos **Liberados** (fluxo normal) e veículos retidos em **Malha Fina** (auditoria), permitindo identificar gargalos e avaliar o desempenho de transportadoras.

---

## 📋 Funcionalidades

### 📊 Visualização de Dados
- **KPIs em Tempo Real:** Fluxo total, veículos liberados, retidos e taxa de retenção global (com comparativo vs. período anterior).
- **Rankings:** Top transportadoras por volume e por retenção.
- **Análises Temporais:** Visões diária, semanal, mensal e anual.
- **Mapas de Calor:** Identificação de dias da semana com maior risco de retenção.
- **Funil do Processo:** Visualização da proporção entre portaria, liberação e malha.

### 🛠️ Gestão de Dados (CRUD)
- **Importação:** Suporte para arquivos `.csv`, `.xlsx` (Excel) e `.db` (SQLite).
- **Edição Manual:** Interface estilo planilha para adicionar, editar ou excluir registros diretamente no banco de dados.
- **Persistência:** Os dados são salvos automaticamente em um banco de dados local (`dados.db`).
- **Exportação:** Download de relatórios filtrados em Excel (`.xlsx`) e backup do banco de dados.

### 🔒 Segurança
- **Login de Administrador:** Acesso restrito para edição e filtros avançados (Senha padrão: `admin123`).
- **Modo Leitura:** Usuários sem senha podem visualizar os dados, mas não podem editar.

---

## 🚀 Como Rodar o Projeto (Desenvolvimento)

### Pré-requisitos
- Python 3.9 ou superior instalado.

### 1. Instalação das Dependências
Abra o terminal na pasta do projeto e execute:

```bash
pip install -r requirements.txt
```

*Conteúdo do `requirements.txt`:*
```text
streamlit
pandas
plotly
sqlalchemy
openpyxl
pyinstaller
```

### 2. Executando o Dashboard
Para rodar a aplicação no navegador:

```bash
streamlit run dashboard.py
```

---

## 📦 Gerando o Executável (.exe)

Para distribuir o dashboard para usuários que não têm Python instalado, utilizamos o **PyInstaller**.

### Passo a Passo

1. Certifique-se de que o arquivo `run.py` (script de inicialização) e `logo.png` estão na pasta raiz.
2. Feche qualquer instância do dashboard que esteja rodando.
3. Execute o seguinte comando no terminal:

```powershell
pyinstaller --noconfirm --onefile --windowed --name "DashboardLogistica" --collect-all streamlit --collect-all plotly --collect-all pandas --collect-all altair --hidden-import sqlalchemy.sql.default_comparator --hidden-import openpyxl --copy-metadata typing_extensions --add-data "dashboard.py;." --add-data "logo.png;." run.py
```

### Onde encontrar o executável?
Após o término do processo (pode levar cerca de 3 a 5 minutos), o arquivo **`DashboardLogistica.exe`** estará disponível na pasta **`dist/`**.

> **Nota:** Ao distribuir o executável, o arquivo de banco de dados `dados.db` será criado automaticamente na mesma pasta onde o `.exe` estiver localizado.

---

## ☁️ Deploy Online (Streamlit Cloud)

Você pode hospedar este dashboard gratuitamente no Streamlit Cloud usando o GitHub.

### ⚠️ Aviso sobre Persistência de Dados
No ambiente de nuvem (Streamlit Cloud), o arquivo `dados.db` é **reiniciado** sempre que o app "dorme" ou reinicia. Portanto, as edições feitas via dashboard **não ficarão salvas permanentemente** na versão online (diferente da versão `.exe` local, onde tudo fica salvo).

### Passo a Passo para Deploy
1. Crie uma conta no GitHub e um novo repositório.
2. Faça o upload dos arquivos: `dashboard.py`, `requirements.txt`, `logo.png` e `dados.db` (se quiser que ele já inicie com dados).
   * *Dica: Não é necessário subir a pasta `dist`, `build` ou o `.exe`.*
3. Crie uma conta no Streamlit Cloud.
4. Clique em **"New app"**, selecione seu repositório do GitHub e o arquivo `dashboard.py`.
5. Clique em **Deploy**.

---

## 📂 Estrutura do Projeto

```
Dashboard-controle-de-malha/
│
├── dashboard.py        # Código principal da aplicação Streamlit
├── run.py              # Script "wrapper" para inicializar o Streamlit dentro do .exe
├── requirements.txt    # Lista de bibliotecas necessárias
├── logo.png            # Logotipo da empresa (opcional)
├── dados.db            # Banco de dados SQLite (gerado automaticamente)
│
├── dist/               # Pasta onde o .exe final é gerado
└── build/              # Arquivos temporários de compilação (pode ser ignorado)
```

---

## ℹ️ Como Usar

1. **Login:** Na barra lateral esquerda, digite a senha `admin123` para liberar as ferramentas de edição.
2. **Importar Dados:** Use o botão "Carregar arquivo" para subir planilhas históricas.
3. **Editar:** Vá até o final da página, expanda a seção "Ver Dados Detalhados / Editar", faça as alterações na tabela e clique em **"💾 Salvar Alterações"**.
4. **Filtros:** Utilize os filtros laterais (Data, Transportadora, Operação) para refinar os gráficos.

---

**Desenvolvido por:** Clayton S. Silva