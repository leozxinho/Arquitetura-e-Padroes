# Constraints 


PRIMARY KEY

Identidade da tabela:

. Identificado unicamente em cada linha
. Não pode ser NULL
. Não pode repetir
. Só pode existir uma PK por tabela

sql: id INT PRIMARY KEY


FOREIGN KEY

Regra de realacionamento. Garante integridade entre tabelas:

. Aponta para a PRIMARY KEY (ou UNIQUE) de outra tabela
. Impede referências fantasmas (ex: pedido sem usuário)

Com controle de comportamento:

FOREIGN KEY (user_id) REFERENCES users(id)
ON DELETE CASCADE

Ex:

. CASCADE - apagou o pai? apaga os filhos
. RESTRICT - não deixa apagar
. SET NULL - quebra o relacionamento


UNIQUE

Valor não pode repetir, mas pode ser NULL(geralmente):

. Ideal para: Email, CPF, username
. Diferente da PK, pode existir mais de um UNIQUE

sql: email VARCHAR(255) UNIQUE ou combinado UNIQUE (user_id, role



CHECK 

Regra lógica. O banco valida antes de salvar

CHECK (age >= 18)
CHECK (status IN ('activate', 'inactive'))

