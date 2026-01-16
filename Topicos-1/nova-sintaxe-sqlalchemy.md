# Nova sintaxe do SQLAlchemy


Agora o SQLAlchemy usa "type hints do python" como fonte de verdade. O ORM fica mais previsível, mais legível.


# Mapped/column

Exemplo da sintaxe antiga:

class User(Base):
    __tablename___ = "users"

    id = Column(Integer, primary_key=True)
    nome = Column(String)


Problemas:

. Tipagem implícita
. ORM e Python "desalinhados"
. Fácil de errar e só descobrir um runtime


Exemplo da sintaxe nova(2.0):


from sqlalchemy.orm import Mapped, mapped_column

class User(Base):
    __tablename__ = "users"

    id: Mapped[int] = mapped_column(primary_key=True)
    name: Mapped[str]


Vantagens:

. Tipagem explícita
. IDE entende tudo
. Código mais limpo
. ORM alinhado com Python moderno



# Relationship


Exemplo:


from sqlalchemy.orm import relationship

class User(Base):
    __tablename__ = "users"

    id: Mapped[int] = mapped_column(primary_key=true)
    name: Mapped[str]


class Post(Base):
   __tablename__ = "posts"

   id: Mapped[int] = mapped_column(primary_key=True)
   title: Mapped[str]

   user_id: Mapped[int] = mapped_column(ForeignKEy("users.id"))
   user: mapped["User"] = relationship(back_populates="posts")




Regra:

Banco de dados?
→ Mapped[...]

Configuração da coluna?
→ mapped_column()

Relacionamento entre tabelas?
→ relationship()
