# Corpus de Avaliações de Assistentes de IA Generativa

Projeto acadêmico de Processamento de Linguagem Natural (PLN) para
construção e preparação de um corpus de avaliações da Google Play,
destinado à futura análise de sentimentos e emoções.

## Corpus

O corpus contém 5.000 avaliações de dez aplicativos: ChatGPT, Google
Gemini, Grok, Meta AI, Perplexity, Nova, Dola, Claude, DeepSeek e Luzia.

Foram coletadas 100 avaliações por nota, de 1 a 5 estrelas, para cada
aplicativo, utilizando a biblioteca não oficial `google-play-scraper`,
com os parâmetros `lang="pt"`, `country="br"` e ordenação por relevância.

Os registros foram preservados em 50 arquivos JSON. Nomes e fotos
dos usuários não foram armazenados. A seleção dos aplicativos não
representa um ranking de downloads.

## Trabalho 1 — Construção e preparação do corpus

Etapas realizadas:

- Coleta e conferência da integridade dos registros.
- Consolidação das avaliações em CSV.
- Limpeza de espaços e conversão para minúsculas.
- Tokenização e lematização com spaCy.
- Salvamento de duas versões: com tokens e com lemas.
- Análise descritiva apresentada em quatro tabelas.
- Elaboração do relatório técnico.

Os textos originais foram preservados. Não foram removidos acentos,
pontuação, emojis ou stopwords, e não foi aplicado stemming.

## Trabalho 2 — Análise de sentimentos e emoções

A próxima etapa utilizará o corpus preparado para análise de sentimentos
e emoções, com avaliação dos métodos e integração de um componente
contemporâneo de PLN.

As estrelas serão utilizadas como metadados, não como rótulos de emoções.

## Organização

- `notebooks/01_coleta.ipynb`: coleta e conferência dos dados.
- `notebooks/02_preparacao.ipynb`: preparação e análise descritiva.
- `data/raw/`: arquivos brutos da coleta.
- `data/interim/`: CSV consolidado.
- `data/processed/`: versões preparadas com tokens e com lemas.
- `requirements.txt`: dependências Python.

## Execução

Os notebooks estão configurados para Google Colab e Google Drive.

1. Disponibilize a pasta `pln_trabalho` no Drive, mantendo a estrutura
   de dados do projeto.
2. Abra o notebook desejado no Colab e autorize a conexão com o Drive.
3. Confira o caminho `/content/drive/MyDrive/pln_trabalho`.
4. Execute as células na ordem, incluindo as instalações necessárias.

Com os arquivos brutos disponíveis, não é necessário repetir a coleta:
execute diretamente `02_preparacao.ipynb`.

A execução local exige adaptar os caminhos e remover as células de
conexão com o Colab/Drive. O ambiente registrado utiliza Python 3.13.15,
pandas 2.2.3, spaCy 3.8.16 e o modelo `pt_core_news_sm` 3.8.0.

## Limitações

- A seleção por relevância e as cotas por nota não representam a
  distribuição natural das avaliações.
- Os parâmetros de idioma e país não garantem textos exclusivamente
  em português brasileiro.
- Novas coletas podem retornar registros diferentes.
- A tokenização pode separar emojis compostos, e a lematização pode
  produzir formas incorretas.
- O corpus ainda não possui rótulos de emoções.