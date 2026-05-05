# Pesquisa

## DAO

### O que é?

DAO é um padrão de projetos que tem como objetivo separar as camadas de apresentação, processamento e acesso a dados. Ele provê uma interface que abstrai o acesso aos dados. Ele também lê e grava a partir da origem dos dados (banco de dados, memória etc.) e, por fim, encapsula esse acesso, de modo que as outras classes não precisem saber sobre isso.

### Arquitetura e responsabilidade

Por exemplo, em uma aplicação web comum que segue o modelo MVC, os DAOs ficam junto do Model e fazem um trabalho de suporte, integrando a fonte dos dados ao modelo de objeto do sistema.

Seguindo o princípio da responsabilidade única, um DAO não deve ser responsável por mais do que o acesso a dados. Ele deve fazer apenas uma leitura ou gravação no banco de dados. Não é função dele controlar transações ou realizar operações adicionais.

### Implementação

Para implementar o DAO, é preciso envolver muitos componentes, como a interface DAO e a sua implementação concreta, a Fábrica (ou Factory) DAO e o DTO (Data Transfer Object), mas todos eles são opcionais. A seguir, explico cada um dos componentes.

#### Data Transfer Object (DTO)

O DTO é responsável por transportar os dados recuperados ou persistidos de uma base de dados utilizando as camadas de lógica de um software. Um exemplo é: se você quiser transferir uma lista de objetos “Itens”, com informações desse item, como id, características e fabricação, que foram recuperados de uma “Camada de Acesso a Dados” para uma camada “Web”, a camada de serviço seria responsável por transferir de um DAO para um DTO os dados solicitados.

---

# Conexão JDBC

## Introdução

O JDBC  (Java Database Connectivity) é uma API responsavel por conectar e executar consultas em um Banco de Dados, ele pode funcionar em qualquer banco desde que os drivers certos sejam fornecidos para ele. Os drivers são implementações da API JDBC usados para conectar a um tipo específico de banco. Nós temos alguns tipos de drivers:

- Tipo 1: no primeiro tipo nós temos um mapeamento para outra API de acesso a dados, por exemplo o driver JDBC-ODBC.
- Tipo 2: esse já é uma implementação que utiliza bibliotecas do lado do cliente do banco de dados de destino, também chamado de driver de API nativa.
- Tipo 3: ele utiliza um middleware para converter chamadas JDBC em chamadas específicas do banco de dados, também conhecido como um driver de protoco de rede.
- Tipo 4: se conecta diretamente a um banco de dados convertendo chamadas JDBC em chamadas específicas do banco, são conhecidas também como drivers de protocolo de banco de dados ou drivers leves.

O tipo 4 é mais usado por ser independe de plataforma, ter conexão direta com um servidor de banco de dados proporciona um melhor desempenho. Porém, uma desvantagem é que ele é específico para cada banco de dados. 

## Ciclo de Vida

Existe basicamente um ciclo de vida de uma conexão, que representa o tempo entre a abertura da comunicação entre a aplicação Java e banco de dados e o fechamento dele. O ciclo básico segue os seguintes passos:

1. **Carregamento do Driver**: antes de se conectar é preciso que a aplicação carregue o driver específico do banco de dados (ex: MySQL, PostgreSQL, Oracle) para a memória.
2. **Estabelecimento da conexão**: nesse passo a aplicação solicita uma conexão ao banco de dados, e o driver negocia a conexão com o banco.
3. **Criação de Instrução**: enquanto a conexão está aberta, um objeto é criado para enviar comandos em SQL.
4. **Execução da Consulta SQL**: o sql é enviado, processado (parsing, otimização) e é executado pelo SGBD.
5. **Processamento dos Resultados**: a aplicação lê os dados retornados.
6. **Fechamento da Conexão (Crucial)**: a conexão deve ser fechada para liberar os recursos ocupados no banco de dados.

---

## O que é SQL injection?

SQL injection ocorre quando dados enviados pelo usuário manipulam a consulta sql original, fazendo com que os atacantes consigam vizualizar, modificar ou exluir os dados confidenciais, conseguindo contornar mecânismos de autenticação.

## Prepared statements

Traduzindo, significa declarações preparadas, são um recurso do banco de dados que serve para realizar consultas SQL de forma mais eficiente e segura, separando o comando SQL dos dados. Primeiro eles copiam o modelo da query, para depois inserir os valores, prevenindo os ataques de injeção de SQL e melhorando o desempenho.

---

# Fontes

[Implementando o Data Access Object no Java EE](https://share.google/4ihFCeVaLs2HZJdnz)

[Qual a diferença entre o Statement e o PreparedStatement?](https://share.google/W2FVViuEWw4kc3FSk)

[How to prevent SQL Injection Vulnerabilities: How Prepared Statements Work](https://share.google/JeP67I9e9B6h5bK1w)

[JDBC no Java: o que é, tipos e como usar | Alura](https://share.google/Fq7oRyQn3jkEwGyGf)

[ORM, JPA, Hibernate, JDBC, JPQL, DDL, DML e DQL: descomplicando a sopa de letrinhas do Java](https://share.google/mQn6zQMUDlr2HVRWj)
