# Projeto Integrado I: Chatbot para Venda e Pedidos de Açaí

## Documentação do Projeto

## 1. Visão Geral

O sistema consiste em um fluxo de vendas automatizado via chat, 
orquestrado pelo n8n, integrado a um banco de dados PostgreSQL. 
O usuário interage por mensagens de texto e preenchimento de formulário via Telegram,
seleciona produtos, informa a forma de pagamento e endereço, e recebe a confirmação do pedido. 
O pagamento é apenas simulado, sem integração real. 
### 1.1 Identificação do Usuário:
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
| RF01 | Responder Mensagens      | O sistema deve responder às entradas do usuário via mensagem e formulários personalizados.|
| RF02 | Exibir Cardápio          | O sistema deve exibir os produtos lidos no banco de dados e apresentá-los ao usuário.|
| RF03 | Solicitar Produto        | O sistema deve solicitar ao usuário que escolha a partir de um formulário seus produtos.|
| RF04 | Solicitar Quantidade     | Via formulário o sistema solicita a quantidade dos produtos escolhidos pelo usuário.|
| RF05 | Cálculo Automático       | O sistema deve calcular o valor do pedido de acordo com os produtos escolhidos e seus valores, e mostrar ao usuário. E se o valor for menor ou igual a zero (ou seja a quantida digitada foi zero para todos os produtos escolhidos), o pedido é automaticamente cancelado.|
| RF06 | Solicitar Endereço e Pagamento | O sistema deve solicitar o endereço e pagamento via formulário ao usuário, que informará os dados (bairro, rua, número e referência (opcional) ). E a forma de pagamento (Pix, Cartão).|
| RF07 | Confirmar Pedido/Cancelar Pedido| O sistema deve apresentar o resumo do pedido e solicitar a confirmação que através de mensagem o usuário confirma ou não.|
| RF08 | Confirmar Pagamento (simulação) | O sistema envia uma mensagem de simulação onde o usuário confirma ou não o pagamento (simulando um caso real que o usuário pode paga ou não um pedido e só assim ele realmente é confirmado ).|
| RF09 | Registrar Pedido         | O sistema deve registrar os pedidos pagos no banco de dados e suas informações.|
| RF10 | Enviar Confirmação       | O sistema deve enviar uma mensagem de confirmação ao dono do estabelecimento contendo os detalhes do pedido para a entrega.|
|RF11|Fazer o Controle de Sessão e Etapas|O sistema deve controlar a sessão do usuário, verificar se já existe uma sessão para aquele usuário e se está ativa e identificar a etapa atual do fluxo, (Sem sessão ou sessão encerrada (numero_etapa = vazio); sessao iniciada (numero_etapa = 1); menu enviado (numero_etapa = 2); pagar  (numero_etapa = 3)). Fazer o controle de erro como a opção voltar "0", (primeiro_erro_zero). E encerramento de sessão. A sessão deve ser encerrada: 1 Ao final do pedido; 2 Se o total for menor ou igual a zero ou seja o usuário cancelou as escolhas, digitando zero nas quantidades dos produtos por ele escolhido; 3 Após tempo limite de inatividade.|
|RF12|Fazer o Controle de Formulário| O sistema deve garantir que apenas formulários recentemente solicitados sejam aceitos, desconsiderando respostas de formulários antigos (codigo_formulario).|
|RF13|Gerenciar Códigos de Pagamento e Id dos Pedidos | O sistema deve gerenciar o código de pagamento, pix ou cartão (codigo_pagamento (pix = 1; cartão = 2)), assim como o id do pedido (id_pedido), recem amarzenado para atualização do status do pedido.|

#

### 5.2 Requisitos Não Funcionais

| ID   | Nome                     | Descrição |
|------|--------------------------|-----------|
| RNF01 | Integrar ao PostgreSQL | O sistema deve utilizar o banco de dados para armazenar os dados. |
| RNF02 | Integrar ao n8n        | O sistema deve utilizar o n8n como gerenciador do fluxo. |
| RNF03 | Utilizar o Docker     | O n8n e o PostgreSQL devem rodar em um contêineres Docker. |
|RNF04 | Manutenibilidade | O sistema deve ser estruturado de forma a permitir manutenção facilitada dos fluxos no n8n e do banco de dados PostgreSQL, utilizando contêineres Docker para isolar os serviços e simplificar atualizações.|
|RNF05|Escalabilidade|O sistema deve ser capaz de suportar o aumento gradual no número de usuários e pedidos simultâneos, garantindo a integridade dos dados e mantendo o desempenho adequado mesmo com o crescimento.|
|RNF06|Desempenho|O sistema deve responder às interações do usuário em tempo adequado, garantindo fluidez na conversa.|
|RNF07|Disponibilidade|O sistema deve esta disponível para uso contínuo.|
|RNF08|Segurança|O sistema deve manter os dados amarzenados e de fluxo protegidos evitando acessos não autorizados.|
|RNF09|Usabilidade|O sistema deve possuir interação simples e intuitiva, permitindo que o usuário realize pedidos com facilidade, por meio de mensagens claras e formulários guiados.|

#

## 6. Modelagem do Sistema 

### 6.1 Diagrama de Caso de Uso


![DiagramaDeCasoDeUso_AcaiBot_PI1](https://github.com/user-attachments/assets/d3ee4526-c9a4-4121-85ae-e2d11ada1424)


#

### 6.2 Diagrama Entidade Relacionamento (DER)


<img width="773" height="603" alt="Diagrama_entidade_relacionamento_AcaiBot_PI1" src="https://github.com/user-attachments/assets/2f932815-5117-41af-a7c3-239b50a0c7bc" />


## Autores

Elizany Furtado Martins e Tanilo Vulcão de Freitas
