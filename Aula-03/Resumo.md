# Resumo - Aula 03: Projetos com Frameworks Front-end

## 1. Introdução aos Frameworks Front-end

Um **framework front-end** é um conjunto de ferramentas, bibliotecas e convenções que fornece uma estrutura para padronizar e facilitar o desenvolvimento de interfaces Web.

O objetivo é acelerar o desenvolvimento e facilitar a criação e manutenção de aplicações mais complexas.

### Desenvolvimento sem framework

No desenvolvimento utilizando apenas JavaScript (Vanilla JS), muitas tarefas precisam ser realizadas manualmente. Isso pode resultar em:

- Repetição de código;
- Maior dificuldade de manutenção;
- Maior quantidade de código manual;
- Maior dificuldade para organizar aplicações complexas.

### Desenvolvimento com framework

Os frameworks oferecem recursos que facilitam o desenvolvimento, como:

- Componentes reutilizáveis;
- Gerenciamento de estado;
- Atualizações eficientes da interface;
- Estrutura organizada;
- Recursos para roteamento;
- Integração com APIs.

---

# 2. Framework x Biblioteca

Embora os termos sejam frequentemente utilizados como sinônimos, existe uma diferença importante entre **framework** e **biblioteca**.

## Framework

O framework possui uma estrutura definida e normalmente controla o fluxo de execução da aplicação.

Isso está relacionado ao conceito de **inversão de controle**: em vez de o desenvolvedor controlar completamente quando determinada funcionalidade será executada, o framework define parte desse fluxo.

Características:

- Possui uma estrutura definida;
- Controla o fluxo da aplicação;
- Apresenta convenções e padrões;
- Pode fornecer diversos recursos integrados.

Exemplos apresentados:

- Angular;
- Vue.

## Biblioteca

Uma biblioteca fornece funcionalidades que podem ser utilizadas pelo desenvolvedor quando necessário.

Características:

- O desenvolvedor controla quando utilizar suas funcionalidades;
- Possui maior flexibilidade;
- Não impõe uma estrutura completa para a aplicação.

Exemplos apresentados:

- React;
- jQuery.

### Exemplo

Em uma biblioteca, o desenvolvedor pode chamar uma funcionalidade quando precisar.

Já em um framework, o próprio framework pode determinar quando determinadas partes da aplicação serão executadas ou renderizadas.

> **Importante:** o React é frequentemente chamado de framework, mas, tecnicamente, o material da aula o classifica como uma **biblioteca JavaScript**.

---

# 3. Por que utilizar Frameworks?

Os frameworks oferecem diversos recursos que podem facilitar o desenvolvimento de aplicações Web.

### Produtividade

Fornecem soluções prontas para tarefas comuns, evitando que o desenvolvedor precise criar tudo do zero.

Exemplos:

- Roteamento;
- Gerenciamento de estado;
- Renderização.

### Boas práticas

A utilização de componentes e padrões ajuda a manter o código mais organizado.

### Manutenção

Recursos internos dos frameworks podem facilitar a atualização e manutenção da interface.

Exemplos apresentados:

- Virtual DOM no React;
- Change Detection no Angular.

### Comunidade e suporte

Frameworks populares possuem:

- Documentação;
- Comunidades ativas;
- Plugins;
- Tutoriais;
- Soluções para problemas comuns.

---

# 4. Principais tecnologias apresentadas

Na aula foram apresentadas quatro tecnologias principais:

| Tecnologia | Classificação apresentada | Característica |
|---|---|---|
| React | Biblioteca JavaScript | Criação de interfaces e componentes reutilizáveis |
| Angular | Framework | Framework completo para aplicações Web |
| Vue.js | Framework progressivo | Pode ser adotado gradualmente |
| Next.js | Framework baseado em React | Aplicações Web modernas e recursos full-stack |

---

# 5. Características dos Frameworks Front-end

## 5.1 Estrutura de código organizada

Frameworks oferecem uma estrutura para organizar o código e facilitar:

- Manutenção;
- Escalabilidade;
- Separação de responsabilidades;
- Reutilização de código.

Muitos frameworks utilizam **componentes**, que permitem dividir a interface em partes menores.

## 5.2 Componentização

Um **componente** é uma parte independente e reutilizável da interface.

Um componente pode encapsular:

- Lógica;
- Estrutura;
- Apresentação.

A componentização permite reutilizar partes da aplicação e facilita a manutenção.

## 5.3 Programação reativa

Frameworks como React, Vue e Angular possuem mecanismos que permitem atualizar a interface automaticamente quando o estado da aplicação é alterado.

Isso reduz a necessidade de manipulação manual do DOM.

## 5.4 Build e Bundling

As ferramentas de desenvolvimento podem realizar tarefas como:

- Minificação;
- Transpilação;
- Combinação de arquivos.

Esses processos ajudam no desempenho e na compatibilidade da aplicação.

## 5.5 Sistema de rotas

Os frameworks podem facilitar a criação de aplicações com diferentes páginas e rotas.

Em aplicações **SPA (Single Page Application)**, a navegação pode ocorrer sem a necessidade de recarregar toda a página.

## 5.6 Integração com APIs

Frameworks facilitam a comunicação entre a interface e serviços externos.

Isso permite:

- Realizar chamadas assíncronas;
- Consumir APIs;
- Sincronizar dados;
- Trabalhar com gerenciamento de estado.

## 5.7 Documentação e comunidade

Frameworks populares possuem comunidades e documentações que fornecem:

- Tutoriais;
- Plugins;
- Exemplos;
- Soluções para problemas comuns.

## 5.8 Design e acessibilidade

Frameworks podem incentivar boas práticas de design e acessibilidade por meio de componentes e padrões.

## 5.9 Testes

Algumas ferramentas fornecem suporte para:

- Testes unitários;
- Testes de integração.

Esses recursos ajudam a verificar a confiabilidade da aplicação.

---

# 6. Comparação entre Frameworks

A escolha da tecnologia deve considerar as características do projeto.

Entre os fatores apresentados na aula estão:

- Complexidade do projeto;
- Curva de aprendizado;
- Desempenho;
- Escalabilidade;
- Manutenção;
- Suporte da comunidade;
- Experiência do usuário.

Cada tecnologia possui características próprias, portanto a escolha depende das necessidades da aplicação.

---

# 7. React

O **React** foi desenvolvido pelo Facebook em 2013 e é uma biblioteca JavaScript utilizada para criar interfaces de usuário dinâmicas e eficientes.

Para trabalhar com React, é necessário possuir conhecimentos de:

- HTML;
- JavaScript.

O React utiliza uma arquitetura baseada em componentes e o **Virtual DOM**.

## 7.1 Hooks

### useState

É utilizado para gerenciar o estado de um componente funcional.

### useEffect

É utilizado para lidar com efeitos colaterais, como chamadas de API.

## 7.2 JSX

O **JSX** permite escrever uma estrutura semelhante ao HTML dentro do código JavaScript.

Algumas diferenças:

- Expressões JavaScript são utilizadas dentro de `{}`;
- Atributos utilizam camelCase;
- `class` é representado por `className`;
- Tags precisam ser fechadas.

Exemplo:

```bash

<img src="imagem.png" />

```

## 7.3 Gerenciamento de estado

Foram apresentados:

### Context API

Uma solução simples e direta, adequada para determinados casos de gerenciamento de estado.

### Redux

Pode ser utilizado para estados mais complexos e compartilhados globalmente.

---

# 8. DOM e Virtual DOM

**DOM (Document Object Model)** é uma representação em árvore da estrutura de uma página Web.

O JavaScript pode utilizar o DOM para alterar o conteúdo da página.

O **Virtual DOM**, utilizado pelo React, funciona como uma representação da interface.

Quando ocorre uma alteração:

1. O React atualiza o Virtual DOM;
2. Compara a versão atual com a anterior;
3. Identifica as diferenças;
4. Aplica as alterações necessárias no DOM real.

Esse processo busca tornar as atualizações da interface mais eficientes.

---

# 9. Angular

O **Angular** é um framework desenvolvido pelo Google.

É apresentado como um framework completo para desenvolvimento de aplicações Web, incluindo recursos para aplicações de página única (SPA).

## 9.1 Requisitos

Para trabalhar com Angular, o material apresenta como requisitos:

- Node.js instalado;
- Conhecimentos de Programação Orientada a Objetos (POO).

## 9.2 Principais características

O Angular oferece:

- Roteamento;
- HTTP Client;
- Injeção de dependências;
- TypeScript;
- Arquitetura MVC;
- Angular CLI;
- Change Detection.

## 9.3 Conceitos fundamentais

### Componentes

Os componentes utilizam:

- HTML;
- CSS;
- TypeScript.

A estrutura utiliza o decorator `@Component`.

### Módulos

Os módulos, representados por `@NgModule`, organizam a aplicação em blocos funcionais.

### Serviços

Os serviços permitem organizar lógica reutilizável utilizando `@Injectable`.

### Data Binding

O Angular possui recursos de ligação de dados, como:

- `[(ngModel)]` para two-way binding;
- `{{ }}` para interpolação.

### Injeção de dependência

Permite fornecer dependências aos componentes e serviços utilizando uma hierarquia de providers.

### Roteamento

O `RouterModule` permite configurar a navegação entre diferentes views.

---

# 10. Criando um Projeto Angular

O Angular utiliza o **Angular CLI (Command Line Interface)** para criar, gerenciar e construir projetos.

### 1. Instalar o Angular CLI

```bash

npm install -g @angular/cli

```

### 2. Criar o projeto

```bash

ng new meu-app-angular

```

### 3. Entrar na pasta

```bash

cd meu-app-angular

```

### 4. Abrir no VS Code

```bash

code .

```

### 5. Iniciar o servidor

```bash

ng serve

```

---

# 11. Estrutura de um Projeto Angular

## node_modules

Armazena os pacotes e dependências instalados no projeto.

As dependências podem ser instaladas utilizando:

```bash

npm install

```

ou:

```bash

npm i

```

## public

Armazena arquivos estáticos, como:

- HTML;
- JSON;
- Imagens;
- Outros recursos públicos.

## src

É o diretório principal do código-fonte da aplicação.

Pode conter:

- Componentes;
- Serviços;
- Módulos;
- Outros arquivos da aplicação.

## app

Contém os principais componentes, módulos, serviços e arquivos da aplicação Angular.

## index.html

É o ponto de entrada HTML da aplicação.

O componente raiz é renderizado por meio do seletor:

```bash

<app-root>

```

## main.ts

É o arquivo principal responsável pela inicialização da aplicação.

## styles.css

Contém os estilos globais da aplicação.

## angular.json

É o arquivo principal de configuração do Angular, incluindo configurações relacionadas a:

- Build;
- Testes;
- Estilos globais.

## package.json

Gerencia informações, dependências e scripts do projeto.

## package-lock.json

Registra informações das dependências instaladas.

## .gitignore

Define arquivos e diretórios que devem ser ignorados pelo Git, como `node_modules` e arquivos de ambiente.

## tsconfig.json

Define configurações gerais do TypeScript.

Também existem arquivos específicos, como:

- `tsconfig.app.json`;
- `tsconfig.spec.json`.

---

# 12. Vue.js

O **Vue.js** é apresentado como um framework progressivo que pode ser adotado gradualmente conforme as necessidades da aplicação aumentam.

## 12.1 Requisitos

Para trabalhar com Vue, o material apresenta:

- Node.js instalado;
- Conhecimento em JavaScript/TypeScript;
- Conhecimento em programação reativa e baseada em componentes.

## 12.2 Principais características

### Progressivo

Pode ser utilizado desde pequenas partes de uma aplicação até aplicações SPA mais complexas.

### Reatividade

Possui um sistema de reatividade que permite atualizar a interface automaticamente.

### Single-File Components

Os **SFCs (Single-File Components)** permitem organizar HTML, CSS e JavaScript em um único arquivo `.vue`.

### Curva de aprendizado

A sintaxe é apresentada como acessível para iniciantes, mantendo recursos para aplicações mais avançadas.

### Performance

Utiliza Virtual DOM e possui otimizações para desempenho.

---

# 13. Criando um Projeto Vue

### 1. Criar o projeto

```bash

npm create vue@latest

```

### 2. Entrar na pasta

```bash

cd meu-projeto-vue

```

### 3. Instalar as dependências

```bash

npm install

```

### 4. Abrir no VS Code

```bash

code .

```

### 5. Iniciar o servidor

```bash

npm run dev

```

---

# 14. Estrutura de um Projeto Vue

## node_modules

Contém os pacotes e dependências instalados.

## public

Contém arquivos estáticos que não passam pelo processo de build do Vite.

Exemplos:

- `favicon.ico`;
- `robots.txt`.

## src

É o diretório principal do código-fonte.

## assets

Armazena recursos que são processados pelo Vite, como:

- Imagens;
- Fontes;
- CSS global.

## components

Contém componentes Vue reutilizáveis.

Exemplos:

```bash

Button.vue
Header.vue

```

## App.vue

É o componente raiz da aplicação.

Pode conter:

- Estrutura;
- CSS;
- JavaScript.

Também pode importar outros componentes.

## main.js

É o ponto de entrada da aplicação Vue.

É responsável por montar a aplicação no DOM e configurar plugins globais.

## index.html

É o HTML principal da SPA.

Contém a `div` com `id="app"`, onde o Vue é inserido.

## vite.config.js

Contém configurações do Vite, como:

- Build;
- Plugins;
- Proxies.

---

# 15. Next.js

O **Next.js** é um framework baseado em React para desenvolvimento de aplicações Web modernas e full-stack.

Ele adiciona recursos que não fazem parte diretamente do React.

Entre os recursos apresentados estão:

- Roteamento baseado em arquivos;
- Renderização no servidor;
- Server Components;
- Otimização de imagens;
- Otimização de fontes;
- Gerenciamento de páginas;
- Gerenciamento de layouts;
- APIs e recursos de backend;
- Otimizações para desempenho;
- Recursos relacionados a SEO.

---

# 16. Criando um Projeto Next.js

### 1. Criar o projeto

```bash

npx create-next-app@latest meu-projeto

```

### 2. Entrar na pasta

```bash

cd meu-projeto

```

### 3. Abrir no VS Code

```bash

code .

```

### 4. Iniciar o servidor

```bash

npm run dev

```

---

# 17. Estrutura de um Projeto Next.js

## node_modules

Contém os pacotes e dependências instalados no projeto.

## public

Armazena arquivos estáticos.

## app

É o diretório principal da aplicação quando utilizado o **App Router**.

Pode conter:

- Páginas;
- Layouts;
- Estilos globais;
- Componentes relacionados à estrutura da aplicação.

Os arquivos `page.js` definem páginas, enquanto a organização das pastas determina as rotas.

---

# 18. Importação de Projetos

Nem sempre é necessário começar um projeto do zero.

A comunidade **open source** disponibiliza diversos projetos que podem ser utilizados como modelos e personalizados.

Isso pode acelerar o desenvolvimento e permitir o aproveitamento de estruturas e boas práticas existentes.

## Ferramentas apresentadas

### GitHub

Permite pesquisar repositórios desenvolvidos com diferentes frameworks.

Um projeto pode ser copiado utilizando:

```bash

git clone <url>

```

### Vercel

Possui templates que podem ser utilizados como base para projetos.

### CodeSandbox

Permite pesquisar templates e projetos desenvolvidos com diferentes tecnologias.

---

# 19. Git e Versionamento dos Projetos

Durante o desenvolvimento dos projetos, o **Git** deve ser utilizado para versionar as aplicações.

Os projetos devem ser publicados no **GitHub**, mantendo um histórico de commits que registre a evolução do desenvolvimento.

Esse histórico permite acompanhar as alterações realizadas durante o projeto.

---

# 20. Atividade Prática

A atividade proposta consiste no desenvolvimento, em grupo, de **quatro projetos Web sobre o mesmo tema**, utilizando diferentes tecnologias.

Os projetos devem ser desenvolvidos com:

1. React;
2. Vue;
3. Angular;
4. Next.js.

Cada projeto deve apresentar:

- Uma página funcional;
- Design responsivo;
- Organização adequada;
- Componentes;
- Recursos básicos da tecnologia escolhida.

Durante o desenvolvimento, os projetos devem:

- Ser versionados com Git;
- Ser publicados no GitHub;
- Manter um histórico de commits;
- Ser organizados em seus respectivos repositórios.

Ao final, deve ser realizada uma breve comparação entre as quatro tecnologias, destacando as principais diferenças encontradas durante o desenvolvimento.

## Entregas

| Projeto | Tecnologia |
|---|---|
| Projeto 01 | React |
| Projeto 02 | Vue |
| Projeto 03 | Angular |
| Projeto 04 | Next.js |
| Projeto 05 | Cópia de um projeto a partir de um repositório |

---

# 21. Resumo Geral

A aula apresentou os principais conceitos relacionados aos **Frameworks Front-end**, começando pela diferença entre desenvolvimento com e sem frameworks e pela distinção entre **framework e biblioteca**.

Foram estudadas as tecnologias **React, Angular, Vue.js e Next.js**, suas principais características, conceitos fundamentais e formas de criação de projetos.

Também foram apresentadas as estruturas básicas dos projetos Angular, Vue e Next.js, além de ferramentas para criação e gerenciamento dos projetos.

Por fim, foi abordada a utilização do **Git e GitHub** durante o desenvolvimento e proposta uma atividade prática para desenvolver aplicações utilizando as quatro tecnologias e comparar as diferenças encontradas durante o desenvolvimento.

---

**Fonte:** material da Aula 03, que aborda introdução aos frameworks, React, Angular, Vue, Next.js, criação de projetos, Git/versionamento e atividade prática.