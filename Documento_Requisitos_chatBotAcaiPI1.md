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
- Informar endereço via formualrio
- Escolher forma de pagamento (Pix, Cartão) via formulario
- confirmar pedido
- confirmar pagamento(Simulação)
- Registro do pedido e itens no PostgreSQL
- Envio de mensagem de confirmação


# 4. Requisitos Funcionais
|Id|Nome|Descrição|
|-------|-------|-------|
|RF01|Responder mensagens|O Chatbot deve reponder as entradas do usuario via mensagem|
|RF2|Exibição do cardapio|O Chatbot deve exibir os produtos lidos no banco dados e apresentar ao usuario|
|RF3|Selecionar produto|O chatbot deve solicitar a escolha do usuario via formulario, e apartir dele o usuario faz suas escolhas|
|RF4|Selcionar quantidade|O Chatbot solicita ao usuario via formulario, e apartir dele o usuario digita a quantidade|








