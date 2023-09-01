# Equipe `uniaovasko`

# Subgrupo `B`
* `Henrique Marques de Martim` - `248333`
* `Leandro Henrique Silva Resende` - `213437`
* `Matheus Mantovani Meneghel` - `230906`

## Modelo Conceitual ER Original

<img src="images/ER_lab03.png" width="400px" height="auto">

*Diagrama ER Original*

## Mapeamento para o Modelo Relacional

~~~
ALUNO(_idAluno_, nutrientesConsumidos, numRefeicoes, idRefeicao)
  idRefeicao chave estrangeira -> REFEICAO(idRefeicao)
CARDAPIO(_tipo_, _data_, _horario_, _idPorcao_, valoresNutricionais)
  idPorcao chave estrangeira -> PORCOES(idPorcao)
PORCOES(_idPorcao_, _ingrediente_, valoresNutricionais, nome, rankingPopularidade)
  ingrediente chave estrangeira -> INGREDIENTE(nome)
INGREDIENTE(_nome_, valorNutricional, tipo)
  /*Ingredientes compostos por outros ingredientes serao tratados como porcoes*/
REFEICAO(_idRefeicao_, _porcao_)
  porcao chave estrangeira -> PORCOES(idPorcao)
~~~
