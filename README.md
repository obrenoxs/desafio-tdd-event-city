# DESAFIO TDD Event City

API REST desenvolvida em **Java + Spring Boot** com foco em **TDD (Test-Driven Development)**, implementando o cadastro de cidades (`City`) e eventos (`Event`), com relacionamento entre elas.

Este projeto foi desenvolvido como desafio do módulo **Testes Automatizados** do curso [Java Spring Expert](https://devsuperior.club/courses/6) da [DevSuperior](https://devsuperior.club).

## 💡 Sobre o desafio

O código base (entidades, DTOs e testes de integração) foi fornecido pelo professor. A partir dele, a proposta foi implementar toda a lógica da aplicação — repositories, services, controllers e tratamento de exceções — seguindo a metodologia TDD: os testes já existiam prontos e guiaram cada etapa da implementação, sendo executados continuamente até todos passarem.

## 🚀 Tecnologias utilizadas

- Java
- Spring Boot
- Spring Data JPA / Hibernate
- Spring MVC (REST Controllers)
- H2 Database (testes)
- JUnit 5
- MockMvc (testes de integração)
- Maven

## 📌 Funcionalidades

### City
| Método | Endpoint      | Descrição                                                                 |
|--------|---------------|----------------------------------------------------------------------------|
| GET    | `/cities`     | Lista todas as cidades, ordenadas por nome                                |
| POST   | `/cities`     | Insere uma nova cidade                                                    |
| DELETE | `/cities/{id}`| Remove uma cidade (bloqueado se houver eventos vinculados a ela)          |

### Event
| Método | Endpoint      | Descrição                                  |
|--------|---------------|---------------------------------------------|
| PUT    | `/events/{id}`| Atualiza os dados de um evento existente   |

## ⚠️ Tratamento de exceções

A API trata os seguintes cenários de erro de forma padronizada (`StandardError`), via `@ControllerAdvice`:

- **404 Not Found**: recurso não encontrado (`ResourceNotFoundException`)
- **400 Bad Request**: violação de integridade referencial, como excluir uma cidade que possui eventos vinculados (`DatabaseException`)

## 🧪 Testes

O projeto conta com testes de integração (`@SpringBootTest` + `MockMvc`) cobrindo:

- Listagem de cidades ordenada corretamente
- Inserção de cidade com retorno `201 Created`
- Remoção de cidade com `204 No Content` (sem dependências)
- Remoção de cidade com `404 Not Found` (id inexistente)
- Remoção de cidade com `400 Bad Request` (id com evento vinculado)
- Atualização de evento com `200 OK`
- Atualização de evento com `404 Not Found` (id inexistente)

Para rodar os testes:

```bash
mvn test
```

## ▶️ Como executar

```bash
git clone https://github.com/obrenoxs/bds02.git
cd bds02
mvn spring-boot:run
```

A aplicação sobe por padrão em `http://localhost:8080`.

## 👤 Autor

Desenvolvido por [Breno Oliveira de Souza](https://github.com/obrenoxs) durante os estudos do curso Java Spring Expert (DevSuperior).
