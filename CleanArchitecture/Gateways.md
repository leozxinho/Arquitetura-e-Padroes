# Gateways

Gateway é um intermediário, ele fica no meio do caminho entre:

. a regra de negócio(use case)
. e o mundo de fora(banco, API, serviço externo)

Ex:

. o use case pede algo
. o gateway vai lá fora buscar
. o use case nem sabe como isso foi feito

Gateway: 

1. Busca
2. Salvo
3. Envio
4. Recebo


Use case pensa em criar dados, o Gateway os executa.