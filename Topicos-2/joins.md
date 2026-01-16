# JOINS 


1. join() - JOIN SQL raiz

Usado quando:

. Você precisa filtrar, ordenar ou agrupar usando dados de outra tabela
. Você quer controle total da query

exemplo:

stmt = (
    select(User)
    .join(User.orders)
    .where(Order.status == "PAID")
)

Gera algo tipo:

SELECT user.*
FROM user
JOIN order ON order.user_id = user.id
WHERE order.status = 'PAID'

Importante:

. join() NÃO carrega o relacionamento automaticamente no ORM
. Se acessar o user.orders, pode disparar outra query

#resumo: join() é para filtrar, não para carregar relacionamento


2. outerjoin() - JOIN, só que sem perder registros

Mesmo esquema do join(), mas é LEFT OUTER JOIN

Usado quando:

. Você quer manter registros mesmo sem relacionamento
. Ex. usuários sem pedidos 

stmt = (
    select(User)
    .outerjoin(User.orders)
)

Resumo:

. join() → perde quem não tem relação
. outerjoin() → mantém todo mundo


3. joinedload() - Carregar relacionamento via JOIN (eager load)

joinedload() não é para filtrar, é para evitar N+1

stmt = (
    select(User)
    .options(joinedload(User.orders))
)

O ORM faz um LEFT OUTER JOIN por baixo e preenche user.orders na memória, resultado:

. 1 query
. Sem N+1
. Relacionamento já carregado
. Se for one-to-many, duplica linhas
. Pode ficar pesado em tabelas grandes

Resumo:
. joinedload() = rápido, mas pode virar um monstro


4. selectinload() - O campeão no mundo real

2 queries, zero dor de cabeça

stmt = (
    select(User)
    .options(selectinload(User.orders))
)

O que acontece:

. Busca usuários
. Busca pedidos com WHERE user_id IN (...)

Exemplo SQL:

SELECT * FROM user;
SELECT * FROM order WHERE user_id IN (1, 2, 3);

Vantagens:

. Sem duplicação
. Escala melhor
. ORM-friendly
. Menos chance de cagada
