# OrderFlow

OrderFlow é uma plataforma de gerenciamento de pedidos desenvolvida para simular um ambiente de microsserviços utilizado em aplicações de e-commerce. O sistema acompanha todo o ciclo de vida de um pedido, desde a autenticação do usuário até o processamento do pagamento, a reserva de estoque e o envio de notificações.

O projeto tem como objetivo aplicar conceitos de Engenharia de Software, arquitetura de microsserviços e comunicação entre serviços, priorizando boas práticas de desenvolvimento, documentação e organização de código em um ambiente próximo ao encontrado em equipes profissionais.

## Status

O OrderFlow está em desenvolvimento e vem sendo construído de forma incremental por meio de Sprints. Novas funcionalidades, microsserviços e documentações serão adicionados ao longo da evolução do projeto.

## Project Goals

O OrderFlow foi desenvolvido com os seguintes objetivos:

* Demonstrar a implementação de uma arquitetura de microsserviços utilizando Java e Spring Boot.
* Aplicar boas práticas de Engenharia de Software, incluindo organização de código, separação de responsabilidades e documentação técnica.
* Explorar diferentes formas de comunicação entre serviços, utilizando REST para comunicação síncrona e Apache Kafka para comunicação assíncrona baseada em eventos.
* Desenvolver uma aplicação orientada a testes, utilizando testes unitários e de integração para garantir a confiabilidade dos serviços.
* Utilizar conteinerização com Docker para criar um ambiente de desenvolvimento consistente e próximo ao utilizado em produção.
* Simular um ambiente de desenvolvimento semelhante ao encontrado em equipes profissionais, adotando práticas como arquitetura documentada, versionamento estruturado, decisões arquiteturais (ADR), integração entre serviços e organização em monorepo.

## Visão Geral da Arquitetura

O OrderFlow foi projetado seguindo o estilo arquitetural de microsserviços, permitindo que cada serviço seja desenvolvido, implantado e evoluído de forma independente. Essa abordagem favorece o baixo acoplamento entre os componentes, maior escalabilidade e melhor organização das responsabilidades do sistema.

Cada microsserviço possui seu próprio banco de dados, garantindo autonomia na persistência dos dados e reduzindo dependências entre os diferentes domínios da aplicação.

A comunicação entre os serviços ocorre de duas formas. Para operações que exigem resposta imediata, é utilizada comunicação síncrona por meio de APIs REST. Já para o processamento de eventos e tarefas executadas em segundo plano, é utilizada comunicação assíncrona baseada em eventos com Apache Kafka.

O acesso aos microsserviços é centralizado por meio de um API Gateway, responsável por atuar como ponto único de entrada da aplicação, direcionando as requisições para os serviços responsáveis.

Para garantir consistência do ambiente de desenvolvimento e facilitar a implantação da aplicação, todos os componentes do sistema são conteinerizados utilizando Docker.

## Stack Tecnológica

A tabela abaixo apresenta as principais tecnologias utilizadas no OrderFlow e a finalidade de cada uma dentro da arquitetura do projeto.

| Tecnologia              | Finalidade                                                                                                          |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------- |
| **Java 21**             | Linguagem principal utilizada no desenvolvimento dos microsserviços.                                                |
| **Spring Boot**         | Framework responsável pela construção dos microsserviços e exposição das APIs REST.                                 |
| **Spring Data JPA**     | Camada de acesso a dados, simplificando a comunicação com o banco de dados.                                         |
| **Hibernate**           | Implementação ORM utilizada pelo Spring Data JPA para o mapeamento objeto-relacional.                               |
| **PostgreSQL**          | Banco de dados relacional utilizado por cada microsserviço, seguindo o princípio de *Database per Service*.         |
| **Apache Kafka**        | Comunicação assíncrona baseada em eventos entre os microsserviços.                                                  |
| **Docker**              | Conteinerização dos serviços para garantir consistência entre os ambientes de desenvolvimento e implantação.        |
| **Docker Compose**      | Orquestração do ambiente local, facilitando a execução conjunta dos microsserviços e componentes de infraestrutura. |
| **Gradle (Groovy DSL)** | Ferramenta de automação de build utilizada para gerenciamento de dependências e configuração do monorepo.           |
| **JUnit 5**             | Desenvolvimento de testes unitários.                                                                                |
| **Lombok**              | Redução de código repetitivo (*boilerplate*) nas classes Java.                                                      |
| **Swagger / OpenAPI**   | Documentação automática das APIs REST desenvolvidas no projeto.                                                     |
| **GitHub Actions**      | Automação de processos de integração contínua (CI), incluindo build e execução de testes.                           |

## Estrutura do Repositório

O OrderFlow utiliza uma organização baseada em monorepo, onde todos os microsserviços e recursos compartilhados são mantidos em um único repositório. Essa abordagem facilita o gerenciamento do projeto, a padronização da arquitetura e a evolução coordenada dos serviços.

```text
orderflow/
│
├── services/           # Microsserviços da aplicação
├── infrastructure/     # Infraestrutura (Docker, Kafka, scripts, etc.)
├── docs/               # Documentação técnica do projeto
├── .github/            # Configurações de GitHub Actions e templates
│
├── build.gradle        # Configuração principal do Gradle
├── settings.gradle     # Definição dos módulos do monorepo
├── gradle.properties   # Propriedades compartilhadas do Gradle
├── docker-compose.yml  # Ambiente de desenvolvimento
├── README.md
└── LICENSE
```

### Diretórios

#### `services/`

Contém todos os microsserviços que compõem o sistema. Cada serviço possui sua própria aplicação Spring Boot, banco de dados, dependências, testes e Dockerfile, permitindo desenvolvimento, implantação e evolução de forma independente.

#### `infrastructure/`

Armazena todos os recursos relacionados à infraestrutura da aplicação, como configurações de Docker, Apache Kafka, monitoramento, scripts de inicialização e demais componentes necessários para executar o ambiente local.

#### `docs/`

Centraliza toda a documentação do projeto, incluindo arquitetura, decisões arquiteturais (ADR), diagramas, documentação técnica e registros de aprendizado produzidos durante o desenvolvimento.

#### `.github/`

Contém os arquivos utilizados pelo GitHub, como workflows de integração contínua (GitHub Actions), templates para Issues e Pull Requests e demais configurações relacionadas ao repositório.

## Roadmap

- [x] Sprint 1 - Foundation
- [ ] Sprint 2 - Authentication Service
- [ ] Sprint 3 - Order Service
- [ ] Sprint 4 - Inventory Service
- [ ] Sprint 5 - Payment Service
- [ ] Sprint 6 - Notification Service
- [ ] Sprint 7 - API Gateway
- [ ] Sprint 8 - Observabilidade
- [ ] Sprint 9 - CI/CD
- [ ] Sprint 10 - Deploy