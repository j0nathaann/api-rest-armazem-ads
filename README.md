# API REST - Armazém

API REST para gerenciamento de produtos, clientes e pedidos de um armazém, desenvolvida como atividade da disciplina de Análise e Desenvolvimento de Sistemas (ADS).

## Tecnologias

- Node.js
- TypeScript
- Express
- SQLite (sqlite3)
- Zod (validação de dados)

## Como executar

1. Clone o repositório:
   ```
   git clone https://github.com/j0nathaann/api-rest-armazem-ads.git
   cd api-rest-armazem-ads
   ```

2. Instale as dependências:
   ```
   npm install
   ```

3. Crie o banco de dados e o schema:
   ```
   npm run db:init
   ```

4. (Opcional) Popule o banco com dados de exemplo:
   ```
   npm run db:seed
   ```

5. Inicie o servidor em modo de desenvolvimento:
   ```
   npm run dev
   ```

A API ficará disponível em `http://localhost:3000`.

## Endpoints

| Método | Rota                    | Descrição                          |
|--------|-------------------------|------------------------------------|
| GET    | /products               | Lista os produtos                  |
| GET    | /products/:id           | Busca um produto                   |
| POST   | /products               | Cria um produto                    |
| PUT    | /products/:id           | Atualiza um produto                |
| DELETE | /products/:id           | Remove um produto                  |
| GET    | /customers              | Lista os clientes                  |
| GET    | /customers/:id          | Busca um cliente                   |
| GET    | /customers/:id/orders   | Lista os pedidos de um cliente     |
| POST   | /customers              | Cria um cliente                    |
| PUT    | /customers/:id          | Atualiza um cliente                |
| DELETE | /customers/:id          | Remove um cliente                  |
| GET    | /orders                 | Lista os pedidos                   |
| GET    | /orders/:id             | Busca um pedido com seus itens     |
| POST   | /orders                 | Cria um pedido                     |

As requisições de exemplo estão no arquivo `requests.http`, que pode ser executado com a extensão REST Client do VS Code.

## Regras de negócio

- Não é possível cadastrar dois clientes com o mesmo e-mail.
- Não é possível remover um produto ou cliente que tenha pedidos associados.
- O preço do item é registrado no momento da venda.

## Estrutura de pastas

```
src/
├── config/        # conexão com o banco
├── controllers/   # recebem as requisições
├── database/      # schema SQL, inicialização e seed
├── errors/        # classe de erro da aplicação
├── middlewares/   # tratamento global de erros
├── models/        # interfaces dos dados
├── repositories/  # acesso ao banco
├── routes/        # definição das rotas
├── schemas/       # validação com Zod
└── services/      # regras de negócio
```