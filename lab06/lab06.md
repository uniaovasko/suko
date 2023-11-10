## Exercício

Faça a projeção em relação a Patologia, ou seja, conecte patologias que são tratadas pela mesma droga.

### Resolução
~~~cypher
MATCH (p1:Pathology)<-[a]-(d:Drug)-[b]->(p2:Pathology)
MERGE (p1)<-[r:Relates]->(p2)
ON CREATE SET r.weight=1
ON MATCH SET r.weight=r.weight+1

~~~


## Exercício

Construa um grafo ligando os medicamentos aos efeitos colaterais (com pesos associados) a partir dos registros das pessoas, ou seja, se uma pessoa usa um medicamento e ela teve um efeito colateral, o medicamento deve ser ligado ao efeito colateral.

### Resolução
~~~cypher
"Os casos em que uma mesma pessoa toma um mesmo remédio para patologias diferentes
são contabilizados individualmente"

LOAD CSV WITH HEADERS FROM 'https://raw.githubusercontent.com/santanche/lab2learn/master/data/faers-2017/drug-use.csv' AS line
CREATE (:Treat {idperson: line.idperson, codepathology:line.codepathology, codedrug:line.codedrug})

LOAD CSV WITH HEADERS FROM 'https://raw.githubusercontent.com/santanche/lab2learn/master/data/faers-2017/sideeffect.csv' AS line
CREATE (:Caus {idperson: line.idPerson, codepathology:line.codePathology})

MATCH (t:Treat)
MERGE (d:Drug {codedrug: t.codedrug})

MATCH (c:Caus)
MERGE (s:Side {codepathology:c.codepathology})

MATCH (t:Treat)
MATCH (c:Caus)
MATCH (d:Drug)
MATCH (s:Side)
WHERE t.idperson=c.idperson AND t.codedrug=d.codedrug AND c.codepathology=s.codepathlogy
MERGE (d)-[i:Infli]->(s)
ON CREATE SET i.weight=1
ON MATCH SET i.weight=i.weight+1

~~~

## Exercício

Que tipo de análise interessante pode ser feita com esse grafo?

Proponha um tipo de análise e escreva uma sentença em Cypher que realize a análise.

### Resolução
~~~cypher
"Número de nós criados é o número de vezes em que algum efeito colateral foi
causado por mais de uma vez pela mesma droga"
MATCH (d:Drug)-[i:Infli]->(s:Side)
WHERE i.weight > 1
CREATE (:MutlCaus)


"Número de nós criados é o número de vezes em que algum efeito colateral foi
causado somente uma vez por uma mesma droga"
MATCH (d:Drug)-[i:Infli]->(s:Side)
WHERE i.weight = 1
CREATE (:SinglCaus)

~~~
