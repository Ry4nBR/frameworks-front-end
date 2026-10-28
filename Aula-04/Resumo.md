# Resumo - Aula 04: Consumindo APIs no Front-end

## 1. Introdução a APIs

Uma **API (Application Programming Interface)**, ou Interface de Programação de Aplicações, é um conjunto de protocolos, rotinas e ferramentas projetadas para a construção e integração de softwares.

Ela define a forma como diferentes componentes e sistemas computacionais devem interagir entre si, permitindo que aplicações distintas se comuniquem de maneira padronizada e segura, independentemente da linguagem ou plataforma em que foram desenvolvidas.

---

# 2. Estilo Arquitetural REST

O padrão **REST (Representational State Transfer)**, ou Transferência de Estado Representacional, é um estilo arquitetural para o desenvolvimento de sistemas distribuídos, amplamente adotado na World Wide Web.

### Princípios fundamentais do REST:

- **Comunicação cliente-servidor sem estado (stateless):** Cada requisição do cliente para o servidor deve conter todas as informações necessárias para que seja compreendida e processada. O servidor não armazena contexto de sessões anteriores entre requisições;
- **Uso padrão de métodos HTTP:** As operações sobre os dados utilizam os métodos formais do protocolo HTTP (GET, POST, PUT, PATCH, DELETE);
- **Identificação de recursos por URIs:** Cada recurso do sistema é mapeado e acessado por meio de um identificador unívoco (Uniform Resource Identifier);
- **Representação padronizada de dados:** Os dados trafegam formatados em padrões abertos, sendo o JSON o formato mais utilizado na atualidade.

---

# 3. Protocolo HTTP

O **HTTP (Hypertext Transfer Protocol)** é o protocolo de comunicação fundamental da Web. Ele estabelece as normas e regras de formatação para troca de mensagens e dados entre clientes (como navegadores ou aplicações front-end) e servidores web.

### Características principais:

- **Modelo cliente-servidor:** O cliente inicia a comunicação enviando uma requisição (*request*), e o servidor a processa retornando uma resposta (*response*);
- **Stateless:** Cada ciclo de requisição e resposta é isolado e independente;
- **Baseado em texto:** As mensagens possuem cabeçalhos legíveis e estruturas bem definidas.

---

# 4. Métodos HTTP

Os métodos HTTP determinam o tipo de ação que o cliente solicita ao servidor sobre determinado recurso:

| Método | Finalidade | Características |
|---|---|---|
| **GET** | Recuperar informações do servidor | Seguro (não altera dados) e idempotente (múltiplas chamadas produzem o mesmo efeito) |
| **POST** | Criar novos recursos no servidor | Não idempotente (múltiplas requisições criam múltiplos registros) |
| **PUT** | Substituir integralmente um recurso existente | Atualização completa de todas as propriedades do recurso |
| **PATCH** | Atualizar parcialmente um recurso | Altera apenas os campos enviados, preservando os demais |
| **DELETE** | Remover um recurso específico | Idempotente (remover um recurso já inexistente não gera novos efeitos) |

---

# 5. Fluxo de uma Requisição na Prática

A comunicação entre a interface do usuário e os serviços backend ocorre de forma cíclica e estruturada:

1. **Ação no Front-end:** O usuário acessa uma página ou aciona um evento de interface (como o clique de um botão);
2. **Envio da Requisição HTTP:** O navegador ou framework front-end dispara uma chamada assíncrona com o método correspondente (GET, POST, PUT, DELETE);
3. **Processamento no Servidor:** O servidor backend (como uma aplicação Express.js) intercepta a requisição, roteia para o manipulador correspondente e executa a lógica de negócio;
4. **Persistência / Integração:** O servidor consulta, grava ou atualiza informações no banco de dados ou em serviços externos;
5. **Resposta em JSON:** Ao término do processamento, o servidor envia os dados formatados em JSON acompanhados do código de status HTTP;
6. **Atualização da Interface:** O front-end processa os dados recebidos e atualiza o estado e os elementos visuais na tela.

---

# 6. EndPoint

Um **endpoint** é uma URL específica configurada em uma API que fornece acesso direto a determinado recurso ou funcionalidade do sistema.

Ele representa o ponto exato de contato e comunicação entre a aplicação cliente e o servidor.

### Exemplos:
- `GET /usuarios`: Retorna a listagem de todos os usuários;
- `POST /usuarios`: Cadastra um novo registro de usuário na base de dados.

---

# 7. Repositórios e Catálogos de APIs Públicas

Para fins de estudo e integração em aplicações reais, desenvolvedores utilizam catálogos de APIs públicas. Essas plataformas agrupam serviços abertos de terceiros, oferecendo dados para consumo direto em projetos.

### Exemplos de referências:
- Catálogo de APIs abertas: [https://www.freepublicapis.com/](https://www.freepublicapis.com/)
- Exemplo de API aberta nacional: AwesomeAPI CEP ([https://github.com/awesomeapibrasil/awesomeapi-cep](https://github.com/awesomeapibrasil/awesomeapi-cep))

---

# 8. JSON (JavaScript Object Notation)

O **JSON** é um formato aberto, leve e baseado em texto para troca de dados entre sistemas.

### Propriedades:
- Fácil leitura e escrita por seres humanos;
- Alta velocidade de análise sintática (*parse*) e geração por computadores;
- Independente de linguagem, embora baseado na notação de objetos do JavaScript.

### Estruturas fundamentais:
- **Coleções de pares chave/valor:** Representadas por objetos `{}`;
- **Listas ordenadas de valores:** Representadas por arrays `[]`.

```json
{
  "id": "USER-001",
  "nome": "Carlos Silva",
  "email": "carlos@exemplo.com",
  "idade": 28,
  "ativo": true,
  "interesses": [
    "tecnologia",
    "esportes"
  ]
}
```

---

# 9. Servidor Backend e Web Services

- **Servidor Backend:** Sistema responsável pelo processamento de requisições, gestão e persistência de dados e provisão de respostas para os clientes;
- **Funções principais:** Execução de regras de negócio, acesso a bancos de dados e disponibilização de APIs;
- **Web Service:** Serviço disponibilizado via rede sob protocolos web padrão (HTTP/HTTPS) que viabiliza a interoperabilidade entre aplicações heterogêneas construídas com diferentes linguagens e sistemas operacionais.

---

# 10. Framework Express.js

O **Express.js** é um framework minimalista e flexível desenvolvido para o ambiente Node.js, amplamente utilizado para criação de servidores web e APIs REST.

### Principais vantagens:
- **Simplificação do Node.js:** Reduz a verbosidade necessária ao utilizar o módulo nativo `http`;
- **Sistema de Roteamento:** Facilita a associação direta de verbos HTTP e rotas a funções controladoras;
- **Arquitetura de Middlewares:** Permite encadear funções para interceptar requisições, tratar logs, gerenciar erros e autenticação;
- **Performance e agilidade:** Estrutura enxuta voltada para respostas rápidas.

### Comparativo: Node.js Puro vs Express.js

#### Implementação com Node.js Puro:
```javascript
const http = require('http');

const server = http.createServer((req, res) => {
  if (req.url === '/') {
    res.end('Olá, mundo!');
  } else {
    res.end('Rota não encontrada!');
  }
});

server.listen(3000);
```

#### Implementação equivalente com Express.js:
```javascript
const express = require('express');
const app = express();

app.get('/', (req, res) => {
  res.send('Olá, mundo!');
});

app.listen(3000);
```

---

# 11. CORS (Cross-Origin Resource Sharing)

O **CORS** é um mecanismo de segurança implementado pelos navegadores que restringe o compartilhamento de recursos entre origens distintas (combinação de protocolo, domínio e porta).

Quando uma aplicação Front-end em um domínio (ex.: `http://localhost:3000` ou um domínio na Vercel) tenta consumir uma API em outro endereço (ex.: `http://api.onrender.com`), o servidor da API deve explicitamente liberar a origem por meio de cabeçalhos HTTP adequados. No Express, isso é feito por meio do middleware `cors`.

---

# 12. Construção de uma API REST com Express

Passo a passo demonstrado para inicialização e execução de uma API com suporte a CORS:

### 1. Inicializar o projeto
```bash
npm init -y
```

### 2. Instalar o Express e o módulo CORS
```bash
npm install express cors
```

### 3. Criar o arquivo `api.js`
```javascript
import express from 'express';
import cors from 'cors';

const app = express();

app.use(cors());

app.get('/', (req, res) => {
  res.json({
    date: new Date().toLocaleString('pt-BR'),
    status: 'API no Render funcionando!'
  });
});

const PORT = process.env.PORT || 3000;
app.listen(PORT, () => {
  console.log(`Servidor rodando na porta ${PORT}`);
});
```

### 4. Executar localmente
```bash
node api.js
```

---

# 13. Deploy no Render

O **Render** é uma plataforma moderna de nuvem que oferece hospedagem gerenciada com integração direta com o GitHub.

### Benefícios:
- Deploy automatizado a cada commit na branch principal;
- Suporte nativo ao Node.js;
- Emissão gratuita e automática de certificados SSL/HTTPS;
- Monitoramento integrado de logs.

### Passos para deploy:
1. Publicar o repositório da API no GitHub;
2. Criar uma conta e acessar o painel do Render (`dashboard.render.com`);
3. Criar um novo **Web Service** conectado ao repositório;
4. Configurar os comandos de execução:
   - **Build Command:** `npm install` (ou conforme especificado no ambiente)
   - **Start Command:** `node api.js`
5. Concluir o deploy e acessar a URL pública fornecida (`seu-projeto.onrender.com`).

---

# 14. Atividades Práticas

### Atividade 01
- Pesquisa de 10 projetos no GitHub com foco em consumo de APIs;
- Clonagem e análise dos projetos para identificação de frameworks e endpoints utilizados;
- Criação de relatório em Markdown contendo tabela comparativa das aplicações levantadas.

### Atividade 02
- Desenvolvimento de API com Express contendo rota para retornar a data e a hora atual em formato JSON;
- Deploy da API na plataforma Render;
- Criação de uma aplicação Front-end responsável por consumir o endpoint publicado e apresentar as informações na tela;
- Separação dos códigos em repositórios distintos no GitHub e elaboração de documentação comprobatória com capturas de tela.

---

# 15. Resumo Geral

A aula abordou os conceitos essenciais para o consumo e fornecimento de dados em arquiteturas Web modernas. Foram detalhados o funcionamento do protocolo **HTTP**, o padrão **REST**, os métodos fundamentais e a formatação de dados em **JSON**.

Na parte prática, foi explorada a construção simplificada de servidores com **Express.js**, o controle de acesso com **CORS** e o processo de publicação contínua em nuvem com o **Render**, integrando serviços backend a clientes Front-end.

---

**Fonte:** material da Aula 04, que aborda consumo de APIs no Front-end, protocolo HTTP, REST, JSON, Express.js, CORS, hospedagem no Render e atividades práticas.
