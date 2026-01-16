# Query API


O que é a query API?



select() - Ler dados

Exemplo com ORM:

stmt = select(User)
result = session.execute(stmt)
users = result.scalars().all()


insert() - Inserção direta no banco

stmt = insert(User).value(
    name="Leonardo",
    email="leo@gmail.com"
)
session.execute(stmt)
session.commit()


update() - Atualizar registros 

stmt = (
    update(User)
    .where(User.id == 1)
    .values(name="Novo Nome")
)

session.execute(stmt)
session.commit()


delete() - Apagar registros 

stmt = delete(User).where(User.id == 1)
session.execute(stmt)
session.commit()