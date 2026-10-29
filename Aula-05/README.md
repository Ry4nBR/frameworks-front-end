# Aula 05 - Criando APIs para o Front-end

## Sobre a aula

Quinta aula da disciplina de Frameworks Front-end, destinada ao aprofundamento na criação de APIs RESTful e implementação de operações completas de CRUD (Create, Read, Update, Delete) utilizando Express.js e Node.js.

Foram revisados os conceitos fundamentais de HTTP, métodos de requisição, endpoints, JSON e arquitetura cliente-servidor. A aula avançou com a implementação de um servidor de notas persistidas em arquivo JSON (`data.json`), manipulação do corpo de requisições com `body-parser`, tratamento de CORS e publicação contínua do backend no Render.

Além disso, foram abordados a integração entre a aplicação Front-end em React (hospedada na Vercel) e a API online, questões de segurança e escalabilidade arquitetural, e a documentação e testes de endpoints utilizando o Postman.

## Conteúdos

- Revisão de APIs, HTTP, Endpoints e JSON
- Servidor Backend e Web Service
- Evolução do Projeto Express: Implementação de CRUD
- Persistência de Dados em Arquivo JSON com o módulo `fs`
- Manipulação de Requisições com `body-parser`
- Rotas RESTful:
  - Listagem de notas (`GET /api/notes`)
  - Criação de nota (`POST /api/notes`)
  - Obtenção de nota por ID (`GET /api/notes/:id`)
  - Atualização de nota (`PUT /api/notes/:id`)
  - Exclusão de nota (`DELETE /api/notes/:id`)
- Conexão entre Front-end React e API no Render
- Questões de Arquitetura, Segurança e Escalabilidade
- Documentação Técnica de APIs
- Ferramenta Postman: Criação de Coleções, Testes e Monitoramento
- Atividades Práticas

## Material da aula

[Visualizar PDF da aula](./Aula-05.pdf)

## Resumo

O resumo completo do conteúdo apresentado está disponível em:

[Resumo da Aula 05](./Resumo.md)

## Atividade

A aula contou com duas atividades práticas:

### Atividade 01

Atualização do repositório da disciplina com todos os arquivos e alterações desenvolvidas, assegurando que a versão disponibilizada esteja completa e acessível no GitHub, com envio comprobatório via formulário institucional.

### Atividade 02

Desenvolvimento completo de uma aplicação de gerenciamento de notas (CRUD) com backend em Express.js persistido em arquivo JSON e deploy no Render. Construção de uma aplicação Front-end em React consumindo a API online e publicada na Vercel.

Criação e configuração de uma coleção no Postman documentando os quatro endpoints CRUD, acompanhada de parâmetros e descrições claras de códigos de status de resposta. Elaboração de documento técnico comprobatório com capturas de tela e links das aplicações e coleções.

### Repositórios das atividades

- Backend de exemplo: [https://github.com/deivisontakatu/exemplo-api-backend](https://github.com/deivisontakatu/exemplo-api-backend)
- Frontend de exemplo: [https://github.com/deivisontakatu/exemplo-api-frontend](https://github.com/deivisontakatu/exemplo-api-frontend)

> Demais links serão adicionados após a conclusão das atividades.
