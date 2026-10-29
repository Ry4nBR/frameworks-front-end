# Resumo - Aula 05: Criando APIs para o Front-end

## 1. Revisão e Contexto de APIs

Uma **API (Application Programming Interface)** atua como ponte de comunicação padronizada entre diferentes sistemas de software.

No desenvolvimento moderno, a interface Front-end opera de forma desacoplada dos serviços backend. A comunicação entre ambos ocorre via requisições sob o protocolo **HTTP**, trafegando dados estruturados no formato **JSON (JavaScript Object Notation)**.

### Métodos HTTP e Idempotência:
- **GET:** Recupera recursos sem modificar o estado do servidor (seguro e idempotente);
- **POST:** Cria novos recursos no servidor (não idempotente);
- **PUT:** Substitui integralmente um recurso existente pelo identificador informado;
- **PATCH:** Atualiza dados parciais de um recurso existente;
- **DELETE:** Remove um recurso específico (idempotente).

---

# 2. Servidores Backend e Web Services

O servidor backend é responsável por:
- Processar requisições recebidas de clientes (navegadores ou aplicativos móveis);
- Aplicar regras de negócio e validações;
- Gerenciar e persistir informações;
- Disponibilizar endpoints por meio de serviços Web padronizados.

A utilização de **Web Services** baseados em REST viabiliza a interoperabilidade entre tecnologias heterogêneas, garantindo que o front-end consuma dados sem depender de detalhes internos da arquitetura do servidor.

---

# 3. Evolução da Aplicação: Implementação de CRUD

Enquanto na etapa anterior a API implementava apenas a consulta estática de data e hora, na Aula 05 a aplicação evolui para um sistema completo de gerenciamento de notas baseado no acrônimo **CRUD**:

- **Create (Criar):** Inclusão de novas notas;
- **Read (Ler / Consultar):** Listagem geral ou consulta específica por ID;
- **Update (Atualizar):** Edição de notas preexistentes;
- **Delete (Excluir):** Remoção de notas do sistema.

---

# 4. Estratégia de Persistência com Arquivo JSON

Para a camada de armazenamento das notas, adota-se um arquivo local denominado `data.json`.

A manipulação do arquivo é feita por meio do módulo nativo do Node.js `fs` (*File System*), utilizando métodos síncronos de leitura e gravação:

- `fs.readFileSync(FILE)`: Lê o conteúdo binário/texto do arquivo;
- `JSON.parse(data)`: Converte a cadeia de caracteres JSON em estruturas de dados JavaScript;
- `fs.writeFileSync(FILE, JSON.stringify(notes, null, 2))`: Serializa o array de objetos em JSON formatado e grava no disco.

### Estrutura dos Registros (`data.json`):
```json
[
  {
    "id": "1",
    "titulo": "Lembretes",
    "texto": "Comprar leite e pão",
    "criadoEm": "2026-04-28T10:00:00Z"
  },
  {
    "id": "2",
    "titulo": "Tarefas do trabalho",
    "texto": "Enviar relatório até sexta-feira",
    "criadoEm": "2026-04-28T10:00:00Z"
  }
]
```

---

# 5. Configuração e Dependências do Servidor

Para a criação do serviço backend, são configurados o framework **Express.js** e o middleware **Body-Parser**.

### 1. Criação do diretório e instalação de pacotes:
```bash
npm install express body-parser
```

- **Express.js:** Framework minimalista para criação de rotas e manipulação de requisições HTTP;
- **Body-Parser:** Middleware responsável por processar dados enviados no corpo (*body*) das requisições (como JSON em métodos POST e PUT) e disponibilizá-los em `req.body`.

---

# 6. Implementação Completa do Servidor (`server.js`)

Abaixo está a implementação integrada do servidor com tratamento de CORS e rotas CRUD:

```javascript
// Importação de dependências
const express = require('express');
const bodyParser = require('body-parser');
const fs = require('fs');

const app = express();
const PORT = process.env.PORT || 3000;
const FILE = 'data.json';

// Middleware para decodificar JSON no corpo da requisição
app.use(bodyParser.json());

// Configuração de CORS para permitir acesso de clientes externos
app.use((req, res, next) => {
  res.header('Access-Control-Allow-Origin', '*');
  res.header('Access-Control-Allow-Headers', 'Origin, X-Requested-With, Content-Type, Accept');
  res.header('Access-Control-Allow-Methods', 'GET, POST, PUT, DELETE, OPTIONS');
  next();
});

// Funções utilitárias de persistência
function readNotes() {
  try {
    const data = fs.readFileSync(FILE);
    return JSON.parse(data);
  } catch {
    return [];
  }
}

function saveNotes(notes) {
  fs.writeFileSync(FILE, JSON.stringify(notes, null, 2));
}

// 1. GET /api/notes - Listar todas as notas
app.get('/api/notes', (req, res) => {
  const notes = readNotes();
  res.json(notes);
});

// 2. POST /api/notes - Criar nova nota
app.post('/api/notes', (req, res) => {
  const notes = readNotes();
  const novaNota = {
    id: Date.now().toString(),
    titulo: req.body.titulo,
    texto: req.body.texto,
    criadoEm: new Date().toISOString()
  };
  notes.push(novaNota);
  saveNotes(notes);
  res.status(201).json(novaNota);
});

// 3. PUT /api/notes/:id - Atualizar nota por ID
app.put('/api/notes/:id', (req, res) => {
  const notes = readNotes();
  const index = notes.findIndex(n => n.id === req.params.id);
  if (index >= 0) {
    notes[index].titulo = req.body.titulo;
    notes[index].texto = req.body.texto;
    saveNotes(notes);
    res.json(notes[index]);
  } else {
    res.status(404).json({ erro: 'Nota não encontrada' });
  }
});

// 4. DELETE /api/notes/:id - Excluir nota por ID
app.delete('/api/notes/:id', (req, res) => {
  const notes = readNotes();
  const novasNotas = notes.filter(n => n.id !== req.params.id);
  saveNotes(novasNotas);
  res.json({ mensagem: 'Nota removida' });
});

// Inicialização do servidor
app.listen(PORT, () => {
  console.log(`Servidor rodando em http://localhost:${PORT}`);
});
```

---

# 7. Ciclo de Deploy e Integração com o Front-end

O fluxo de publicação e conexão entre camadas segue 10 passos estruturados:

1. **Commit e versionamento no GitHub:** Publicação do projeto backend em repositório dedicado;
2. **Criação da conta no Render:** Acesso ao painel administrativo;
3. **Criação de Web Service:** Conexão direta ao repositório GitHub do backend;
4. **Configuração de comandos de execução:**
   - *Build Command:* `npm install`
   - *Start Command:* `node server.js`
5. **Deploy e obtenção de URL:** Obtenção do endereço público HTTPS (`https://seu-projeto.onrender.com`);
6. **Execução e validação:** Verificação do status operacional dos endpoints;
7. **Criação da aplicação React:** Implementação de componentes para listagem, criação, edição e exclusão de notas;
8. **Conexão do Front-end:** Substituição dos endpoints locais (`http://localhost:3000/api/notes`) pela URL remota do Render;
9. **Deploy do Front-end:** Publicação da interface React na plataforma Vercel;
10. **Validação do sistema distribuído:** Testes de comunicação entre Vercel (Front-end) e Render (API Backend).

---

# 8. Análise Crítica: Arquitetura, Segurança e Escalabilidade

A aula propõe quatro questões técnicas para análise do modelo adotado:

### 1. Riscos de segurança e mitigação:
- **CORS irrestrito (`*`):** Permite chamadas de qualquer origem; em produção deve-se restringir aos domínios autorizados do front-end;
- **Ausência de validação e sanitização:** Dados enviados em `req.body` devem ser validados contra injeção de scripts (XSS);
- **Falta de autenticação:** Rotas críticas devem exigir controle de acesso por tokens (ex.: JWT).

### 2. Uso de arquivo JSON como persistência:
- **Vantagens:** Simplicidade de configuração, não requer instalação de bancos de dados adicionais, legibilidade direta;
- **Desvantagens:** Riscos de inconsistência com múltiplas gravações concorrentes, ausência de transações ACID e bloqueio de I/O em métodos síncronos (`fs.readFileSync` e `fs.writeFileSync`).

### 3. Limitações para escalabilidade (ex.: 10.000 registros):
- Carregar o arquivo inteiro na memória RAM a cada requisição degrada drasticamente a performance;
- Operações de busca e filtragem tornam-se lineares ($O(N)$), exigindo migração para bancos de dados relacionais (PostgreSQL/MySQL) ou NoSQL (MongoDB) com indexação.

### 4. Concentração de código em arquivo único (`server.js`):
- O padrão monolítico em arquivo único dificulta manutenção, testes unitários e trabalho colaborativo;
- Recomenda-se organizar a arquitetura em camadas (MVC): separando controladores (*controllers*), rotas (*routes*), modelos (*models*) e serviços (*services*).

---

# 9. Documentação e Testes de APIs com Postman

Uma API deve ser acompanhada de documentação técnica detalhada, especificando endpoints, parâmetros, métodos HTTP aceitos, cabeçalhos, exemplos de requisição e códigos de resposta.

O **Postman** foi apresentado como ferramenta essencial para o ecossistema de desenvolvimento:
- **Interface intuitiva:** Execução de requisições sem necessidade de scripts de linha de comando (`curl`);
- **Coleções (*Collections*):** Agrupamento ordenado de requisições organizadas por projeto ou módulo;
- **Variáveis de ambiente:** Facilidade para alternar entre ambientes locais (`localhost`) e de produção (`Render`);
- **Automatização de testes e CI/CD:** Suporte a testes automatizados com scripts pré e pós-requisição e integração contínua via linha de comando com o Newman;
- **Recursos avançados:** Criação de *Mock Servers* e monitoramento automatizado de disponibilidade (*uptime*).

---

# 10. Atividades Práticas

### Atividade 01: Sincronização do Repositório
- Atualização e consolidação de todos os arquivos desenvolvidos no repositório GitHub da disciplina;
- Envio do endereço atualizado por meio do formulário institucional de acompanhamento docente.

### Atividade 02: CRUD Completo e Documentação no Postman
- Construção de aplicação completa com backend Express.js no Render e front-end React na Vercel;
- Criação de coleção no Postman contendo as requisições para os 4 verbos CRUD (GET, POST, PUT, DELETE);
- Configuração detalhada de parâmetros e descrições dos códigos de retorno HTTP (200, 201, 204, 404, etc.);
- Documento técnico com capturas de tela e links de entrega via plataforma Canva.

---

# 11. Resumo Geral

A Aula 05 consolidou a integração prática entre clientes Front-end e servidores backend. Foi desenvolvida uma API RESTful completa com operações de CRUD sobre notas, persistência em arquivo com o módulo `fs` e publicação contínua no **Render**.

Também foram examinadas as limitações de escalabilidade de arquiteturas baseadas em arquivos locais e destacada a importância de boas práticas de segurança, modularização de código e uso do **Postman** para testes, validações e documentação técnica.

---

**Fonte:** material da Aula 05, que aborda criação de APIs para o Front-end, operações CRUD com Express.js, persistência JSON, deploy no Render, integração com React na Vercel e documentação com Postman.
