# DevOps

## Solução & Arquitetura Moderniazação 

O desenho dessa arquitetura de soluções foi realizado com base no estudo feito para uma aplicação do segmento de uma seguradora.
Nesse caso de uso apresentado, vamos falar da porto seguro que é uma empresa de segmento de automóvel, residência e empresarial.

## Descrição da Empresa

A Porto Seguro é uma empresa brasileira com mais de 70 anos de mercado e está entre as maiores seguradoras do País, ocupando a primeira posição nos ramos de Seguro Auto e Residência. Atualmente, são mais de 8,4 milhões de clientes únicos, 13 mil funcionários, 12 mil prestadores e 35 mil corretores parceiros. A companhia tem ainda 101 sucursais e escritórios regionais em todo o Brasil. O Grupo Porto Seguro é formado por 27 empresas – entre elas Azul Seguros, Itaú Seguros de Auto e Residência, Porto Seguro Saúde e Porto Seguro Uruguai – que atuam nos mais diversos ramos como seguros, produtos financeiros, serviços de emergência e conveniência, proteção e monitoramento, plano de saúde para Pets, entre outros. Em 2020, o lucro líquido da companhia foi de R$ 1,695,8 milhões.

"[https://exemplo.com/logo.png](https://github.com/tayralabdesafios/DevOps/assets/145468256/02a985b8-7790-4a8c-92a3-64180204360f))"

## Regra do Negócio

Análisando a estratégias da empresa está o desenvolvimento de uma plataforma de cálculo e subscrição, que viabilize a implementação de vendas cruzadas (cross-sell) dos produtos da Porto Seguro, com abrangência de atuação para negócios de Seguros, Financeiros e Serviços.

- Visando concretizar tal estratégia e sabendo da vital necessidade do negócio em lidar com diversos dados gerados em tempo real para fornecer assim uma experiência exclusiva e personalizada para cada cliente, foi tomada a decisão de utilizar tecnologias que possibilitem a elasticidade das aplicações e interdependência dos sistemas focando sempre em um ambiente confiável, escalável, resiliente e altamente disponível.

- Pensando em autonomia de desenvolvimento dos roteiros de cálculo para integração de diversos serviços utilizados nas rotinas de precificação e aceitação, são agregadas funcionalidades adicionais no que tange estratégia de oferta, como implementações de inteligência de oferta corporativa (venda consultiva) e campanha, dando possibilidades de integrar APIs de modelos estatísticos que visam trazer mais inteligência no processo de vendas, risco e operacionais.

- Através de um estudo foi concluído que será necessário criar uma arquitetura com  diminuição de downtime e velocidade nas entregas contínuas de novas features e assim garantir o time-to-market do negócio, aliando com uma arquitetura baseada em serviços.

# Arquitetura AWS e Serviços

A arquitetura desenvolvida será hospedada na nuvem AWS que facilita o processo de migração para aplicativos existentes enquanto preserva opções para criar novas soluções.
Desse modo vamos utilizar os serviços abaixo conforme necessidade dos aplicativos e com base nas regras de negocio da empresa.

- Cluster EKS
  
Os containers proporcionam uma maneira padrão de empacotar código, configurações e dependências de seu aplicativo em um único objeto. Eles compartilham um sistema operacional instalado no servidor e são executados como processos isolados de recursos. Isso permite fazer implantações rápidas, confiáveis e consistentes, independentemente do ambiente. A Nuvem AWS oferece recursos de infraestrutura otimizados para a execução de containers, além de um conjunto de serviços de orquestração que facilitam a criação e execução de aplicativos conteinerizados em produção.

-  Serverless
  
Serviço totalmente geranciado e  sem servidor é uma forma de criar e executar aplicativos e serviços sem precisar gerenciar a infraestrutura . Sua aplicação ainda roda em servidores, mas todo o gerenciamento do servidor é feito pela AWS. Reduz e permite que os desenvolvedores recuperem tempo e energia para investirem no desenvolvimento de produtos incríveis, escaláveis e confiáveis, reduzem a complexidade operacional da execução e do gerenciamento de aplicações.
  
-  NoSQL

Bancos de dados NoSQL são criados para modelos de dados específicos e têm esquemas flexíveis para a criação de aplicativos modernos. Os bancos de dados NoSQL são amplamente reconhecidos por sua facilidade de desenvolvimento, funcionalidade e performance em escala. Em um banco de dados NoSQL, um registro de livro é normalmente armazenado como um documento JSON. Para cada livro, o item, o ISBN, o Título do livro, o Número de edição, o Nome do autor e o AuthorID são armazenados como atributos em um único documento. Neste modelo, os dados são otimizados para desenvolvimento intuitivo e escalabilidade horizontal.
  
-  API Gateways
  
O Amazon API Gateway é um serviço gerenciado que permite que desenvolvedores criem, publiquem, mantenham, monitorem e protejam APIs em qualquer escala com facilidade. APIs agem como a “porta de entrada” para aplicativos acessarem dados, lógica de negócios ou funcionalidade de seus serviços de back-end. Usando o API Gateway, você pode criar APIs do RESTful e APIs do WebSocket que habilitam aplicativos de comunicação bidirecionais em tempo real. O API Gateway dá suporte a cargas de trabalho conteinerizadas e sem servidor, além de aplicativos da web.

O API Gateway administra todas as tarefas envolvidas no recebimento e processamento de até centenas de milhares de chamadas de API simultâneas, inclusive gerenciamento de tráfego, suporte de CORS, controle de autorização e acesso, com fluxo controlado, monitoramento e gerenciamento de versões de API. O API Gateway não tem taxas mínimas ou custos antecipados. Você paga apenas pelas chamadas de API recebidas e pela quantidade transferida de dados de saída. Além disso, com o modelo de definição de preço em camadas do API Gateway, você pode reduzir os custos à medida que seu uso da API é escalado.

# CI/CD
Com base no modelo de arquitetura proposta para a empresa e pensando em modernizar todo o processo foi impletado a esteira de CI/CD Continuous Integration/Continuous Delivery. Essa implantação te como objetivo acelera o desenvolvimento automatizando o trabalho manual de validação e implantação de alterações na base de código. Pensando nisso vamos utilizar os seguintes serviços da AWS para construção da esteira:


- AWS CodePipeline
  
O AWS CodePipeline é um serviço totalmente gerenciado de entrega contínua que ajuda a automatizar pipelines de lançamento para oferecer atualizações rápidas e confiáveis de aplicações e infraestruturas.

- O AWS CodeCommit é um serviço de controle de código-fonte totalmente gerenciado, seguro e altamente escalável que hospeda repositórios privados do Git.


- O AWS CodeBuild é um serviço de integração contínua totalmente gerenciado que compila código-fonte, executa testes e produz pacotes de software prontos para implantação.


- O Amazon Elastic Container Registry (Amazon ECR) é um registro de contêiner totalmente gerenciado que oferece hospedagem de alta performance para que você possa implantar imagens e artefatos de aplicações de forma confiável em qualquer lugar.
  
- O AWS Lambda é um serviço de computação sem servidor e orientado a eventos que permite executar código para praticamente qualquer tipo de aplicação ou serviço de backend sem provisionar ou gerenciar servidores.


img src="![image](https://github.com/tayralabdesafios/DevOps/assets/145468256/73958709-e560-4174-9262-7beb3d7bd7cd)


# Monitoramento e Observabilidade

A observabilidade da AWS permite coletar, correlacionar, agregar e analisar a telemetria na sua rede, na infraestrutura e nas aplicações em ambientes na nuvem, híbridos ou on-premises para que você obtenha insights sobre o comportamento, a performance e a integridade do seu sistema. Esses insights ajudam a detectar, investigar e solucionar os problemas com mais rapidez; e juntamente com a inteligência artificial e machine learning, a reagir, prever e evitar problemas de forma proativa.
- O Amazon CloudWatch coleta e visualiza logs, métricas e dados de eventos em tempo real em painéis automatizados para otimizar sua infraestrutura e manutenção de aplicações.
  
- O AWS X-Ray fornece uma visão completa das solicitações à medida que elas percorrem sua aplicação e filtra dados visuais em cargas úteis, funções, rastreamentos, serviços, APIs e muito mais com movimentos sem código e com pouco código.
  
- O Amazon Managed Grafana é um serviço totalmente gerenciado para o Grafana, uma plataforma de análise de código aberto popular que permite consultar, visualizar, entender e receber alertas sobre suas métricas, não importa onde elas estejam armazenadas.

- O Amazon Managed Service for Prometheus é um serviço compatível com o Prometheus que monitora e fornece alertas sobre aplicações em contêiner e infraestrutura em escala. O serviço é integrado ao Amazon Elastic Kubernetes Service (EKS), Amazon Elastic Container Service (ECS) e AWS Distro para OpenTelemetry.

![image](https://github.com/tayralabdesafios/DevOps/assets/145468256/47d6cad7-5722-429f-842d-35671c0df9b4)
  

# Benefícios

 As melhorias tecnológicas foram:

- Implementação de API’s para consumo de diversos produtos;
- Utilização de Machine Learning para os modelos estatísticos;
- Segmentação por microsserviços;
- Centralização de vários cálculos complexos em uma única plataforma.
- Já o para os negócios percebemos a criação de novas estratégias e também o aumento de velocidade significativo para todos os clientes da plataforma, em que os benefícios colhidos por negócios foram:

- Maior agilidade na implementação e lançamento de novos modelos estatísticos;
- Criação de novas e maiores possibilidades de cross-sell, Up-Sell e retenção de clientes;
- Implementação e maior velocidade de processamento em lotes de renovação de contratos.”
