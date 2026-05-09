# CP2 – API de Brinquedos
---

## Descrição
API REST para gerenciar brinquedos de crianças até 14 anos.  
Desenvolvida com Spring Boot + JPA + Oracle, rodando na porta 8080.

---

## Tecnologias
- Java 21 | Spring Boot 4.0.6 | Maven
- Spring Web, Spring Data JPA, Validation, Lombok
- Oracle JDBC | Tomcat (porta 8080)

---

## Como rodar
1. Abra a pasta `brinquedos` no IntelliJ
2. Edite `application.properties` com seu RM e senha Oracle
3. Execute `BrinquedosApplication.java`
4. Acesse `http://localhost:8080/brinquedos` no Postman

---

## Endpoints

| Método | URL | Descrição |
|---|---|---|
| GET | `/brinquedos` | Lista todos |
| GET | `/brinquedos/{id}` | Busca por ID |
| POST | `/brinquedos` | Cria novo |
| PUT | `/brinquedos/{id}` | Atualiza |
| DELETE | `/brinquedos/{id}` | Remove |

---

## Exemplos de JSON para Postman

> **Atenção:** No Postman, sempre use **Body → raw → JSON** para os métodos POST e PUT.

---

### POST – Criar brinquedos
**URL:** `http://localhost:8080/brinquedos` | **Método:** POST

**Brinquedo 1**
```json
{
  "nome": "LEGO Batman",
  "tipo": "Montar",
  "classificacao": "6+",
  "tamanho": "Médio",
  "preco": 149.90
}
```

**Brinquedo 2**
```json
{
  "nome": "Barbie Fashionista",
  "tipo": "Boneca",
  "classificacao": "3+",
  "tamanho": "Pequeno",
  "preco": 89.99
}
```

**Brinquedo 3**
```json
{
  "nome": "Hot Wheels Pista Radical",
  "tipo": "Veículo",
  "classificacao": "5+",
  "tamanho": "Grande",
  "preco": 249.90
}
```

**Brinquedo 4**
```json
{
  "nome": "Quebra-Cabeça 500 Peças",
  "tipo": "Educativo",
  "classificacao": "10+",
  "tamanho": "Médio",
  "preco": 59.90
}
```



**Resposta esperada (HTTP 201 Created):**
```json
{
  "id": 1,
  "nome": "LEGO Batman",
  "tipo": "Montar",
  "classificacao": "6+",
  "tamanho": "Médio",
  "preco": 149.90
}
```

---

### GET – Listar todos
**URL:** `http://localhost:8080/brinquedos` | **Método:** GET

**Resposta esperada (HTTP 200 OK):**
```json
[
  {
    "id": 1,
    "nome": "LEGO Batman",
    "tipo": "Montar",
    "classificacao": "6+",
    "tamanho": "Médio",
    "preco": 149.90
  },
  {
    "id": 2,
    "nome": "Barbie Fashionista",
    "tipo": "Boneca",
    "classificacao": "3+",
    "tamanho": "Pequeno",
    "preco": 89.99
  }
]
```

---

### GET – Buscar por ID
**URL:** `http://localhost:8080/brinquedos/1` | **Método:** GET

**Resposta esperada (HTTP 200 OK):**
```json
{
  "id": 1,
  "nome": "LEGO Batman",
  "tipo": "Montar",
  "classificacao": "6+",
  "tamanho": "Médio",
  "preco": 149.90
}
```

**Se o ID não existir (HTTP 404):**
```json
{
  "erro": "Brinquedo com ID 99 não encontrado."
}
```

---

### PUT – Atualizar brinquedo
**URL:** `http://localhost:8080/brinquedos/1` | **Método:** PUT

**Atualização do Brinquedo 1:**
```json
{
  "nome": "LEGO Batman Deluxe",
  "tipo": "Montar",
  "classificacao": "7+",
  "tamanho": "Grande",
  "preco": 199.90
}
```

**Atualização do Brinquedo 2:**
```json
{
  "nome": "Barbie Profissões Médica",
  "tipo": "Boneca",
  "classificacao": "4+",
  "tamanho": "Pequeno",
  "preco": 109.90
}
```

**Atualização do Brinquedo 3:**
```json
{
  "nome": "Hot Wheels Super Pista Looping",
  "tipo": "Veículo",
  "classificacao": "6+",
  "tamanho": "Grande",
  "preco": 299.90
}
```

**Resposta esperada (HTTP 200 OK):**
```json
{
  "id": 1,
  "nome": "LEGO Batman Deluxe",
  "tipo": "Montar",
  "classificacao": "7+",
  "tamanho": "Grande",
  "preco": 199.90
}
```

---

### DELETE – Remover por ID
**URL:** `http://localhost:8080/brinquedos/1` | **Método:** DELETE

**Resposta esperada (HTTP 204 No Content):**
*(sem corpo na resposta)*

---

### Validação – Campos inválidos
**Exemplo de envio com erro:**
```json
{
  "nome": "",
  "tipo": "Boneca",
  "classificacao": "3+",
  "tamanho": "Pequeno",
  "preco": -10
}
```

**Resposta (HTTP 400 Bad Request):**
```json
{
  "nome": "O nome do brinquedo é obrigatório.",
  "preco": "O preço deve ser um valor positivo."
}
```

---

