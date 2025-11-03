🧩 Modelo de Banco de Dados — Sistema de E-commerce
📘 Descrição Geral
Este projeto apresenta o modelo relacional de um sistema de e-commerce, desenvolvido em MySQL Workbench, com foco na clareza dos relacionamentos entre entidades como Clientes, Produtos, Pedidos, Pagamentos e Entregas.

O arquivo principal (diagrama_eer.mwb) contém todo o modelo visual (EER Diagram), com todas as chaves estrangeiras (FKs) e relacionamentos físicos definidos.

💡 Este repositório disponibiliza o modelo visual completo, sem dados ou script SQL exportado.
Ideal para fins acadêmicos, documentação de sistemas ou engenharia de software.

🧱 Estrutura do Projeto
Arquivo incluso:

Arquivo	Descrição
diagram_ecom_v2.mwb	Arquivo do MySQL Workbench contendo o modelo visual (EER Diagram) completo.

Não incluso:

Arquivo .sql (estrutura textual)

Dados de exemplo (INSERTs)

Triggers, procedures ou views

🧩 Entidades Principais
🛍️ Produto
Cada produto possui um fornecedor.

Um ou mais produtos podem compor um pedido.

Produtos podem ser classificados em categorias.

👤 Cliente
O cliente pode se cadastrar com CPF ou CNPJ.

Cada cliente possui um ou mais endereços (envio e cobrança).

O endereço do cliente determina o frete.

Cada cliente pode realizar vários pedidos.

📦 Pedido
Criado por um cliente, contendo um ou mais produtos.

Armazena informações de status, frete e valores totais.

Pode ser cancelado ou devolvido dentro do prazo de carência.

🚚 Entrega
Cada pedido pode gerar uma ou mais remessas.

As remessas estão vinculadas a uma transportadora, com código de rastreio e status de entrega.

💳 Pagamento
Cada pedido pode ter um ou mais pagamentos.

Suporta métodos como PIX, cartão de crédito, boleto, etc.

Armazena status da transação e valor pago.

🔗 Relacionamentos Principais
Origem	Destino	Tipo	Descrição
clientes	enderecos_cliente	1:N	Um cliente possui vários endereços.
fornecedores	produtos	1:N	Cada produto pertence a um fornecedor.
pedidos	itens_pedido	1:N	Um pedido possui um ou mais itens.
produtos	itens_pedido	1:N	Produtos são vinculados a itens de pedido.
pedidos	pagamentos	1:N	Cada pedido pode ter vários pagamentos.
pedidos	remessas	1:N	Cada pedido pode ter várias entregas.
transportadoras	remessas	1:N	Uma transportadora realiza várias remessas.

⚙️ Como abrir o diagrama
Baixe o arquivo diagrama_eer.mwb.

Abra o MySQL Workbench (versão 8.0 ou superior).

Vá em File → Open Model...

Selecione o arquivo .mwb.

O diagrama EER será exibido automaticamente, com todas as tabelas e relações.

💡 É possível gerar o script SQL completo usando
File → Export → Forward Engineer SQL CREATE Script... dentro do Workbench.

🧠 Observações Técnicas
Ferramenta: MySQL Workbench 8.0

Engine: InnoDB (para suporte a chaves estrangeiras)

Charset: UTF8MB4

Integridade referencial: todas as FKs ativas (linhas contínuas no diagrama)

Status: modelo completo, sem dados de teste

📜 Licença e Uso
Este modelo pode ser utilizado livremente para fins acadêmicos, estudos e documentação de sistemas.
Recomenda-se citar este repositório em trabalhos ou demonstrações.

👨‍💻 Autor
Yggor Ramos
Projeto de modelagem de banco de dados para e-commerce, desenvolvido em MySQL Workbench.
Contato profissional: www.linkedin.com/in/yggorramos
