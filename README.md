# Dashboard de vendas Porsche

Projeto do curso **Criando Agentes de Tratamento de Dados** (DIO). A base tem 100 vendas, com cada campo em duas versões: o dado cru e o sanitizado. A dashboard usa a versão sanitizada e responde perguntas de negócio em um HTML de arquivo único, com os dados embutidos. Os filtros recortam todos os gráficos ao mesmo tempo, e clicar em uma barra aplica o filtro correspondente.

**Endereço publicado:** `https://SEU-USUARIO.github.io/nome-do-repositorio/`
**Prints:** `docs/print-dashboard.png` (tela inicial) e `docs/print-filtro-taycan.png` (filtro de exemplo aplicado)

## Perguntas de negócio escolhidas e por quê

Escolhi três perguntas principais. Cada uma leva a uma decisão concreta, e por isso valem mais que um monte de gráficos soltos.

1. **Qual família de modelos gera mais receita?** Mostra onde está o dinheiro (911, 718, Cayenne, Macan, Panamera, Taycan) e ajuda a decidir o que priorizar em estoque. O ticket médio por família, logo abaixo, separa volume de valor.
2. **Como os clientes pagam?** A base tinha 13 grafias de pagamento. Agrupadas, mostram se a venda depende de financiamento, transferência ou dinheiro, o que muda a operação financeira.
3. **Em quais estados as vendas se concentram?** Mostra onde estão os clientes e onde vale reforçar a operação.

### Análises complementares

Depois das três principais, acrescentei seis blocos que aprofundam as respostas:

- **Receita por ano do modelo:** quais safras concentram o faturamento.
- **Modelos que mais faturam:** top 8 por receita (ex.: 911 Dakar).
- **Cidades que mais faturam:** top 8, complementando a visão por estado.
- **Faixas de preço:** cinco faixas, de "até 75 mil" a "acima de 200 mil".
- **Família × pagamento:** matriz em mapa de calor.
- **10 maiores vendas:** tabela com modelo, ano, cidade, pagamento e preço.

## Filtros e indicadores

- Filtros: família, ano do modelo, estado e forma de pagamento (pela lista ou clicando nas barras).
- Indicadores de topo: vendas, receita, ticket médio, maior venda, estados e cidades.
- Cada gráfico tem uma frase de insight que se recalcula conforme o filtro.
- Tema claro e escuro automáticos, conforme o sistema do visitante.

## Tratamento da base antes da IA

- Fiquei só com as colunas sanitizadas (modelo, ano, preço, pagamento, cidade, estado), coladas como valores.
- Ano e preço convertidos em número.
- 13 preços vinham abaixo de 1.000 (ex.: 121). Interpretei como milhares de dólares (US$ 121.000). **Premissa a validar na base crua.**
- 2 preços `INVALID` ficam fora de receita, ticket médio, faixas de preço e ranking de maiores vendas. As vendas continuam na contagem.
- Pagamentos equivalentes agrupados: Wire Transfer, Wiretransfer, Bank Transfer e ACH em Transferência; Financing e Financing Plan em Financiamento; Lease e Lease Plan em Leasing; Credit Card e Credit Card Payment em Cartão de crédito.
- 24 datas estavam `INVALID` e algumas caíam em 2027. Por isso o filtro de tempo usa o **ano do modelo**, não a data da venda.
- **Dados sensíveis:** como a base vai embutida no HTML, nomes de clientes e vendedores ficaram de fora. Nenhum dado pessoal entrou na dashboard.

## Prompt e evolução

**Prompt inicial (resumo):**

> Crie uma dashboard em HTML de arquivo único com os dados embutidos. Responder três perguntas: receita por família de modelo, formas de pagamento e concentração por estado. Filtros por família, ano do modelo, estado e pagamento. Indicadores de topo: vendas, receita e ticket médio. Visual inspirado na Porsche: grafite, off-white e vermelho como destaque, fonte condensada.

**Refinamento (resumo):**

> Use o HTML e o README atuais para aumentar a quantidade de gráficos, desenvolver e aperfeiçoar as informações e deixar tudo preparado para o GitHub.

**O que mudou até a versão final:**

- Troquei cidade por estado no filtro, porque estado tem menos categorias.
- Adicionei uma frase de insight acima de cada gráfico.
- Passei de 3 para 9 análises, com ticket médio por família, ano do modelo, modelos, cidades, faixas de preço, matriz de pagamento e maiores vendas.
- Passei de 3 para 6 indicadores de topo e incluí o filtro por clique nas barras.

_(Acrescente aqui as suas próprias iterações, se tiver feito outras.)_

## Ferramenta usada

Claude (arquivo HTML gerado a partir da planilha). _Se você também fez o outro caminho do curso (ChatGPT com Canvas ou agente com skill), diga aqui qual usou, o que comparou e por que ficou com esta versão._

## Como publicar no GitHub Pages

1. Crie um repositório público na sua conta, com nome em minúsculas e sem acento (ex.: `dashboard-vendas-porsche`).
2. Envie `index.html`, `README.md` e a pasta `docs/` com os prints.
3. Em **Settings > Pages**, escolha **Deploy from a branch**, branch `main`, pasta `/ (root)`.
4. Aguarde cerca de um minuto e copie o endereço gerado para o topo deste README.
5. Na entrega, envie o link do **repositório**, não o da dashboard.

## Arquivos

- `index.html`: a dashboard
- `README.md`: este arquivo
- `docs/print-dashboard.png`: tela inicial
- `docs/print-filtro-taycan.png`: exemplo de filtro aplicado
