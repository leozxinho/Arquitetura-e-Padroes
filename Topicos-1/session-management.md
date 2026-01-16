# Session Management 


Pense na session como uma unidade de trabalho, entrou, fez o que tinha que fazer, commit ou rollback e tchau.

Ex: session

from sqlalchemy.orm import sessionmaker
from sqlalchemy import create_engine

engine = create_engine("mysqldb+aiomysql://root:leo@localhost/db", echo=True)

SessionLocal = sessionmaker(
    bind=engine,
    autoflush=False,
    autocommit=False,
)

Ex: context managers

from sqlalchemy.orm import Session

with SessionLocal.begin() as session:
    session.add(user)
    raise Exception("OK")


Dessa forma acima:
. commit automático se tudo der certo
. rollback automático se der erro
. código menor
. impossível esquecer commit/rollback


