(Não modificamos o modelo lógico)

Utilizando as técnicas de análise de redes e com base no grafo e as perguntas do laboratório 7, elaboramos as seguintes respostas:

Quais os subgrupos mais consumidos em peso?
  Utilizando o conceito de betweness em centralidade, podemos encontrar o subgrupo mais consumido, uma vez que quando uma receita é realizada, ela passa por seus ingrediente e por seus respectivos subgrupos, 
então o subgrupo mais consumido será aquele que mais caminhos percorram por ele.

Grupos que tem maiores INTAKE_BW_AVG?
  Tratando o INTAKE-BW-AVG como a importância de cada vértice de ingrediente, é possível resolver essa pergunta por meio de eigenvector centrality, já que os grupos os quais esses ingredientes recebem esta importância
fazendo assim, com que os grupos com mais importância sejam aqueles com maiores INTAKE-BW-AVG.

Média de ingredientes por receita?
  Ao fazer uma análise dos grupos formados pelas receitas e seus ingredientes, podemos utilizar o conceito de modularidade, mas ao invés de comparar com casos aleatórios, comparamos com um caso que mostre a média
de ingredientes por receita e, assim é possível determinarmos o quão distantes estão as receitas da média de ingredientes.
