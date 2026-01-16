# Resumo Clean Architecture

A Clean Architecture organiza o sistema em camadas bem separadas, com dependências sempre apontando para dentro.



Estrutura de pastas basica:

src
├── controllers
│   └── create_user_controller.py
│
├── usecases
│   └── create_user_usecase.py
│
├── gateways
│   └── user_gateway.py
│
├── repositories
│   └── user_repository.py
│
├── entities
│   └── user.py
│
└── main.py




Exemplo de uma arquitetura de pastas:

src
├── domain
│   ├── entities
│   │   └── user.py
│   ├── value_objects
│   │   └── email.py
│   ├── repositories
│   │   └── user_repository.py
│   ├── events
│   │   └── user_created_event.py
│   └── errors
│       └── user_errors.py
│
├── application
│   ├── use_cases
│   │   └── create_user
│   │       ├── use_case.py
│   │       ├── dto.py
│   │       └── response.py
│   └── services
│       └── password_service.py
│
├── interfaces
│   ├── http
│   │   ├── controllers
│   │   │   └── create_user_controller.py
│   │   ├── presenters
│   │   │   └── user_presenter.py
│   │   └── routes.py
│   ├── cache
│   │   └── redis_client.py
│   └── messaging
│       └── sqs_publisher.py
│
├── infrastructure
│   ├── database
│   │   ├── sqlalchemy
│   │   │   ├── models
│   │   │   │   └── user_model.py
│   │   │   ├── repositories
│   │   │   │   └── user_repository_impl.py
│   │   │   └── session.py
│   │   └── migrations
│   ├── cache
│   │   └── redis_repository.py
│   ├── messaging
│   │   └── sqs_publisher_impl.py
│   └── settings
│       └── config.py
│
├── main.py
└── container.py
