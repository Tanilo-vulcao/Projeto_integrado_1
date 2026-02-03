# Projeto Integrado I: Chatbot para Venda e Pedidos de Açaí

## Documentação do Projeto

## 1. Visão Geral

O sistema consiste em um fluxo de vendas automatizado via chat, 
orquestrado pelo n8n, integrado a um banco de dados PostgreSQL. 
O usuário interage por mensagens de texto e preenchimento de formulário via Telegram,
seleciona produtos, informa a forma de pagamento e endereço, e recebe a confirmação do pedido. 
O pagamento é apenas simulado, sem integração real. 
### Identificação do usuário:
O sistema não possui módulo de autenticação ou cadastro de usuários. O usuário é identificado exclusivamente pelo identificador da plataforma de chat (chat_id), sendo este utilizado para controle de sessão, pedidos e fluxo de interação.

## 2. Objetivo

Automatizar o processo de registro de pedidos, desde a escolha de produtos até a confirmação final,  
armazenando todas as informações no banco de dados para controle e histórico.

## 3. Escopo

### 3.1 Funcionalidades Incluídas

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

### 3.2 Funcionalidades Excluídas

- Integração real com gateways de pagamento
- Confirmação bancária de pagamentos

## 5. Requisitos

### 5.1 Requisitos Funcionais

| ID   | Nome                     | Descrição |
|------|--------------------------|-----------|
| RF01 | Responder mensagens      | O chatbot deve responder às entradas do usuário via mensagem e formulários.|
| RF02 | Exibir cardápio          | O chatbot deve exibir os produtos lidos no banco de dados e apresentá-los ao usuário.|
| RF03 | Solicitar produto        | O chatbot deve solicitar a escolha do usuário via formulário, e a partir dele o usuário faz suas escolhas.|
| RF04 | Solicitar quantidade     | O chatbot solicita ao usuário via formulário, e a partir dele o usuário digita a quantidade.|
| RF05 | Cálculo automático       | O chatbot deve calcular o valor do pedido de acordo com os produtos escolhidos e seus valores, e mostrar ao usuário. E se o valor for menor ou igual a zero (ou seja a quantida digitada foi zero para todos os produtos escolhidos), o pedido é automaticamente cancelado.|
| RF06 | Solicitar endereço e pagamento | O chatbot deve solicitar o endereço e pagamento via formulário ao usuário, que informará os dados (bairro, rua, número e referência (opcional) ) e a forma de pagamento (Pix, Cartão).|
| RF07 | Confirmar pedido/Cancelar Pedido| O chatbot deve apresentar o resumo do pedido e solicitar a confirmação, que, através de mensagem, o usuário confirma ou não.|
| RF08 | Confirmar pagamento (simulação) | O chatbot envia uma mensagem de simulação onde o usuário confirma ou não o pagamento (simulando um caso real que o usuário pode paga ou não um pedido e só assim ele realmente e confirmado ). E a espera para ser efetuado o pagamento deve ser de 5 minutos.|
| RF09 | Registrar pedido         | O chatbot deve registrar os pedidos pagos no banco de dados e suas informações.|
| RF10 | Enviar confirmação       | O chatbot deve enviar uma mensagem confirmando o pedido feito ao dono do estabelecimento para a entrega.|
|RF11|Fazer o Controle de Sessão e Formulários|O sistema deve controlar a sessão do usuário, verificar se já existe uma sessão ativa, identificar a etapa atual do fluxo (sessao_iniciada_1 (numero_etapa = 1), menu_enviado_2 (numero_etapa = 2), pagar_3 (numero_etapa = 3)) e o código do pagamento pix, cartão (codigo_pagamento (pix = 1, cartão = 2)). Garantir que apenas formulários recentemente solicitados sejam aceitos, desconsiderando respostas de formulários antigos (codigo_formulario), controle de erro como a opção voltar "0", (primeiro_erro_zero). A sessão deve ser encerrada: 1 Ao final do pedido; 2 Se o total for menor ou igual a zero ou seja o usuário cancelou as escolhas, digitando zero na quantidade dos produtos por ele escolhido; 3 Após tempo limite de inatividade.|

#

### 5.2 Requisitos Não Funcionais

| ID   | Nome                     | Descrição |
|------|--------------------------|-----------|
| RNF01 | Integrar ao PostgreSQL | O chatbot deve utilizar o banco de dados para armazenar os dados. |
| RNF02 | Integrar ao n8n        | O chatbot deve utilizar o n8n como gerenciador do fluxo. |
| RNF03 | Utilizar o Docker     | O n8n e o PostgreSQL devem rodar em contêineres Docker. |
|RNF04 | Manutenibilidade | O sistema deve ser estruturado de forma a permitir manutenção facilitada dos fluxos no n8n e do banco de dados PostgreSQL, utilizando contêineres Docker para isolar os serviços e simplificar atualizações.|


#

## 6. Modelagem do Sistema 

### 6.1 Diagrama de Caso de Uso


![DiagramaDeCasoDeUso_AcaiBot_PI1](https://github.com/user-attachments/assets/d3ee4526-c9a4-4121-85ae-e2d11ada1424)

#

### 6.2 Diagrama Entidade Relacionamento (DER)

<img width="893" height="682" alt="DIagrama_entidade_relacionamento_AcaiBot_PI1" src="https://github.com/user-attachments/assets/06a92935-9d9d-4e41-9cdd-1c9f3742e9ae" />


## Autores

Elizany Furtado Martins e Tanilo Vulcão de Freitas
