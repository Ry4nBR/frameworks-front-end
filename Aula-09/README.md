# Aula 09 - Projeto React 02

## Sobre a aula

Nona aula da disciplina de Frameworks Front-end, voltada ao desenvolvimento avançado de aplicações com React, introduzindo o gerenciamento de estado interno, controle de formulários, sincronização de efeitos colaterais com o ecossistema externo, consumo de APIs assíncronas e roteamento client-side com React Router.

Foram aprofundados os conceitos de Estado e Hooks funcionais, com destaque para a diferença entre variáveis comuns e o `useState`, compreendendo como as alterações de estado disparam o ciclo de renderização do componente. Em formulários, explorou-se o padrão de campos controlados (*controlled components*), captura de digitação via `onChange`, tratamento de submissão via `onSubmit` e prevenção de reload da página com `e.preventDefault()`.

A aula também explorou o Hook `useEffect` para sincronização com sistemas externos, ciclo de vida, lista de dependências e função de limpeza (*cleanup*). Abordou-se o consumo de APIs REST utilizando `fetch()`, tratamento de erros com `try/catch`, status HTTP, requisições GET e POST, cuidados com CORS e segurança. Por fim, apresentou-se a biblioteca `react-router-dom` para navegação multi-páginas via URLs, componentes `BrowserRouter`, `Routes`, `Route`, links sem recarregamento com `Link` e captura dinâmica de parâmetros com `useParams()`.

## Conteúdos

- Gerenciamento de Estado no React:
  - O que é State e limitações de variáveis locais convencionais
  - Conceito e regras de Hooks funcionais
  - Hook `useState`: inicialização, leitura e função de atualização
- Formulários e Campos Controlados:
  - Associação de `value` ao estado e detecção de digitação com `onChange`
  - Submissão com `onSubmit` e controle de eventos com `e.preventDefault()`
  - Validação de entrada de dados e mensagens de confirmação
- Efeitos Colaterais com `useEffect`:
  - Sincronização do componente com recursos externos (título da aba, listeners de janela)
  - Lista de dependências e controle do ciclo de execução
  - Função de retorno para limpeza de efeitos (*cleanup*)
- Consumo de APIs REST com React:
  - Requisições assíncronas com `fetch()`, `async/await` e manipulação de JSON
  - Ciclo de busca de dados no `useEffect` com array de dependências vazio (`[]`)
  - Métodos HTTP (GET para consulta e POST com `headers` e `JSON.stringify()`)
  - Tratamento de status de resposta (`response.ok`), erros com `try/catch`, estados de carregamento e boas práticas de segurança
- Navegação e Roteamento com React Router (`react-router-dom`):
  - Por que utilizar roteamento *client-side* em SPAs
  - Estrutura com `BrowserRouter`, `Routes` e `Route`
  - Navegação fluida sem recarregar a página com o componente `Link`
  - Rotas dinâmicas e captura de parâmetros da URL com o hook `useParams()`
- Atividade Prática

## Material da aula

[Visualizar PDF da aula](./Aula-09.pdf)

## Resumo

O resumo completo do conteúdo apresentado está disponível em:

[Resumo da Aula 09](./Resumo.md)

## Atividade

A atividade prática consiste no desenvolvimento e publicação de uma aplicação completa em React reunindo todos os tópicos abordados:

1. Gerenciamento dinâmico de estado com `useState`;
2. Criação de formulários estruturados com campos controlados e validação no envio;
3. Sincronização de efeitos externos e busca de dados em API REST com `useEffect` e `fetch()`, contemplando tratamento de erros e estados de carregamento;
4. Estruturação da navegação entre múltiplas páginas e rotas parametrizadas com `react-router-dom` (`BrowserRouter`, `Routes`, `Route`, `Link`, `useParams`);
5. Publicação em repositório público no GitHub com documentação em `README.md` contendo a visão geral do projeto, funcionalidades construídas e conceitos de React aplicados.

### Repositórios e materiais complementares de referência

- Repositório de conceitos: [https://github.com/deivisontakatu/aula-react](https://github.com/deivisontakatu/aula-react)
- Repositório do projeto de exemplo: [https://github.com/deivisontakatu/projeto-react](https://github.com/deivisontakatu/projeto-react)
- Aplicação de exemplo em produção: [https://projeto-react-five-swart.vercel.app/](https://projeto-react-five-swart.vercel.app/)
- API de testes utilizada nos exemplos: [https://jsonplaceholder.typicode.com/](https://jsonplaceholder.typicode.com/)
