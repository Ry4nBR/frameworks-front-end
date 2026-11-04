# Resumo - Aula 08: Projeto React

## 1. Revisão de JavaScript para Front-end

O JavaScript é a linguagem fundamental para adicionar interatividade e dinamismo às aplicações Web. Ele permite manipular o DOM, responder a eventos do usuário, gerenciar dados, consumir APIs remotas e controlar dinamicamente a apresentação de páginas.

### Formas de Inclusão no HTML:
- **In-line / Manipuladores de Eventos:** Inserido diretamente nos atributos das tags HTML (ex.: `onclick="alert('Olá!')"`). Indicado apenas para interações muito pontuais;
- **Interno:** Inserido no documento através da tag `<script>`;
- **Externo:** Definido em arquivo `.js` separado e importado com o atributo `src` na tag `<script>` (ex.: `<script src="app.js"></script>`), sendo o padrão recomendado para facilitar modularização e manutenção.

---

# 2. Variáveis, Tipos de Dados e Operadores

### Declaração de Variáveis e Escopo:
O JavaScript permite declarar variáveis em qualquer ponto do código, e seus identificadores são estritamente *case sensitive* (`nome`, `Nome` e `NOME` são distintos).

- `var`: Apresenta escopo de função (ou global, se fora de função). Permite redeclaração e sofre *hoisting* com valor `undefined`. É considerado legado;
- `let`: Apresenta escopo de bloco (`{ }`). Não pode ser redeclarado no mesmo escopo, sendo a escolha ideal para variáveis mutáveis;
- `const`: Apresenta escopo de bloco (`{ }`). Deve ser inicializado na declaração e seu identificador não pode ser reatribuído. Garante imutabilidade da referência.

### Tipos de Dados em JavaScript:
O JavaScript realiza inferência dinâmica de tipos através do operador `typeof`:
- `String`: Sequências de texto delimitadas por aspas simples, duplas ou crases (template literals);
- `Number`: Representa números inteiros e de ponto flutuante (ex.: `10`, `3.14`);
- `Boolean`: Valores lógicos (`true` ou `false`);
- `Undefined`: Representa variável declarada cujo valor ainda não foi atribuído;
- `Null`: Representa ausência intencional de valor ou ponteiro nulo;
- `Object`: Estrutura de coleção de pares chave/valor (ex.: `{ nome: "Ana", idade: 20 }`);
- `Array`: Lista ordenada de valores (ex.: `[10, 20, 30]`);
- `Symbol`: Identificador único e imutável;
- `BigInt`: Suporte a números inteiros com precisão arbitrária além do limite de `Number`.

### Operadores:
- **Aritméticos:** Soma (`+`), Subtração (`-`), Multiplicação (`*`), Divisão (`/`), Módulo/Resto (`%`), Exponenciação (`**`);
- **Comparação:** Igualdade de valor (`==`), Igualdade estrita de valor e tipo (`===`), Desigualdade estrita (`!==`), Maior/Menor (`>`, `<`, `>=`, `<=`);
- **Lógicos:** AND (`&&`), OR (`||`), NOT (`!`).

---

# 3. Estruturas de Controle e Funções

### Condicionais:
Permitem executar diferentes fluxos de código com base em condições booleanas:
```javascript
if (nota >= 7) {
  console.log("Aprovado");
} else if (nota >= 5) {
  console.log("Recuperação");
} else {
  console.log("Reprovado");
}
```

### Estruturas de Repetição:
Permitem iterar sobre sequências e coleções:
```javascript
// Laço for clássico
for (let i = 1; i <= 10; i++) {
  console.log(i);
}
```

### Funções:
Blocos reutilizáveis de código com parâmetros e valor de retorno:
```javascript
// Função tradicional
function somar(a, b) {
  return a + b;
}

// Arrow function concisa
const somar = (a, b) => a + b;
```

---

# 4. Manipulação de Objetos, Arrays e DOM

### Objetos e Arrays:
- **Objetos:** Armazenam dados estruturados em propriedades e comportamentos em métodos;
- **Arrays:** Coleções indexadas que disponibilizam métodos utilitários essenciais para Front-end, como `.map()`, `.filter()`, `.find()` e `.forEach()`.

### Seleção e Interação com o DOM:
O navegador expõe a interface do DOM (*Document Object Model*) para manipulação via JavaScript:
- `document.getElementById('id')`: Seleciona o elemento único com o ID informado;
- `document.querySelector('seletor')`: Seleciona o primeiro elemento compatível com o seletor CSS fornecido;
- `addEventListener('evento', callback)`: Registra manipuladores assíncronos para responder a eventos (como cliques, digitação ou submissão de formulários).

---

# 5. JSX (JavaScript XML) no React

O **JSX** é uma extensão sintática para JavaScript recomendada pelo React para descrever como a interface do usuário deve se parecer visualmente.

### Características e Regras do JSX:
1. **Expressões JavaScript:** Qualquer expressão JavaScript válida pode ser interpolada dentro do JSX envolvendo-a entre chaves `{ }`:
   ```jsx
   const nome = "João";
   const saudacao = <h1>Olá, {nome}!</h1>;
   ```
2. **Diferenças em relação ao HTML:**
   - Atributos utilizam convenção *camelCase*: `className` em vez de `class`, `htmlFor` em vez de `for`;
   - Tags vazias (*self-closing*) devem obrigatoriamente ser fechadas: `<img />`, `<input />`, `<br />`;
   - Todo componente funcional deve retornar um único elemento raiz (ou um fragmento vazio `<>...</>`).
3. **Compilação:** O JSX não é executado diretamente pelos navegadores; ferramentas de build (como Babel ou Vite) o compilam em chamadas de função `React.createElement()`.

---

# 6. Componentes Funcionais e Composição

Componentes são os blocos de construção fundamentais de qualquer aplicação React. Eles encapsulam estrutura, estilo e comportamento em unidades autônomas e reutilizáveis.

### Boas Práticas e Convenções:
- Devem iniciar obrigatoriamente com a **primeira letra maiúscula** (ex.: `Cabecalho`, `CardProduto`), permitindo ao React diferenciá-los de tags HTML nativas (`header`, `div`);
- Devem retornar elementos descritos em JSX;
- Devem ser compostos de maneira modular para formar layouts complexos:

```jsx
function Cabecalho() {
  return (
    <header>
      <h1>React Lab</h1>
    </header>
  );
}

function Rodape() {
  return <footer>Material de estudo</footer>;
}

function App() {
  return (
    <div>
      <Cabecalho />
      <main>Conteúdo Principal</main>
      <Rodape />
    </div>
  );
}
```

---

# 7. Props e Fluxo Unidirecional de Dados

As **props** (abreviação de *properties*) são o mecanismo utilizado para transferir dados e configurações de um componente pai para um componente filho.

### Princípios das Props:
- **Fluxo Unidirecional (*Top-Down*):** Os dados fluem exclusivamente do pai para o filho, tornando o rastreamento do estado previsível e explícito;
- **Imutabilidade:** As props são estritamente somente leitura (*read-only*). Um componente filho jamais deve modificar diretamente as props que recebeu;
- **Reutilização:** Permitem parametrizar componentes visuais para exibir diferentes informações sem duplicar código:

```jsx
function CardAluno({ nome, curso }) {
  return (
    <div className="card">
      <h3>{nome}</h3>
      <p>Curso: {curso}</p>
    </div>
  );
}

function App() {
  return (
    <div>
      <CardAluno nome="Ana" curso="Engenharia de Software" />
      <CardAluno nome="Bruno" curso="Sistemas de Informação" />
    </div>
  );
}
```

---

# 8. Virtual DOM e Reconciliação

O **Virtual DOM** é uma representação virtual leve da interface mantida em memória pelo React e sincronizada com o DOM real do navegador.

### Como funciona o ciclo de atualização:
1. **Renderização Virtual:** Quando o estado ou as props mudam, o React gera uma nova árvore do Virtual DOM;
2. **Diffing (Comparação):** O algoritmo de comparação do React analisa as diferenças entre a nova árvore virtual e a versão anterior;
3. **Reconciliação:** O React calcula o conjunto mínimo e mais eficiente de mutações necessárias;
4. **Atualização no DOM Real:** Apenas os nós do DOM real que sofreram alterações reais são atualizados em lote (*batch*), evitando recálculos pesados de layout (*reflow* e *repaint*) e garantindo alta performance na interface.

---

# 9. Renderização de Listas e Coleções Dinâmicas

Apresentar coleções de dados (como listas de produtos, usuários ou tarefas) armazenadas em arrays é uma das operações mais comuns no Front-end.

O React utiliza o método funcional `.map()` do JavaScript para transformar coleções de dados em elementos JSX:

```jsx
const alunos = [
  { id: 101, nome: "Ana" },
  { id: 102, nome: "Bruno" },
  { id: 103, nome: "Caio" }
];

function ListaAlunos() {
  return (
    <ul>
      {alunos.map((aluno) => (
        <li key={aluno.id}>{aluno.nome}</li>
      ))}
    </ul>
  );
}
```

### A Importância do Atributo `key`:
- O atributo `key` fornece uma identidade estável e única para cada elemento da lista;
- Auxilia o algoritmo de reconciliação do Virtual DOM a identificar com precisão quais itens foram adicionados, removidos, movidos ou alterados;
- Deve-se priorizar identificadores únicos do banco de dados (ex.: `id`) em vez de índices numéricos do array.

---

# 10. Renderização Condicional

A renderização condicional permite que a aplicação exiba elementos, componentes ou mensagens específicas de acordo com o estado atual da aplicação (ex.: autenticação, carregamento, erros).

### Abordagens comuns:

## 10.1 Condicional com `if/else`
Utilizado para retornos precoces ou renderizações completas distintas:
```jsx
function MensagemAcesso({ autenticado }) {
  if (autenticado) {
    return <p>Bem-vindo de volta!</p>;
  }
  return <p>Entre para continuar.</p>;
}
```

## 10.2 Operador Ternário (`condicao ? verdadeiro : falso`)
Ideal para alternar dinamicamente entre dois elementos dentro do próprio JSX:
```jsx
function ResultadoBusca({ carregando }) {
  return (
    <div>
      {carregando ? <p>Buscando dados...</p> : <p>Busca finalizada com sucesso.</p>}
    </div>
  );
}
```

## 10.3 Operador Lógico AND (`condicao && elemento`)
Utilizado quando se deseja renderizar um elemento somente se a condição for verdadeira, não exibindo nada caso contrário:
```jsx
function Notificacoes({ totalMensagens }) {
  return (
    <div>
      <h2>Painel</h2>
      {totalMensagens > 0 && <p>Você possui novas mensagens não lidas!</p>}
    </div>
  );
}
```

---

# 11. Atividade Prática da Aula

A atividade orientada requer a criação e publicação de um projeto React completo:
- Implementação de arquitetura baseada em componentes funcionais e JSX;
- Distribuição de dados entre componentes utilizando props e fluxo unidirecional;
- Renderização de coleções dinâmicas a partir de arrays com `.map()` e chaves únicas (`key`);
- Emprego de renderização condicional em fluxos de carregamento ou autenticação;
- Publicação de repositório público no GitHub acompanhado de `README.md` contendo documentação das funcionalidades e conceitos aplicados.

---

# 12. Referências Bibliográficas

1. SOUZA, Natan. **Bootstrap 4: conheça a biblioteca front-end mais utilizada no mundo.** São Paulo: Casa do Código, 2018. E-book. Disponível em: https://plataforma.bvirtual.com.br.
2. MACHADO, Kheronn Khennedy. **Angular 11 e Firebase: construindo uma aplicação integrada com a plataforma do Google.** São Paulo: Casa do Código, 2021.
3. EIS, Diego. **Guia Front-end: o caminho das pedras para ser um dev front-end.** São Paulo: Casa do Código, 2015.
4. GONÇALVES, Edson. **Desenvolvendo aplicações Web com JSP, Servlets, JavaServer Faces, Hibernate, EJB 3 Persistence e Ajax.** Rio de Janeiro: Ciência Moderna, 2007.
5. HARTCOPP, Patrícia Ferreira. **Métrica Web.** São Paulo: Contentus, 2020.
6. NIEDERAUER, Juliano. **Desenvolvendo Websites com PHP: aprenda a criar Websites dinâmicos e interativos com PHP e banco de dados.** 3. ed. São Paulo: Novatec, 2017.
7. PREECE, J.; ROGERS, Y.; SHARP, H. **Design de Interação: além da interação Homem-Computador.** 3. ed. Porto Alegre: Bookman, 2013.
8. SOUSA, Roque Fernando Marcos. **Canvas HTML 5: composição gráfica e interatividade na Web.** Rio de Janeiro: Brasport, 2014.
