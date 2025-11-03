Sistema de E-commerce — Modelo Relacional MySQL
📘 Descrição Geral
Este projeto implementa um modelo de banco de dados relacional para um sistema de e-commerce, desenvolvido em MySQL 8 utilizando o MySQL Workbench.

O modelo foi projetado para representar de forma consistente as entidades fundamentais de uma loja virtual, incluindo Clientes, Produtos, Pedidos, Pagamentos e Entregas, com integridade referencial completa entre todas as tabelas.

Todas as relações (FKs) estão implementadas no banco e visualmente representadas por linhas contínuas no diagrama EER, indicando integridade física real.

🧩 Estrutura Conceitual
O sistema foi modelado a partir de três narrativas principais:

1️⃣ Produto
Os produtos são vendidos por uma única plataforma online.

Cada produto possui um fornecedor específico.

Um ou mais produtos podem compor um pedido.

2️⃣ Cliente
O cliente pode se cadastrar com CPF ou CNPJ.

O endereço do cliente determina o valor do frete.

O cliente pode realizar múltiplos pedidos e possui um prazo de devolução (carência).

3️⃣ Pedido
Os pedidos são criados pelos clientes e contêm informações de compra, entrega e status.

Um ou mais produtos compõem cada pedido.

O pedido pode ser cancelado.

Além dessas três narrativas principais, o modelo foi expandido para incluir as entidades de Entrega e Pagamento, garantindo uma visão completa do processo de compra.

🗂️ Estrutura Física das Tabelas
🧍 Tabelas de Pessoas e Endereços
Tabela	Descrição
clientes	Armazena dados pessoais ou empresariais (CPF/CNPJ, e-mail, telefone).
enderecos_cliente	Permite múltiplos endereços (envio, cobrança), com indicadores de padrão.

🏢 Catálogo de Produtos
Tabela	Descrição
fornecedores	Cadastro dos fornecedores dos produtos.
categorias	Classificação dos produtos por categoria.
produtos	Itens disponíveis na plataforma, com preço, descrição e vínculo ao fornecedor.
produto_categorias	Relação N:N entre produtos e categorias.
estoques	Locais físicos de armazenamento.
itens_estoque	Quantidade de cada produto em cada estoque.

📦 Pedidos e Itens
Tabela	Descrição
pedidos	Pedido principal, vinculado ao cliente, endereços e valores totais.
itens_pedido	Produtos comprados em cada pedido, com preço histórico e quantidade.

🚚 Entregas
Tabela	Descrição
transportadoras	Empresas responsáveis pelo envio.
remessas	Entregas vinculadas aos pedidos, com rastreamento e status.

💳 Pagamentos
Tabela	Descrição
metodos_pagamento	Tipos de pagamento disponíveis (PIX, Cartão, Boleto, etc.).
pagamentos	Transações financeiras associadas aos pedidos, com valor, status e data.

🔗 Relacionamentos Principais
Origem	Destino	Tipo	Descrição
clientes.id	enderecos_cliente.cliente_id	1:N	Um cliente pode ter vários endereços.
fornecedores.id	produtos.fornecedor_id	1:N	Cada produto pertence a um fornecedor.
produtos.id	itens_pedido.produto_id	1:N	Produtos são incluídos em pedidos.
pedidos.id	itens_pedido.pedido_id	1:N	Cada pedido tem um ou mais itens.
pedidos.id	remessas.pedido_id	1:N	Cada pedido pode gerar uma ou mais remessas.
transportadoras.id	remessas.transportadora_id	1:N	Cada remessa é enviada por uma transportadora.
pedidos.id	pagamentos.pedido_id	1:N	Cada pedido pode ter múltiplos pagamentos.
metodos_pagamento.id	pagamentos.metodo_id	1:N	Cada pagamento utiliza um método.

⚙️ Configuração e Execução
1️⃣ Criar o banco de dados
sql
Copiar código
CREATE DATABASE ecom_v2
  DEFAULT CHARACTER SET utf8mb4
  DEFAULT COLLATE utf8mb4_0900_ai_ci;
USE ecom_v2;
2️⃣ Executar o script DDL
Cole e execute o conteúdo do arquivo SQL (ecom_v2.sql) no editor do MySQL Workbench.
Isso criará todas as tabelas e relações automaticamente.

3️⃣ Verificar as tabelas criadas
sql
Copiar código
SHOW TABLES;
4️⃣ Visualizar o modelo no diagrama
No Workbench:

pgsql
Copiar código
Database → Reverse Engineer → ecom_v2
O diagrama EER será gerado com todas as linhas contínuas, representando as chaves estrangeiras físicas.

🧠 Observações Técnicas
Engine: InnoDB (para suportar chaves estrangeiras e transações).

Charset: UTF8MB4 (suporte completo a acentuação e emojis).

Integridade referencial: Total (todas as FKs implementadas).

Status e enums: padronizados para facilitar filtros em consultas e aplicações.

Campos de auditoria: todas as tabelas principais incluem criado_em e atualizado_em.

🧾 Exemplo de Fluxo de Uso
1️⃣ Um cliente é cadastrado e insere dois endereços (envio e cobrança).
2️⃣ Ele faz um pedido com três produtos de fornecedores distintos.
3️⃣ O sistema calcula o frete com base no CEP do endereço de envio.
4️⃣ O cliente realiza o pagamento via PIX (registrado na tabela pagamentos).
5️⃣ Uma remessa é criada com status POSTADO e código de rastreamento.
6️⃣ Após a entrega, o status muda para ENTREGUE.

🧰 Próximos Passos (opcionais)
Adicionar controle de cupons de desconto e códigos promocionais.

Implementar logs de auditoria (histórico de status de pedidos).

Adicionar tabela de usuários administrativos (gestores e operadores).

Criar triggers para atualização automática de estoque.

👨‍💻 Autor
Yggor Ramos
Projeto desenvolvido em MySQL Workbench 8.0, com foco em clareza de relacionamentos e normalização de dados.
