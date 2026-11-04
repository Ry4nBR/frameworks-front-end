# Resumo - Aula 07: Frameworks CSS

## 1. Introdução ao CSS (Cascading Style Sheets)

O **CSS (Cascading Style Sheets)** é a linguagem responsável por definir a camada visual e de apresentação dos documentos HTML na Web.

Ele não se limita apenas a definir cores e fontes, mas também controla:
- Margens e espaçamentos internos;
- Alinhamentos e distribuições de elementos;
- Larguras, alturas e dimensões de componentes;
- Elementos flutuantes e posicionamentos específicos;
- Layouts organizados, fluidos e responsivos.

Com o uso adequado de suas propriedades, é possível unir estética, acessibilidade e funcionalidade, garantindo interfaces consistentes em diferentes navegadores e dispositivos.

---

# 2. Sintaxe e Estrutura Básica do CSS

O CSS é estruturado através da seguinte regra fundamental:

```css
seletor {
  propriedade: valor;
}
```

- **Seletor:** Identifica qual elemento (tag HTML, classe ou ID) receberá o conjunto de estilos;
- **Propriedade:** Especifica o atributo visual que será modificado (ex.: `background-color`, `font-size`, `margin`);
- **Valor:** Define a configuração atribuída à propriedade (ex.: `#FF0000`, `16px`, `center`).

### Comparação: HTML Clássico vs CSS Moderno

No HTML antigo, estilos eram frequentemente definidos por atributos na própria tag:
```html
<!-- Abordagem legada (HTML puro) -->
<body bgcolor="#FF0000">
```

No CSS, a estilização é desacoplada da marcação, promovendo flexibilidade e padronização:
```css
/* Abordagem moderna (CSS) */
body {
  background-color: #FF0000;
}
```

---

# 3. Formas de Aplicação do CSS

O CSS pode ser aplicado aos documentos HTML de três maneiras principais:

## 3.1 CSS In-line

Aplicado diretamente sobre o elemento HTML através do atributo global `style`:

```html
<p style="color: red; font-size: 20px;">Este é um texto em vermelho e maior</p>
```

- **Vantagens:** Aplicação rápida e imediata, sem necessidade de arquivos externos;
- **Desvantagens:** Dificulta a manutenção, gera duplicação de regras e polui o HTML;
- **Uso recomendado:** Testes rápidos, e-mails HTML ou ajustes estritamente pontuais.

## 3.2 CSS Interno

Inserido no próprio arquivo HTML, dentro da tag `<style>` contida na seção `<head>`:

```html
<head>
  <style>
    p {
      color: blue;
      font-size: 18px;
    }
  </style>
</head>
```

- **Vantagens:** Centraliza os estilos daquela página específica;
- **Desvantagens:** Não permite reaproveitamento entre diferentes páginas do projeto;
- **Uso recomendado:** Landing pages com arquivo único ou protótipos de página isolada.

## 3.3 CSS Externo

Escrito em um arquivo separado com extensão `.css` e vinculado ao documento HTML através da tag `<link>` no `<head>`:

```html
<head>
  <link rel="stylesheet" href="estilos.css">
</head>
```

- **Vantagens:** Separação total de responsabilidades, reutilização de estilos em múltiplas páginas, facilidade de manutenção e melhoria de desempenho por cache do navegador;
- **Uso recomendado:** **Padrão mais recomendado para todos os projetos de desenvolvimento Web.**

---

# 4. Propriedades Fundamentais do CSS

A aula revisou as propriedades essenciais mais empregadas no cotidiano do desenvolvimento Front-end:

### Cores e Tipografia
- `color`: Define a cor do texto do elemento (ex.: `color: #ff0000;` ou `color: red;`);
- `background-color`: Define a cor de fundo do elemento (ex.: `background-color: #0000ff;` ou `background-color: blue;`);
- `font-family`: Especifica a família tipográfica (ex.: `font-family: Arial, sans-serif;`);
- `font-size`: Controla a dimensão do texto em pixels, rems, ems, etc. (ex.: `font-size: 16px;`, `font-size: 1.2rem;`);
- `text-align`: Controla o alinhamento horizontal do texto no container (ex.: `text-align: center;`, `text-align: justify;`).

### Espaçamentos e Dimensões
- `margin`: Controla o espaçamento externo (fora das bordas), afastando o elemento de seus vizinhos. Pode ser uniforme (`margin: 20px;`) ou individual (`margin: 10px 5px 15px 20px;` - top, right, bottom, left);
- `padding`: Controla o preenchimento interno (entre o conteúdo e a borda). Pode ser uniforme (`padding: 15px;`) ou por eixos (`padding: 10px 20px;` - vertical, horizontal);
- `border`: Define espessura, estilo e cor da borda perimetral (ex.: `border: 2px solid black;`);
- `width` e `height`: Definem a largura e a altura do elemento (ex.: `width: 300px; height: 200px;`).

### Exibição e Posicionamento
- `display`: Determina a forma de renderização do elemento no fluxo da página (`block`, `inline`, `inline-block`, `flex`, `grid`, `none`);
- `position`: Especifica o método de posicionamento do elemento (`static`, `relative`, `absolute`, `fixed`, `sticky`);
- `top`, `right`, `bottom`, `left`: Coordenadas utilizadas com posicionamentos relativos, absolutos ou fixos para posicionar elementos com precisão cirúrgica.

---

# 5. Seletores: Classes (.class) vs IDs (#id)

O CSS utiliza seletores específicos para aplicar regras com diferentes níveis de escopo e especificidade:

### Classes (`.nome-classe`)
- Permitem aplicar o mesmo estilo a múltiplos elementos em uma ou mais páginas;
- Garantem reuso, consistência visual e facilidade de manutenção;
- Exemplo:
  ```css
  .botao-primario {
    background: blue;
    color: red;
    padding: 10px;
  }
  ```

### IDs (`#nome-id`)
- Devem ser únicos por documento HTML, identificando um elemento exclusivo;
- Utilizados para estilos de alta especificidade, âncoras de navegação (`#secao`) e manipulação direta via JavaScript (`document.getElementById`);
- Exemplo:
  ```css
  #cabecalho-principal {
    height: 80px;
    background: #333;
  }
  ```

---

# 6. Box Model (Modelo de Caixas)

O **Box Model** é o conceito estrutural fundamental do CSS que determina como todos os elementos HTML são interpretados visualmente pelo navegador como caixas retangulares.

### Componentes do Box Model

1. **Content (Conteúdo):** A área central onde residem textos, imagens, vídeos ou outros elementos filhos;
2. **Padding (Preenchimento Interno):** O espaço entre o conteúdo e a borda interna do elemento;
3. **Border (Borda):** A linha de contorno que envolve o padding e o conteúdo;
4. **Margin (Margem Externa):** O espaço vazio transparente que separa o elemento de outros elementos vizinhos no layout.

### Importância da aplicação do Box Model:
- Controle rigoroso das dimensões dos elementos;
- Criação de espaçamento uniforme e organização visual;
- Prevenção de quebras de layout e sobreposição indevida de elementos;
- Construção de interfaces previsíveis;
- Adaptação facilitada para diferentes tamanhos de viewport.

---

# 7. Flexbox (Flexible Box Layout)

O **Flexbox** é um módulo de layout unidimensional do CSS desenvolvido para distribuir espaços e alinhar itens eficientemente ao longo de uma linha ou coluna.

### Propriedades fundamentais do Flexbox:

- `display: flex`: Transforma o elemento pai em um flex container;
- `flex-direction`: Define a direção do eixo principal (`row`, `row-reverse`, `column`, `column-reverse`);
- `justify-content`: Controla o alinhamento dos itens ao longo do eixo principal (`flex-start`, `center`, `flex-end`, `space-between`, `space-around`, `space-evenly`);
- `align-items`: Controla o alinhamento dos itens no eixo transversal (`flex-start`, `center`, `flex-end`, `stretch`, `baseline`);
- `flex-wrap`: Define se os itens podem quebrar para a próxima linha (`nowrap`, `wrap`, `wrap-reverse`);
- `gap`: Define o espaçamento entre itens flexíveis de forma moderna e simplificada (sem necessidade de margens complexas nos filhos).

---

# 8. Layouts Responsivos

O design responsivo é a abordagem que permite que o conteúdo e os componentes de uma aplicação se adaptem visualmente de maneira fluida a qualquer tamanho de tela:
- Suporte a celulares, tablets, notebooks e monitores ultrawide;
- Aumento da usabilidade e melhoria substancial da experiência do usuário (UX);
- Eliminação da necessidade de desenvolver versões separadas do site para dispositivos móveis (ex.: subdomínios `m.site.com`).

---

# 9. O que é um Framework CSS?

Um **framework CSS** é um pacote estruturado de recursos, padrões, classes pré-programadas e componentes reutilizáveis projetado para acelerar e padronizar o desenvolvimento Front-end.

### Pilares de um Framework CSS:
- **Layout:** Sistemas de Grid, Flexbox e breakpoints responsivos;
- **Estilos Globais:** Paletas de cores harmônicas, espaçamentos padronizados e tipografia escalável;
- **Componentes:** Botões, cartões (*cards*), barras de navegação (*navbar*), modais e formulários.

### O Problema do CSS Tradicional (Manual):
No desenvolvimento CSS manual, cada elemento precisa ser construído do zero:
```html
<button class="botao">Enviar</button>
```
```css
.botao {
  background: #2563eb;
  color: white;
  padding: 12px 24px;
  border-radius: 8px;
}
```
Isso exige declarar regras repetitivas para botões, cards, formulários, grids e breakpoints, aumentando a probabilidade de inconsistências visuais e dificuldade de manutenção em equipes grandes.

---

# 10. Tailwind CSS e o Paradigma Utility-First

O **Tailwind CSS** é um framework moderno baseado primordialmente no conceito de **Utility-First**.

### O Conceito de Utility-First
Em vez de disponibilizar componentes monolíticos prontos com classes genéricas (como `.btn` ou `.card`), o Tailwind disponibiliza classes utilitárias atômicas de responsabilidade única:
- **Uma utility = uma responsabilidade única;**
- **Várias utilities combinadas = um componente personalizado.**

Exemplo:
```html
<!-- Componente construído combinando classes utilitárias -->
<button class="bg-blue-600 text-white px-6 py-3 rounded-lg font-bold">
  Enviar
</button>
```
Nesse exemplo:
- `bg-blue-600`: define a cor de fundo;
- `text-white`: define a cor do texto;
- `px-6 py-3`: define padding horizontal e vertical;
- `rounded-lg`: define bordas arredondadas;
- `font-bold`: define peso da fonte.

### Propósitos e Vantagens do Tailwind CSS:
1. **Redução no tempo de desenvolvimento:** Estilização direta na estrutura HTML sem necessidade de alternar constantemente entre arquivos `.css` e `.html`;
2. **Flexibilidade e originalidade:** Não impõe uma "cara de template pré-fabricado" ao projeto;
3. **Facilidade de customização:** Tokens de design centralizados para cores, tipografias e espaçamentos;
4. **Reutilização e consistência:** Elimina classes CSS órfãs e garante uso de valores padronizados de design system;
5. **Responsividade integrada:** Abordagem *Mobile First* nativa com prefixos simples (ex.: `md:flex`, `lg:grid-cols-3`).

---

# 11. Instalação e Configuração do Tailwind CSS

O Tailwind pode ser adicionado aos projetos através de duas formas principais:

## 11.1 Importação via Play CDN (Ideal para testes rápidos e aprendizado)
Inclusão direta no `<head>` do arquivo `index.html`:
```html
<script src="https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4"></script>
```

## 11.2 Instalação via Tailwind CLI e Ferramentas de Build (Recomendado para produção)
1. **Instalação dos pacotes via npm:**
   ```bash
   npm install tailwindcss @tailwindcss/cli
   ```
2. **Importação no arquivo CSS principal:**
   ```css
   @import "tailwindcss";
   ```
3. **Integração com PostCSS:**
   ```bash
   npm install tailwindcss @tailwindcss/postcss postcss
   ```
4. **Integração com frameworks:** O Tailwind possui guias específicos de integração para Next.js, Angular, Vite, Vue, Laravel e Astro.

## 11.3 Extensão Tailwind CSS IntelliSense
Ferramenta indispensável para editores como VS Code:
- Autocomplete de classes utilitárias;
- Visualização instantânea das propriedades CSS geradas em hover;
- Redução de erros de digitação e aumento da produtividade.

---

# 12. Atividades Práticas

### Atividade 01: CSS Clássico, Box Model e Flexbox
- Desenvolvimento com arquivos `index.html` e `style.css` externos;
- Implementação de 20 elementos manipulando todas as propriedades do Box Model (`content`, `padding`, `border`, `margin`);
- Emprego de 20 propriedades de Flexbox para alinhamento e distribuição responsiva dos elementos.

### Atividade 02: Interface com Tailwind CSS
- Construção de projeto Web empregando pelo menos 30 classes diferentes do Tailwind CSS;
- Abrangência de categorias: cores, tipografia, espaçamentos, dimensões, bordas, posicionamento, flexbox, grid e responsividade;
- Documentação completa em Markdown no GitHub com capturas de tela, listagem explicativa de classes e link do projeto online.

---

# 13. Referências Bibliográficas

1. SOUZA, Natan. **Bootstrap 4: conheça a biblioteca front-end mais utilizada no mundo.** São Paulo: Casa do Código, 2018. E-book. Disponível em: https://plataforma.bvirtual.com.br.
2. MACHADO, Kheronn Khennedy. **Angular 11 e Firebase: construindo uma aplicação integrada com a plataforma do Google.** São Paulo: Casa do Código, 2021.
3. EIS, Diego. **Guia Front-end: o caminho das pedras para ser um dev front-end.** São Paulo: Casa do Código, 2015.
4. GONÇALVES, Edson. **Desenvolvendo aplicações Web com JSP, Servlets, JavaServer Faces, Hibernate, EJB 3 Persistence e Ajax.** Rio de Janeiro: Ciência Moderna, 2007.
5. HARTCOPP, Patrícia Ferreira. **Métrica Web.** São Paulo: Contentus, 2020.
6. NIEDERAUER, Juliano. **Desenvolvendo Websites com PHP: aprenda a criar Websites dinâmicos e interativos com PHP e banco de dados.** 3. ed. São Paulo: Novatec, 2017.
7. PREECE, J.; ROGERS, Y.; SHARP, H. **Design de Interação: além da interação Homem-Computador.** 3. ed. Porto Alegre: Bookman, 2013.
8. SOUSA, Roque Fernando Marcos. **Canvas HTML 5: composição gráfica e interatividade na Web.** Rio de Janeiro: Brasport, 2014.
