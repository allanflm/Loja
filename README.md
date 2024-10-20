# Sistema de Cadastro de Produtos para Loja Online

## Visão Geral
Este projeto foi desenvolvido utilizando **Golang** para criar um sistema de cadastro de produtos voltado para uma loja online. O objetivo principal é fornecer uma API robusta que permita o cadastro, consulta, atualização e remoção de produtos do catálogo da loja. A aplicação segue os princípios de **Clean Architecture** e está estruturada de forma escalável para suportar o crescimento da loja ao longo do tempo.

## Funcionalidades Principais

- **Cadastro de Produtos**: Os administradores da loja podem cadastrar novos produtos com informações detalhadas, como nome, descrição, preço, categoria, quantidade em estoque e imagens.
- **Consulta de Produtos**: O sistema oferece uma API que permite a consulta de produtos por diferentes parâmetros, como nome, categoria e intervalo de preço, com resultados paginados para melhor desempenho.
- **Atualização de Produtos**: Produtos já cadastrados podem ser editados, permitindo a modificação de informações como preço, estoque e descrição.
- **Remoção de Produtos**: Produtos podem ser removidos do catálogo, seja temporariamente (desativação) ou permanentemente (remoção definitiva).

## Tecnologias Utilizadas

- **Linguagem de Programação**: Go (Golang) — Escolhida pela sua eficiência, concorrência nativa e facilidade de escalabilidade.
- **Banco de Dados**: PostgreSQL — Utilizado para armazenar de forma segura as informações dos produtos.
- **API RESTful**: Construída utilizando o framework `net/http` do Go, seguindo o padrão REST para permitir fácil integração com outras partes do sistema (como o front-end da loja).
- **ORM**: GORM — Para facilitar a manipulação dos dados no banco de forma mais intuitiva e produtiva.

## Estrutura do Projeto

### Camada de Modelos (Models)
Define as entidades principais, como `Produto`, com os seguintes campos:
- `ID`: Identificador único do produto.
- `Nome`: Nome do produto.
- `Descrição`: Descrição detalhada do produto.
- `Preço`: Valor do produto.
- `Estoque`: Quantidade disponível em estoque.
- `Categoria`: Categoria do produto (eletrônicos, vestuário, etc.).
- `Imagens`: Links para as imagens do produto.

### Camada de Serviços (Services)
Implementa a lógica de negócios para o gerenciamento dos produtos, como validação de dados, verificação de estoque e regras de negócio específicas da loja (por exemplo, restrição de preço mínimo).

### Camada de Repositórios (Repositories)
Responsável pela interação com o banco de dados. Essa camada contém funções que permitem criar, buscar, atualizar e deletar produtos no PostgreSQL.

### Controladores (Controllers)
Faz a interface entre a aplicação e o cliente (API). Aqui estão implementados os endpoints da API:
- `POST /produtos`: Para cadastrar um novo produto.
- `GET /produtos`: Para listar os produtos.
- `GET /produtos/{id}`: Para obter detalhes de um produto específico.
- `PUT /produtos/{id}`: Para atualizar informações de um produto.
- `DELETE /produtos/{id}`: Para remover um produto.

### Validação e Autenticação
O sistema inclui validação de campos (por exemplo, preço não pode ser negativo) e um sistema básico de autenticação para garantir que apenas administradores possam cadastrar ou editar produtos.

## Desafios Técnicos Superados

- **Concorrência e Eficiência**: Utilizamos as goroutines do Go para permitir a manipulação de múltiplos pedidos ao mesmo tempo, garantindo que o sistema seja altamente eficiente mesmo sob alta carga.
- **Tratamento de Erros**: Um sistema robusto de tratamento de erros foi implementado, retornando respostas HTTP adequadas, como erros 404 (não encontrado) ou 400 (pedido mal formulado).
- **Persistência de Dados**: Integração com o PostgreSQL utilizando o GORM garantiu um acesso eficiente e seguro aos dados, suportando transações complexas e garantindo a consistência do banco.

## Futuras Melhorias

- **Integração com Serviços Externos**: Integração com serviços de pagamento e plataformas de frete.
- **Testes Automatizados**: Implementação de testes unitários e de integração para garantir a estabilidade do sistema.
- **Interface Gráfica**: Desenvolvimento de uma interface web para que os administradores possam gerenciar os produtos de forma mais intuitiva.

## Conclusão

Esse sistema de cadastro de produtos é altamente escalável, eficiente e fácil de integrar com outras partes de uma plataforma de e-commerce. Utilizando as funcionalidades nativas do Go e uma arquitetura bem estruturada, o projeto oferece uma base sólida para lojas que desejam crescer de maneira consistente e organizada.
