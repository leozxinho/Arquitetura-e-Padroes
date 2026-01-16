# Back References 


1. Back reference (conceito geral)

Em modelagem de domínio, um relacionamento entre duas entidades pode ser:

. Unidirecional -> só um lado "conhece" o outro
. Bidirecional -> os dois lados se conhecem 

Back reference é exatamente isso: a referência inversa de um relacionamento bidirecional.

Se A se relaciona com B, a back reference é o caminho B -> A.




2. back_populates (teoria)

back_populates é a declaração explícita de simetria entre dois lados de um relacionamento.

Em termos teóricos:

. Você está dizendo: "Esses dois atributos representam o mesmo vínculo no domínio"
. Cada entidade:
    . define sua própria visão do relacionamento
    . sabe exatamente quem é o outro lado

Conceito-chave
   Consistência explícita

Ambos os lados:
.   existem por vontade do modelador
. têm nomes, responsabilidades e intenções claras
. formam um contrato bidirecional declarado

Analogia

É como um contrato assinado por duas partes.
Nada fica implícito. Nada é presumido


[Exemplo-codígo]

class User(Base):
    __tablename__ = "users"

    id = mapped_column(primary_key=True)
    addresses = relationship("Address", back_populates="user")

class Address(Base):
    __tablename__ = "addresses"

    id = mapped_column(primary_key=True)
    user_id = mapped_column(ForeignKey("users.id"))
    user = relationship("User", back_populates="addresses")


O que está acontecendo?

. User.addresses ↔ Addresses.user
. SQLAlchemy não inventa nada
. Você bate o olho e entende o modelo