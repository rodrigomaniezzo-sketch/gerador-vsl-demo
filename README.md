# Gerador de página de vendas e quiz a partir de uma VSL — demonstração técnica

Uma carta de vendas (VSL) entra. Uma **análise estruturada única** sai. Dela nascem
uma **página de vendas long-form** e um **quiz interativo** — coerentes entre si por
construção, porque leem do mesmo JSON.

**Demonstração ao vivo:** https://rodrigomaniezzo-sketch.github.io/gerador-vsl-demo/

## O que foi medido

Cinco cartas de venda de nichos diferentes, de 2.130 a 8.699 palavras, pelo mesmo pipeline.

| | |
|---|---|
| Tempo da VSL aos dois arquivos | **45 s** (modelo econômico) |
| Custo por geração completa | **US$ 0,07** econômico · US$ 0,33–0,42 no modelo completo |
| Conteúdo da análise que chegou à página | íntegro nas 5 (dores, desejos, benefícios, inclusos, bônus, objeções) |
| Dependências externas | **zero** — tipografia embutida, ícones em SVG inline |

## O modo de falha encontrado

Na carta de 8.699 palavras havia oito valores diferentes no texto (preço, bônus,
ancoragens). A extração não conseguiu decidir qual era *o* preço e devolveu `null`.

A página saiu completa e **sem dizer quanto custa** — chega a escrever "antes do preço,
um ponto importante" e nunca informa o valor. **A falha é silenciosa.**

Um gerador em produção precisa de validação de campos obrigatórios, avisando quando a
fonte for ambígua.

## Aviso

O produto "Destrave" e sua oferta são **fictícios**, criados para este teste. Nenhum
pagamento é processado.

As outras quatro cartas usadas na medição são páginas de vendas reais e públicas.
Serviram apenas como entrada — os resultados não são publicados aqui, porque a copy
é de seus autores.

## Créditos de tipografia

Anton e Inter, ambas sob SIL Open Font License 1.1, embutidas nos arquivos.
