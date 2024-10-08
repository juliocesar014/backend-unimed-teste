
# Gerenciador de Tarefas

## Requisitos

- Docker
- Docker Compose

## Como Rodar o Projeto

1. **Clone o repositório:**
   ```bash
   git clone https://github.com/juliocesar014/backend-task-app.git
   cd backend-task-app
   ```

2. **Construa as imagens Docker e suba os Containers**
   ```bash
   docker-compose up -d --build 
   ```

3. **Rodar testes unitários**
    ```bash
    docker-compose run flask_test
    ```


## Rotas Disponíveis

### 1. Verificar Estado da aplicação

- **Rota:** `/health`
- **Método:** `GET`
- **Descrição:** Verifica se a aplicação está ativa.
- **Resposta de Exemplo:**
  ```json
  {
    "message": "live"
  }
  ```

### 2. Criar uma Tarefa

- **Rota:** `/tasks`
- **Método:** `POST`
- **Descrição:** Cria uma nova tarefa.
- **Payload de Exemplo:**
  ```json
  {
    "title": "Nova tarefa",
    "description": "Descrição da tarefa"
  }
  ```
- **Resposta de Exemplo:**
  ```json
  {
    "message": "task created"
  }
  ```

### 3. Listar Todas as Tarefas

- **Rota:** `/tasks`
- **Método:** `GET`
- **Descrição:** Retorna todas as tarefas criadas.
- **Resposta de Exemplo:**
  ```json
  [
    {
      "id": 1,
      "title": "Tarefa 1",
      "description": "Descrição da Tarefa 1",
      "is_done": false,
      "created_at": "2024-08-30T12:34:56Z",
      "completed_at": null
    },
    {
      "id": 2,
      "title": "Tarefa 2",
      "description": "Descrição da Tarefa 2",
      "is_done": true,
      "created_at": "2024-08-30T12:34:56Z",
      "completed_at": "2024-08-30T13:00:00Z"
    }
  ]
  ```

### 4. Obter Detalhes de uma Tarefa

- **Rota:** `/tasks/<int:id>`
- **Método:** `GET`
- **Descrição:** Retorna os detalhes de uma tarefa específica pelo ID.
- **Resposta de Exemplo:**
  ```json
  {
    "task": {
      "id": 1,
      "title": "Tarefa 1",
      "description": "Descrição da Tarefa 1",
      "is_done": false,
      "created_at": "2024-08-30T12:34:56Z",
      "completed_at": null
    }
  }
  ```

### 5. Atualizar uma Tarefa

- **Rota:** `/tasks/<int:id>`
- **Método:** `PUT`
- **Descrição:** Atualiza uma tarefa específica pelo ID.
- **Payload de Exemplo:**
  ```json
  {
    "title": "Tarefa Atualizada",
    "description": "Nova descrição",
    "is_done": true
  }
  ```
- **Resposta de Exemplo:**
  ```json
  {
    "message": "task updated"
  }
  ```

### 6. Deletar uma Tarefa

- **Rota:** `/tasks/<int:id>`
- **Método:** `DELETE`
- **Descrição:** Deleta uma tarefa específica pelo ID.
- **Resposta de Exemplo:**
  ```json
  {
    "message": "task deleted"
  }
  ```

### 7. Listar Tarefas Completadas

- **Rota:** `/tasks/completed`
- **Método:** `GET`
- **Descrição:** Retorna todas as tarefas que foram marcadas como concluídas.
- **Resposta de Exemplo:**
  ```json
  [
    {
      "id": 2,
      "title": "Tarefa 2",
      "description": "Descrição da Tarefa 2",
      "is_done": true,
      "created_at": "2024-08-30T12:34:56Z",
      "completed_at": "2024-08-30T13:00:00Z"
    }
  ]
  ```

## Importação dos Endpoints no Postman

Na raiz do projeto, há um arquivo chamado `collection.json` que pode ser importado no Postman para facilitar o teste das rotas disponíveis.

Para importar:
1. Abra o Postman.
2. Clique em **Import** no canto superior esquerdo.
3. Selecione o arquivo `collection.json` e importe.
