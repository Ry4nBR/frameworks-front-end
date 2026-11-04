# Resumo - Aula 09: Projeto React 02

## 1. Estado (State) e o Hook `useState`

Nas aplicações em React, o **estado (*state*)** representa as informações dinâmicas que um componente armazena e gerencia internamente ao longo do tempo (como o valor de um contador, o texto de um campo de busca ou itens adicionados a um carrinho).

### Por que variáveis comuns não bastam?
- Em JavaScript tradicional, variáveis declaradas com `let` guardam valores em memória, mas **não solicitam ao React uma nova renderização** quando são alteradas;
- Cada vez que o componente precisa ser renderizado novamente, as variáveis locais declaradas em seu corpo são completamente reinicializadas;
- O `state` do React permite reter informações entre sucessivas renderizações e instrui o motor do React a atualizar a interface visual na tela sempre que seu valor é modificado.

```jsx
// Exemplo com variável comum: a tela NÃO atualiza ao clicar
function ContadorIncorreto() {
  let valor = 0;
  function incrementar() {
    valor = valor + 1; // Não dispara re-render
  }
  return <button onClick={incrementar}>Valor: {valor}</button>;
}
```

---

# 2. O que são Hooks no React?

**Hooks** são funções especiais introduzidas no React que permitem aos componentes funcionais conectar-se aos recursos de estado e ciclo de vida da biblioteca.

### Regras fundamentais dos Hooks:
- O nome de todo Hook inicia obrigatoriamente com o prefixo `use` (ex.: `useState`, `useEffect`, `useParams`);
- Devem ser chamados **apenas no nível superior (*top level*)** do componente funcional ou de um Custom Hook personalizado;
- **Não** devem ser chamados dentro de laços (`for`, `while`), estruturas condicionais (`if/else`) ou funções aninhadas, preservando a ordem estável de execução mantida pelo React.

### Utilizando o Hook `useState`:
O `useState` recebe um valor inicial e retorna um array com exatamente dois elementos:
1. O valor atual do estado;
2. Uma função modificadora responsável por atualizar esse valor e solicitar uma nova renderização.

```jsx
import { useState } from "react";

function Contador() {
  const [contador, setContador] = useState(0);

  return (
    <section>
      <p>Valor: {contador}</p>
      <button onClick={() => setContador(contador + 1)}>
        Incrementar
      </button>
    </section>
  );
}
```

---

# 3. Formulários e Campos Controlados

Formulários são essenciais para receber entradas e interações do usuário, viabilizando autenticação, cadastros, buscas e preferências.

### O Padrão de Campos Controlados (*Controlled Components*):
Em React, um campo é denominado **controlado** quando seu valor na tela é governado diretamente pelo estado do componente:
- A propriedade `value` do elemento HTML reflete o valor atual do estado;
- O evento `onChange` detecta a digitação do usuário e dispara a função atualizadora do estado com `e.target.value`;
- O fluxo opera em ciclo contínuo: **Digitação $\rightarrow$ Evento `onChange` $\rightarrow$ Atualização do Estado $\rightarrow$ Re-renderização com o novo `value`**.

```jsx
import { useState } from "react";

function CampoNome() {
  const [nome, setNome] = useState("");

  return (
    <label>
      Nome:
      <input
        type="text"
        value={nome}
        onChange={(e) => setNome(e.target.value)}
      />
    </label>
  );
}
```

### Submissão de Formulários e `e.preventDefault()`:
O envio de um formulário dispara o evento `onSubmit`. Nos navegadores, o comportamento padrão ao submeter é recarregar a página inteira ou realizar uma requisição HTTP tradicional.

Para evitar o recarregamento em Single-Page Applications (SPAs) e permitir que o React processe a validação e o envio dos dados em segundo plano, utiliza-se obrigatoriamente o método `e.preventDefault()`:

```jsx
function FormularioCadastro() {
  function enviar(e) {
    e.preventDefault(); // Impede o recarregamento da página
    alert("Formulário validado e enviado com sucesso!");
  }

  return (
    <form onSubmit={enviar}>
      <button type="submit">Enviar</button>
    </form>
  );
}
```

---

# 4. Sincronização de Efeitos Colaterais com `useEffect`

Nem todas as operações em uma aplicação dizem respeito exclusivamente a desenhar elementos na tela. Operações que interagem com sistemas externos ao React são denominadas **efeitos colaterais (*side effects*)**.

### Exemplos comuns de efeitos colaterais:
- Alterar o título da aba do navegador (`document.title`);
- Registrar e remover listeners globais na janela (`window.addEventListener`);
- Disparar temporizadores (`setTimeout`, `setInterval`);
- Realizar requisições HTTP para consultar dados de APIs remotas.

### Estrutura do Hook `useEffect`:
O `useEffect` aceita dois argumentos: uma função contendo a lógica do efeito e um array de dependências que dita quando ele deve ser reexecutado.

```jsx
import { useEffect } from "react";

// Sincronizando o título da aba com uma prop
function Pagina({ titulo }) {
  useEffect(() => {
    document.title = titulo;
  }, [titulo]); // Executa sempre que a prop 'titulo' mudar
}
```

### O Array de Dependências:
- **Sem array (`useEffect(fn)`):** O efeito roda após **toda e qualquer** renderização;
- **Array vazio (`useEffect(fn, [])`):** O efeito roda **somente uma vez**, logo após o componente ser montado na tela;
- **Com dependências (`useEffect(fn, [valor])`):** O efeito roda na montagem e é recalculado somente quando alguma das variáveis listadas sofrer alteração.

### Função de Limpeza (*Cleanup Function*):
Alguns efeitos configuram recursos que precisam ser descartados quando o componente é desmontado ou antes de o efeito rodar novamente, evitando vazamentos de memória (*memory leaks*):

```jsx
useEffect(() => {
  function atualizar() {
    console.log("Janela redimensionada");
  }

  window.addEventListener("resize", atualizar);

  // Retorno da função de limpeza
  return () => {
    window.removeEventListener("resize", atualizar);
  };
}, []);
```

---

# 5. Consumo de APIs REST no React

Uma **API (Application Programming Interface)** possibilita que a aplicação Front-end se comunique de forma padronizada com servidores remotos e serviços Web para consumir ou persistir dados.

### A Função `fetch()` e Assincronismo:
O JavaScript moderno utiliza a função global `fetch()` em conjunto com a sintaxe `async/await` para gerenciar requisições assíncronas:

```jsx
import { useState, useEffect } from "react";

function ListaPublicacoes() {
  const [publicacoes, setPublicacoes] = useState([]);

  useEffect(() => {
    async function carregar() {
      try {
        const resposta = await fetch("https://jsonplaceholder.typicode.com/posts");
        if (!resposta.ok) {
          throw new Error("Erro ao buscar publicações");
        }
        const dados = await resposta.json();
        setPublicacoes(dados);
      } catch (erro) {
        console.error(erro);
      }
    }

    carregar();
  }, []); // Executa apenas na montagem

  return (
    <ul>
      {publicacoes.map((item) => (
        <li key={item.id}>{item.title}</li>
      ))}
    </ul>
  );
}
```

### Envio de Dados com Método POST:
Para cadastrar informações na API, utiliza-se o método POST, especificando os cabeçalhos (`Content-Type: application/json`) e transformando o objeto JavaScript em texto JSON através de `JSON.stringify()`:

```javascript
await fetch("/api/publicacoes", {
  method: "POST",
  headers: {
    "Content-Type": "application/json"
  },
  body: JSON.stringify({ title: "Aprendendo React" })
});
```

### Boas Práticas e Cuidados no Consumo de APIs:
- Tratar cenários de falha de conexão e status HTTP de erro (`response.ok`);
- Exibir mensagens claras ao usuário para estados de carregamento, listas vazias e falhas;
- Manter o array de dependências do `useEffect` configurado corretamente para evitar loops infinitos de requisições;
- Jamais expor credenciais secretas, tokens privados ou chaves de serviço no código cliente exposto no navegador;
- Atentar-se a restrições de CORS e limites de requisições (*rate limits*).

---

# 6. Roteamento Client-Side com React Router

Em Single-Page Applications (SPAs), todas as transições de tela ocorrem no navegador do cliente sem requisições de recarregamento completo da página ao servidor. O **React Router** (`react-router-dom`) é a biblioteca padrão utilizada para associar caminhos de URL aos componentes da aplicação.

### Vantagens do Roteamento:
- Permite criar experiências ricas com múltiplas páginas (Início, Catálogo, Sobre, Detalhes);
- Habilita suporte ao histórico do navegador (botões voltar e avançar);
- Permite compartilhamento direto de links específicos para determinadas telas.

### Componentes Fundamentais da Biblioteca `react-router-dom`:
- `BrowserRouter`: Componente provedor que envolve a aplicação e sincroniza a interface com a URL do navegador via HTML5 History API;
- `Routes`: Contêiner que agrupa todas as rotas declaradas;
- `Route`: Declara o mapeamento entre o caminho da URL (`path`) e o componente que deve ser renderizado (`element`);
- `Link`: Substitui a tag tradicional `<a>`, interceptando o clique e alterando a URL internamente sem disparar reload completo da página.

```jsx
import { BrowserRouter, Routes, Route, Link } from "react-router-dom";

function App() {
  return (
    <BrowserRouter>
      <nav>
        <Link to="/">Início</Link>
        <Link to="/sobre">Sobre</Link>
      </nav>

      <Routes>
        <Route path="/" element={<Inicio />} />
        <Route path="/sobre" element={<Sobre />} />
      </Routes>
    </BrowserRouter>
  );
}
```

### Rotas Dinâmicas e o Hook `useParams`:
Para páginas que dependem de identificadores dinâmicos na URL (ex.: detalhes de um produto ou artigo específico), definem-se parâmetros com dois pontos (`:id`):

```jsx
// Declaração da rota dinâmica:
<Route path="/conceitos/:id" element={<DetalhesConceito />} />

// No componente DetalhesConceito:
import { useParams } from "react-router-dom";

function DetalhesConceito() {
  const { id } = useParams(); // Captura o parâmetro da URL

  return <h1>Visualizando Conceito ID: {id}</h1>;
}
```

---

# 7. Atividade Prática da Aula

A atividade prática estabelece a criação de uma aplicação React consolidando os tópicos ministrados:
- Gerenciamento de estado local com `useState`;
- Desenvolvimento de formulários com campos controlados e validação preventiva com `e.preventDefault()`;
- Execução de requisições assíncronas a uma API REST dentro de `useEffect` com tratamento de erros;
- Navegação entre múltiplas páginas e rotas parametrizadas com `react-router-dom` e `useParams`;
- Publicação de repositório público no GitHub com documentação no `README.md` relatando funcionalidades, arquitetura e conceitos aplicados.

---

# 8. Referências Bibliográficas

1. SOUZA, Natan. **Bootstrap 4: conheça a biblioteca front-end mais utilizada no mundo.** São Paulo: Casa do Código, 2018. E-book. Disponível em: https://plataforma.bvirtual.com.br.
2. MACHADO, Kheronn Khennedy. **Angular 11 e Firebase: construindo uma aplicação integrada com a plataforma do Google.** São Paulo: Casa do Código, 2021.
3. EIS, Diego. **Guia Front-end: o caminho das pedras para ser um dev front-end.** São Paulo: Casa do Código, 2015.
4. GONÇALVES, Edson. **Desenvolvendo aplicações Web com JSP, Servlets, JavaServer Faces, Hibernate, EJB 3 Persistence e Ajax.** Rio de Janeiro: Ciência Moderna, 2007.
5. HARTCOPP, Patrícia Ferreira. **Métrica Web.** São Paulo: Contentus, 2020.
6. NIEDERAUER, Juliano. **Desenvolvendo Websites com PHP: aprenda a criar Websites dinâmicos e interativos com PHP e banco de dados.** 3. ed. São Paulo: Novatec, 2017.
7. PREECE, J.; ROGERS, Y.; SHARP, H. **Design de Interação: além da interação Homem-Computador.** 3. ed. Porto Alegre: Bookman, 2013.
8. SOUSA, Roque Fernando Marcos. **Canvas HTML 5: composição gráfica e interatividade na Web.** Rio de Janeiro: Brasport, 2014.
