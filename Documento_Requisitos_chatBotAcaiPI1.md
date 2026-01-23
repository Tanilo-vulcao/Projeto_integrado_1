
# Nome do projeto: Chatbot para Venda e Pedidos de Açaí


# 1. Visão Geral

O sistema consiste em um fluxo de vendas automatizado via chat, orquestrado pelo n8n, integrado a um banco de dados PostgreSQL. O usuário interage por mensagens de texto e preenchimento de formulário via Telegram, seleciona  
produtos, informa a forma de pagamento e  
endereço, e recebe a confirmação do pedido. O pagamento é apenas simulado, sem integração real.

# 2. Objetivo

Automatizar o processo de registro de pedidos,  
desde a escolha de produtos até a confirmação final,  
armazenando todas as informações no banco de dados  
para controle e histórico.

# 3. Escopo

## 3.1 Funcionalidades Incluídas

- Responder a entradas via chat  
- Exibição do cardápio/produtos via chat  
- Seleção de produtos via formulário  
- Seleção de quantidades via formulário  
- Cálculo automático do valor do pedido  
- Informar endereço/escolher forma de pagamento (Pix, Cartão), via formulário  
- Confirmação do pedido  
- Confirmação do pagamento (simulação)  
- Registro do pedido e itens no PostgreSQL  
- Envio de mensagem de confirmação  

# 4. Documentação do Projeto


# 5. Requisitos



## 5.1 Requisitos Funcionais

| ID   | Nome                     | Descrição |
|------|--------------------------|-----------|
| RF01 | Responder mensagens      | O chatbot deve responder às entradas do usuário via mensagem |
| RF02 | Exibir cardápio          | O chatbot deve exibir os produtos lidos no banco de dados e apresentá-los ao usuário |
| RF03 | Solicitar produto        | O chatbot deve solicitar a escolha do usuário via formulário, e a partir dele o usuário faz suas escolhas |
| RF04 | Solicitar quantidade     | O chatbot solicita ao usuário via formulário, e a partir dele o usuário digita a quantidade |
| RF05 | Cálculo automático       | O chatbot deve calcular o valor do pedido de acordo com os produtos escolhidos e seus valores, e mostrar ao usuário |
| RF06 | Solicitar endereço e pagamento | O chatbot deve solicitar o endereço e pagamento via formulário ao usuário, que informará os dados (bairro, rua, número e referência) e a forma de pagamento (Pix, Cartão) |
| RF07 | Confirmar pedido         | O chatbot deve apresentar o resumo do pedido e solicitar a confirmação, que, através de mensagem, o usuário confirma ou não |
| RF08 | Confirmar pagamento (simulação) | O chatbot envia uma mensagem de simulação onde o usuário confirma ou não o pagamento |
| RF09 | Registrar pedido         | O chatbot deve registrar os pedidos pagos no banco de dados e suas informações |
| RF10 | Enviar confirmação       | O chatbot deve enviar uma mensagem confirmando o pedido feito ao dono do estabelecimento para a entrega |



## 5.2 Requisitos Não Funcionais

| ID   | Nome                     | Descrição |
|------|--------------------------|-----------|
| RNF01 | Integrado ao PostgreSQL | O chatbot deve utilizar o banco de dados para armazenar os dados |
| RNF02 | Integrado ao n8n        | O chatbot deve utilizar o n8n como gerenciador do fluxo |
| RNF03 | Utilizar o Docker     | O n8n e o PostgreSQL devem rodar em contêineres Docker |
| RNF04 | Gerenciar formulários | O chatbot deve gerenciar formulários para que somente sejam aceitos como resposta formulários recém solicitados, impedindo a leitura daqueles que já não pertencem ao novo fluxo |