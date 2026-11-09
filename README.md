# Brasileirão: comparação entre 2024 e 2025

Projeto da disciplina Introdução à Ciência de Dados, com coleta por web scraping das classificações do Campeonato Brasileiro na ESPN.

Escolhi esse tema porque gosto muito de futebol e queria comparar o desempenho dos clubes nas duas temporadas usando pontos, gols e aproveitamento.

## Dados e método

Os dados foram coletados em 09/11/2026 nas páginas da ESPN:

- [Classificação de 2024](https://www.espn.com.br/futebol/classificacao/_/liga/bra.1/temporada/2024)
- [Classificação de 2025](https://www.espn.com.br/futebol/classificacao/_/liga/bra.1/temporada/2025)

Usei BeautifulSoup para extrair as tabelas e pandas para organizar e limpar os dados. Conferi tipos, valores ausentes, duplicatas e a consistência dos pontos e gols. Depois calculei o aproveitamento e a média de gols por jogo e gerei gráficos com matplotlib.

O dataset final tem 40 registros e 13 colunas, com uma linha por clube e temporada. A comparação da variação de pontos considera apenas os 16 clubes presentes nos dois anos.

## Arquivos

- `Template_Documentacao.ipynb`: código, documentação, tabelas, gráficos e conclusões.
- `brasileirao_2024_2025.csv`: dataset tratado.
- `requirements.txt`: dependências para executar o notebook.

O dicionário das colunas está na seção "Dataset final" do notebook.

## Como executar

Com Python 3.10 ou superior instalado, abra um terminal na pasta do projeto e execute:

```bash
python -m venv .venv
```

Ative o ambiente no Linux/macOS:

```bash
source .venv/bin/activate
```

Ou no Windows (Prompt de Comando):

```bat
.venv\Scripts\activate.bat
```

Instale as dependências e abra o Jupyter:

```bash
python -m pip install -r requirements.txt
jupyter notebook
```

Abra "Template_Documentacao.ipynb" e execute as células na ordem. A coleta precisa de acesso à internet e às páginas da ESPN. A execução gera o CSV na pasta do notebook, substituindo a versão existente.

As saídas já estão salvas no notebook para consultar os resultados sem repetir a coleta. Para ler o CSV separadamente:

```python
import pandas as pd

df = pd.read_csv("brasileirao_2024_2025.csv")
print(df.head())
```

## Principais resultados

- O Flamengo terminou 2025 com 79 pontos e aproveitamento de 69,30%.
- Entre os clubes presentes nas duas temporadas, o Fluminense teve a maior melhora, com 18 pontos a mais. O Fortaleza teve a maior queda, com 25 pontos a menos.
- O Flamengo marcou 78 gols em 2025, média de 2,05 por jogo.

## Limitações

A análise usa apenas duas temporadas e os totais finais dos clubes. Ela não explica as causas das mudanças de desempenho. Alterações no HTML da ESPN podem exigir ajustes no código de coleta.
