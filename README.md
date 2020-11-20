# Departamento

A aplicação consiste em um _CRUD_ de departamentos utilizando Angular, Spring e PostgresSQL.

Para rodar é necessário apenas ter o `docker` na máquina. Seguindo os passos:

Execute o comando para gerar o pacote da API:

```
.\department-service\gradlew.bat build
```

Após finalizar execute o `docker-compose` para buildar os containers:

```
docker-compose up
```
Com isso o `docker` subirá 3 serviços:

* **API** - localhost:8080
* **FRONT** - localhost:4200
* **POSTGRESQL** - localhost:5432


## API

A API é toda construída em Java 11, utilizando Spring 2.3.1 e buildando em Gradle.

As rotas presentes nela são:

<dl>
  <dt>GET /api/departments</dt>
  <dd>Recuperar departamentos através de um filtro.</dd>
  <dt>GET /api/departments/{id}</dt>
  <dd>Recuperar departamento por id.</dd>
  <dt>POST /api/departments</dt>
  <dd>Para salvar um novo departamento.</dd>
  <dt>PUT /api/departments/{id}</dt>
  <dd>Alterar departamento.</dd>
  <dt>DELETE /api/departments/{id}</dt>
  <dd>Remover departamento.</dd>
  <dt>GET /api/boards</dt>
  <dd>Recuperar a lista de diretorias.</dd>
  <dt>GET /api/states</dt>
  <dd>Recuperar os estados.</dd>
</dl>

Para acessá-las é necessário autenticação, existe dois usuários cadastrados no aplicação:

* **admin** - pode realizar todas as ações.
* **user** - apenas tem permissão de consulta.

Para ambos a senha é **pass**.

Para mais informações é possível acessar: [Swagger Docs](http://localhost:8080/api/swagger-ui/index.html)

Para consultar o estado da API: [Health Check](http://localhost:8080/api/actuator/health)

## FRONT

O frontend é construído em Angular 11, em Typescript e utilizando Sass e Angular Materialize para a estilização das páginas.

Consiste em apenas uma página, acessada direto do "/", com uma tela de consulta, sendo possível filtrar por qualquer campo disponível, exibindo o resultado em uma tabela ordenada e paginada.
Cada registro tem a opções de edição e remoção e no alto do tela há o botão de inclusão de um novo departamento.
