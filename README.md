# Análise de Emoções e Busca Textual em Avaliações de Assistentes de IA Generativa

Projeto acadêmico de Processamento de Linguagem Natural (PLN) voltado
à análise de emoções e à busca textual em avaliações de dez assistentes
de IA generativa populares na Google Play.

## Objetivo

Construir e preparar um corpus de avaliações em português, identificar
evidências de emoções por técnicas tradicionais de PLN e recuperar
comentários relacionados a assuntos de interesse.

As estrelas serão utilizadas como informações complementares para
filtros e comparações. Elas não serão utilizadas para determinar as
emoções presentes nos textos.

## Corpus

Foram coletadas 5.000 avaliações, distribuídas entre os aplicativos:

- ChatGPT
- Google Gemini
- Grok
- Meta AI
- Perplexity
- Nova
- Dola
- Claude
- DeepSeek
- Luzia

A seleção dos aplicativos foi intencional, sem pretensão de representar
um ranking dos dez mais baixados.

A coleta foi realizada com `google-play-scraper==1.2.7`, uma biblioteca
não oficial, utilizando:

- Idioma: português (`lang="pt"`).
- Região: Brasil (`country="br"`).
- Ordenação: avaliações mais recentes primeiro.
- Quantidade: 100 avaliações por nota, de 1 a 5, para cada aplicativo.

Os dados foram armazenados em 50 arquivos JSON, separados por
aplicativo e nota. Os textos foram preservados conforme retornados
pela biblioteca. Nomes e fotos dos usuários não foram armazenados.

## Trabalho 1 — PLN tradicional

Etapas planejadas:

- Consolidação e análise exploratória do corpus.
- Limpeza, normalização e tokenização dos textos.
- Tratamento de stopwords e experimentos com stemming.
- Representação textual com TF-IDF e busca por similaridade.
- Análise de emoções baseada em léxico.
- Avaliação com amostras revisadas manualmente, métricas,
  abordagens de referência e análise de erros.
- Produção de pelo menos quatro visualizações relevantes.

O léxico e as categorias emocionais ainda serão definidos.
Uma avaliação poderá apresentar evidências de múltiplas emoções.
A ausência de correspondências no léxico não será interpretada
automaticamente como neutralidade emocional.

## Trabalho 2 — Componente contemporâneo

A aplicação será ampliada com um recurso de IA generativa para
produzir sínteses dos comentários recuperados pela busca textual,
apresentando referências às avaliações utilizadas.

## Organização

- `notebooks/`: notebooks das etapas do projeto.
- `data/raw/`: dados brutos preservados, sem edição manual.
- `data/interim/`: dados consolidados e transformações intermediárias.
- `data/processed/`: dados preparados para os métodos de análise.

## Ambiente de execução

O desenvolvimento é realizado em Python, utilizando Google Colab,
com versionamento local por Git.

O notebook de coleta utiliza atualmente o Google Drive para armazenar
os dados. A execução local exige a adaptação dos caminhos e das células
específicas do Colab.

O arquivo de dependências e as instruções completas de reprodução
serão adicionados conforme as próximas etapas forem implementadas.

## Limitações

- A amostragem equilibrada por estrelas não representa a distribuição
  natural das avaliações nem garante equilíbrio entre emoções.
- As avaliações representam os autores dos comentários coletados,
  não todos os usuários dos aplicativos.
- Novas coletas podem retornar resultados diferentes.
- Textos curtos, ironia, negação, erros ortográficos e emoções mistas
  podem dificultar a análise.
- Evidências obtidas por léxico não equivalem a rótulos humanos.
- Os resultados dependem da cobertura e da adequação do léxico escolhido.

