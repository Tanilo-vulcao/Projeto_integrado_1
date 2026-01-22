# 1. Visao Geral

O sistema consiste em um fluxo de vendas automatizado
via chat, orquestrado peço n8n, integrado a um banco de
dados PostgresSQL. O usuario interage por mensagens de
texto e prenchimento de formulario via telegram, seleciona
produtos, informa a forma de pagamento de pagamento e 
endereço, e recebe a confirmação do pedido. O pagamento
é apenas simulado, sem integração real.

# 2. Objetivo

Automatizar o processo de registro de pedidos,
desde a escolha de produtos até a confirmação final,
armazenando todas as Infromações no  banco de dados
para controle e historico.

# 3. Escopo

## 3.1 Funcionalidades Incluidas

- Responder a entradas via chat
- Exibição do cardapio/Produtos via chat
- Seleção de produtos via formulario
- Seleção de quantidades via formulario
- Calculo automatico do valor do pedido
- Informar endereço/Escolher forma de pagamento (Pix, Cartão), via formulario
- confirmacao do pedido
- confirmação do pagamento(Simulação)
- Registro do pedido e itens no PostgreSQL
- Envio de mensagem de confirmação

# 4. Requisitos Funcionais

|ID|Nome|Descrição|
|-------|-------|-------|
|RF01|Responder mensagens|O Chatbot deve reponder as entradas do usuario via mensagem|
|RF02|Exibir cardapio|O Chatbot deve exibir os produtos lidos no banco dados e apresentar ao usuario|
|RF03|Solicitar produto|O Chatbot deve solicitar a escolha do usuario via formulario, e apartir dele o usuario faz suas escolhas|
|RF04|Solicitar quantidade|O Chatbot solicita ao usuario via formulario, e apartir dele o usuario digita a quantidade|
|RF05|Calculo automatico|O Chatbot deve calcular o valor do pedido de acordo com os produtos escolhidos e seus valore, e mostra ao usuario|
|RF06|Solicitar endereço e pagamento|O Chatbot deve solicitar o endereço e pagamento via formuario ao usuario, que, informara os dados(Bairro, Rua, Numero e referencia) e a forma de pagamento(Pix, Cartão)
|RF07|Confirmar pedido|O Chatbot deve apresentar o resumo do pedido e solicitar a confirmação, que atraves de mensagem o usuario confirma ou não|
|RF08|Confirmar pagamento(Simulação)|O Chatbot envia uma mensagem de simulaçao onde o usuario confirma ou não o pagamento|
|RF09|Registra pedido|O Chatbot deve registra os pedidos pagos no banco de dados e suas informções|
|RF10|Enviar confirmação|O Chatbot deve enviar uma mensagem confirmando o pedido feito ao dono do estabelecimanto para a entrega|

# 5. Requisitos Não Funcionais

|ID|Nome|Descriçaõ|
|----|----|-------|
|RNF01|Integração ao postgresSQL|O Chatbot deve utilizar o banco de dados para armazenar os dados|
|RNF02|Integração ao n8n|O chatbot deve utilizar o n8n como gerenciador do fluxo|
|RNF03|Utilização do Docker|O n8n e postgresSQL, devem rodar em um container do docker|
|RNF04|Gerenciamento de formuarios|O Chatbot deve gerenciar formularios para que so sejam aceitos como respostas, formualrios recem solicitados impedido a leitura daqueles que ja não pertence ao novo fluxo|



