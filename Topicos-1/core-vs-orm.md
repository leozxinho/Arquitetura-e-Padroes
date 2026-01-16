# Core vs ORM

# Core (SQL “na veia”)

Core é você falando diretamente com o banco. SQL puro ou quase isso.

. Queries escritas por você
. Controle total do que o banco executa
. Pouca ou nenhuma abstração

Vantagens:

. Performance máxima
. Controle absoluto
. Fácil entender o que realmente acontece

Desvantagens:

. Mais código repetido
. Você precisa saber SQL de verdade
. Mudou o banco? Pode doer

Use Core quando:

. Queries complexas (JOIN pesado, subqueries, CTE, window functions)
. Performance é crítica
. Relatórios, dashboards, jobs de dados


# ORM (Object-Relational Mapping)

ORM é o banco fingindo ser objeto. Você pensa em classes, não em tabelas.

O que é:

. Mapeia tabelas → objetos
. CRUD com uma linha
. Relacionamentos automáticos

Vantagens:

. Produtividade absurda
. Código mais legível
. Menos boilerplate

Desvantagens (as traiçoeiras):

. Performance imprevisível
. Queries invisíveis (N+1 é o capeta)
. Abstração que esconde o custo real

Use ORM quando:

. CRUD simples
. MVP, startup, produto em evolução
. Time júnior ou prazo curto
. Regras de negócio, não engenharia de banco

👉 Verdade dura: ORM te deixa rápido… até te deixar lento.