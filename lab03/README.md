# Equipe `uniaovasko`

# Subgrupo `B`
* `Henrique Marques de Martim` - `248333`
* `Leandro Henrique Silva Resende` - `213437`
* `Matheus Mantovani Meneghel` - `230906`

## Modelo Conceitual ER Revisado

> Coloque aqui o diagrama entidade-relacionamento original ou revisado para transformação em modelo relacional. O diagrama deve atributos, cardinalidade e entidades fracas.
>
> Indique abaixo do diagrama (como no exemplo), se é o original ou o revisado.
>
> Não é necessário colocar o diagrama UML revisado.

<img src="images/ER_Diagram_MMORPG.png" width="400px" height="auto">

*Diagrama ER Original*

## Mapeamento para o Modelo Relacional

> Coloque aqui o modelo relacional que mapeia o modelo ER (original ou revisado). Nesse modelo deve constar o esquema das relações, com as chaves primárias e estrangeiras. A especificação de tipos de atributos é opcional.

> Exemplo de modelo lógico relacional
~~~
PESSOA(_Código_, Nome, Telefone)
ARMÁRIO(_Código_, Tamanho, Ocupante)
  Ocupante chave estrangeira -> PESSOA(Código)
~~~
