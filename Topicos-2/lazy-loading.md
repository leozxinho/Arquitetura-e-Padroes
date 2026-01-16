# Lazy loading


Lazy Loading define quando e como o ORM vai buscar os relacionamentos 

1. Select (lazy padrão)

Carrega sob demanda, quando você acessa.

Como funciona:

. 1 query para os objetos principais
. +1 query por acesso ao relacionamento

Problema:

. Fácil de cair no N+1
. Em loop grande=desastre

Quando usar:

. Relacionamento raramente acessado
. Uso pontual, fora de loops

obs: É confortável, mas preigoso. Igual cartão de crédito sem limite



2. Joined (joined loading)

Faz JOIN e traz tudo de uma vez

Como funciona:

. Uma única query com JOIN
. ORM monta os objetos em memória

Vantagens:

. Evita N+1
. 1 round-trio ao banco


Problemas:

. Pode gerar linhas duplicadas
. Query pesada se tiver muitos relacionamentos


Quando uaar?

. Relacionamento sempre necessário
. Cardinalidade sempre necessário



3.  subquery (subquery loading)

Duas queries bem organizadas

Como funciona?

. Query principal
. Segunda query com WHERE IN (...)

Vantagens:

. Evita N+1
. Não duplica linhas como JOIN
. Mais previsível que joined

Problemas:

. Duas queries (não é mágica)
. Pode ficar pesado com listas gigantes

Quando usar:

. One-to-Many grande
. Quando JOIN explode linhas