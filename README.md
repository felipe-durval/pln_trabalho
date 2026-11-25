# Análise de Polaridade e Emoções em Avaliações de Assistentes de IA

Projeto acadêmico de Processamento de Linguagem Natural (PLN) do IFSP São Carlos, desenvolvido em Python com Google Colab.

## Objetivo

Analisar a polaridade e as associações emocionais presentes em avaliações de aplicativos de IA generativa, utilizando um léxico e regras de processamento textual. Na etapa final, utilizar um modelo de linguagem para sintetizar uma seleção de comentários.

As estrelas são utilizadas apenas para comparações e filtros, sem determinar a polaridade ou as emoções dos textos.

## Corpus

O corpus contém 5.000 avaliações de dez aplicativos:

ChatGPT, Google Gemini, Grok, Meta AI, Perplexity, Nova, Dola, Claude, DeepSeek e Luzia.

A coleta utilizou a biblioteca não oficial `google-play-scraper==1.2.7`, com:

- Idioma português e região Brasil.
- Ordenação pelas avaliações mais relevantes.
- 100 avaliações por nota, de 1 a 5, para cada aplicativo.

Os dados brutos foram preservados em 50 arquivos JSON. Nomes e fotos dos autores não foram armazenados.

A escolha dos aplicativos foi intencional e não representa um ranking dos mais baixados.

## Trabalho 1 — Construção e preparação do corpus

- Coleta, conferência e consolidação dos dados.
- Limpeza de espaços excedentes e normalização para minúsculas.
- Tokenização com spaCy.
- Preservação de acentos, pontuação, emojis e stopwords.
- Geração de uma versão alternativa com lemas.
- Análise descritiva do corpus.

Não foi aplicado stemming. A versão lematizada foi preservada, mas não utilizada na análise do Trabalho 2.

## Trabalho 2 — Análise e síntese das avaliações

A análise utiliza o NRC EmoLex em português e um léxico complementar com 70 entradas voltadas ao contexto dos aplicativos.

São contabilizadas associações positivas, negativas e oito emoções:

- Alegria.
- Tristeza.
- Raiva.
- Medo.
- Nojo.
- Confiança.
- Antecipação.
- Surpresa.

Cada avaliação recebe uma classificação de polaridade, contagens emocionais e indicação das emoções predominantes, preservando empates.

Uma regra de negação desconsidera associações de termos próximos a palavras como “não”, “nunca” e “jamais”. A regra não inverte automaticamente as emoções.

O notebook apresenta exemplos individuais, evidências encontradas, tabelas de resultados e comparação entre polaridade lexical e estrelas.

Na etapa final, o modelo `Qwen/Qwen2.5-1.5B-Instruct` produz uma síntese de comentários selecionados. O modelo complementa a análise tradicional.

## Resultados

Nas 5.000 avaliações, a análise lexical produziu:

| Polaridade | Avaliações |
| --- | ---: |
| Positiva | 2.249 |
| Negativa | 1.904 |
| Sem predominância — empate | 686 |
| Sem evidência lexical de polaridade | 161 |

Uma avaliação pode apresentar múltiplas associações emocionais. A ausência de correspondências no léxico não significa neutralidade.

## Organização

- `notebooks/`: coleta, preparação e análise.
- `data/raw/`: arquivos brutos da coleta.
- `data/interim/`: dados consolidados e etapas intermediárias.
- `data/processed/`: dados preparados, resultados da análise e síntese.
- `data/lexico/`: léxico emocional e complemento do projeto.
- `requirements.txt`: dependências.
- `relatorio_tecnico_trabalho_2.pdf`: métodos, resultados e limitações.

## Execução

1. Baixe ou clone o repositório.
2. Disponibilize os arquivos do projeto no Google Drive.
3. Abra o notebook desejado no Google Colab.
4. Ajuste o caminho da pasta do projeto na célula de configuração.
5. Instale as dependências e execute as células em ordem.

Para executar apenas a análise, utilize o notebook
`notebooks/03_analise_emocoes.ipynb`, com os arquivos:

- `data/processed/avaliacoes_preparadas.json`
- `data/lexico/Portuguese-NRC-EmoLex.txt`
- `data/lexico/lexico_complementar.csv`

O arquivo original do EmoLex deve ser obtido conforme as instruções e condições de uso disponibilizadas por seus autores.

O componente generativo requer acesso à internet para baixar o modelo. Pode utilizar GPU, quando disponível, ou CPU, com execução mais lenta.

A execução local exige adaptar os caminhos e remover as células específicas de montagem do Google Drive.

## Limitações

- A seleção por relevância e o equilíbrio por estrelas não representam a distribuição natural das avaliações.
- Os parâmetros de idioma e região não garantem que todos os textos estejam em português.
- As associações do léxico dependem da tradução e do contexto das palavras.
- A regra de negação é aproximada e não resolve ironia, sarcasmo ou interpretações complexas.
- O léxico complementar não foi validado em uma amostra independente.
- Não houve avaliação quantitativa com rótulos humanos nem comparação com baseline.
- A síntese generativa pode omitir informações ou produzir afirmações sem apoio nos comentários.

Os resultados são exploratórios. As contagens representam associações lexicais, e não emoções confirmadas por avaliação humana.