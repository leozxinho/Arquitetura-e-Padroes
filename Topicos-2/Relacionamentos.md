# Relacionamentos 

One-to-Many (1 → N)

Um registro se relacionado com vários outros

Ex.

Usuário → Pedidos

. Um usuário pode ter vários pedidos
. Um pedido pertence a um único usuário

Banco de dados (ideia mental):

. A chave estrangeira fica do lado "many"
. pedido.user_id → usuario.id

Conclusão: Um usuário manda, vários pedidos obedecem.




Many-to-One (N → 1)

É o mesmo comportamento do One-to-Many, só visto do outro lado.

Ex.

Pedido → Usário

. Muitos pedidos → um usuário
. Não muda nada no banco
. Só muda como você olha




Many-to-Many (N ↔ N)

Ex.

Aluno ↔ Curso

. Um aluno faz vários cursos 
. Um curso tem vários alunos 
