# Proposta de Solução - Desafio.

# Descrição da Solução

Todo a solução será contextualizada abaixo com suas possíveis tecnologias e exibido um diagrama representando a proposta de solução de forma a atender os requisitos pré-definidos. Não foi possível realizar a codificação do código que represente o uso na prática da solução proposta.


## Armazenamento de Dados

Para o armazenamento dos dados, e com a necessidade de níveis de segurança alto e sensibilidade de dados, foi pensado no uso de dois tipos de banco de dados SQL(SQL Server, Oracle) por serem mais robustos e NoSQL (MongoDB) e como uma aplicação de CQRS(Command Query Responsibility Segregation), buscando isolar as consultas nos bancos NoSQL e escritas no banco SQL. Sendo a aplicação responsável por eventos internos de domínio por popular o banco de consulta onde serão executadas as queries.


## Tráfego de Dados

Para o tráfego de dados, foi pensado na utilização de contêineres com o uso de Docker em desenvolvimento e a orquestração de contêineres com Kubernetes em nuvem (AKS se utilizado Azure, EKS se utilizado AWS) permitindo a escalabilidade horizontal e vertical daquelas APIs mais requisitadas como no caso dos picos de requisição quando aumentam 30x mais, auxiliado por um API Gateway (Amazon API Gateway ou Azure API Management) com centralização de dados e distribuição de carga de requisições com o uso de (Elastic Load Balancer Azure o ou Azure Load Balancer).


## Disponibilidade de Dados

Para a disponibilidade de dados para múltiplos canais e plataformas, foi idealizado uma arquitetura de microsserviços de forma a ser criados 4 APIs RESTFul, conforme identificadas no diagrama, permitindo escalar quando necessário. Uso de uma arquitetura hexagonal, com uso de DDD (Domain Driven Design) na definição de domínio por API desenvolvidas com .NET Core 5 visto sua performance de trabalho e facilidade de desenvolvimento, além do uso de mensageria para integração de APIs com o uso de eventos, assim como o uso de monitoramento, uso de Health Checks para verificar a disponibilidade das APIs Event Sourcing Pattern, permitindo o controle das operações e auditoria futuramente. Pra mensageria foi idealizado o uso de RabbitMQ em ambiente de desenvolvimento, SQS (AWS) ou Azure Service Bus (Azure). Pra monitoramento foi pensado em Application Insights (Azure) pela sua praticidade de implementação e visualização de dados. Para uma abordagem de cache, Redis foi pensado como alternativa de entrega de dados quando houver indisponibilidade de algum serviço consumido pelos sistemas.

### Clouding Computing

Todo a arquitetura foi pensado no uso de um ambiente de Clouding como Azure e AWS, devido a capacidade de disponibilidade, resiliência e eficiência propostas por essas plataformas, assim como gerenciamento e controle de todo o ecossistema.

## Diagrama
o diagrama representa o uso de CQRS no armazenamento, e consumo de dados, assim como a arquitetura de microsserviços como proposta de solução do problema informado.

![Proposta de Solução](https://github.com/luidgisarto/farmacias-app-test/blob/main/solution.png)


## License
[MIT](https://choosealicense.com/licenses/mit/)
