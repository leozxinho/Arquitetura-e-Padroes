# Controllers


Separação em camadas:


Controllers: # Porta de entrada

O controller é um adaptador de interface para traduzir estimulos externos (HTTP, CLI, fila, UI) para algo que o caso de uso entenda e devolver a resposta no formato que o mundo externo espera.

Ele:
 - Recebe eventos externos
 - Converte dados brutos em dados estruturados
 - Encaminha a execução para um UseCase
 - Ecapsula detalhes do protocolo (HTTP, status, headers, etc.)


Analogia de forma simples:

Imagine um restaurante:

Cliente -> faz o pedido
Garçom -> leva o pedido
Cozinha -> decide como preparar

Ele/Controller:

- Anota o pedido
- Leva para cozinha
- Traz o prato


#Agora traduzindo para software

O que vem de fora?

- HTTP
- JSON
- Formulário
- Clique
- Evento

Lembrando que isso não é regra de negócio, é apenas "barulho" externo.
 
Então... o que o controller faz?

Teoricamente, só isso:

1. Recebe a entrada externa
2. Organiza os dados (sem decidir nada)
3. Chama o caso de uso correto
4. Entrega a resposta no formato correto

# Exemplo prático

Exemplo do tipo de dado que entra do mundo externo, e ocorre o cenário de entrada/saída de um UseCase:


O "mundo" manda isso,

{
  "email": "leo@email.com",
  "password": "123456"
}

O controller recebe isso e transforma em algo assim:

CriarUsuario
- email
- senha


- Ele não verifica se o e-mail existe
- Ele não valida regra
- Ele não cria usuário

obs: ele diz para o sistema que precisa apenas ser criado um novo usuário.


Depois o sistema ira realizar as devidas verificações:

- se pode criar 
- se email é valido
- se salva
- se da erro



Quando o sistema responde, ele devolve algo simples:

UsuarioCriado:
- id = 123

O controller pega isso e traduz de volta, e devolve para o mundo algo que fique entendido:

HTTP 201
{
  "id": 123
}



Map:

Mundo → Controller → Sistema → Controller → Mundo





