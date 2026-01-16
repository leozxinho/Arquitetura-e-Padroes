# Column Types e Custom Types


Um dos tipos mais usado em Column Type:


from sqlalchemy import (
    Integer, String, Text, Boolean,
    Date, DateTime, Float, Numeric,
    ForeignKey
)



Custom Type (Tipos customizados)

1. Enum - Tipo controlado sem texto solto

from sqlalchemy import Enum

class Status(enum.Enum):
    ACTIVE = "active"
    BLOCKED = "blocked"

status = mapped_column(Enum(Status), nullable=False)

2. TypeDecorator - Serve para converter valores Python ↔ Banco


Ex. Salvar dict como JSON

from sqlalchemy.types import TypeDecorator, TEXT
import json

class JSONType(TypeDecorator):
    impl = TEXT

    def process_bind_param(self, value, dialect):
        return json.dumps(value) if value else None

    def process_result_value(self, value, dialect):
        return json.loads(value) if value else None

Uso:
data = mapped_column(JSONType) - Agora o banco vê texto


3. Custom Type com validação 

Exemplo. Email 

class EmailType(TypeDecorator)
   impl = String(255)

   def process_bind_param(self, value, dialect):
       if "@" not in value:
           raise ValueError("Email inválido")
        return value.lower()
        