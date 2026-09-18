# Aula 02 – Configuração do Ambiente de Desenvolvimento

## Objetivo da aula

A aula apresentou os principais conceitos relacionados à configuração do ambiente de desenvolvimento para aplicações Front-end. Foram abordados versionamento de código, Git, GitHub, Versionamento Semântico (SemVer), Visual Studio Code, Node.js, NPM, criação de projetos React e publicação de aplicações utilizando a plataforma Vercel. :contentReference[oaicite:0]{index=0}

---

# Versionamento de Código

O versionamento é um processo que registra todas as alterações realizadas em um projeto, permitindo acompanhar quem realizou cada modificação, quando ela ocorreu e qual foi seu objetivo.

Diferente de um backup, o versionamento mantém um histórico completo das alterações, facilita o trabalho em equipe e permite recuperar versões anteriores do projeto sempre que necessário. :contentReference[oaicite:1]{index=1}

### Benefícios do versionamento

- Histórico completo das alterações;
- Trabalho colaborativo entre desenvolvedores;
- Recuperação de versões anteriores;
- Auditoria e rastreabilidade;
- Redução de conflitos durante o desenvolvimento. :contentReference[oaicite:2]{index=2}

---

# Versionamento Semântico (SemVer)

O Versionamento Semântico é um padrão utilizado para identificar a evolução de um software através do formato:

**MAJOR.MINOR.PATCH**

Exemplos:

- **1.0.0** → primeira versão estável;
- **1.1.0** → nova funcionalidade compatível;
- **1.1.1** → correção de bugs;
- **2.0.0** → mudança incompatível com versões anteriores. :contentReference[oaicite:3]{index=3}

Esse padrão facilita a compreensão das mudanças realizadas e auxilia no gerenciamento de dependências entre projetos.

---

# Git e GitHub

O Git é um sistema de controle de versão instalado localmente no computador. Ele registra todas as alterações do projeto e permite sincronizar o código com repositórios remotos, como o GitHub. :contentReference[oaicite:4]{index=4}

Durante a aula foi demonstrado como:

- instalar o Git;
- verificar a instalação com `git --version`;
- configurar usuário e e-mail;
- integrar o Git ao Visual Studio Code. :contentReference[oaicite:5]{index=5}

---

# Tags e boas práticas no Git

As **Tags** são utilizadas para marcar versões importantes do software, como releases ou versões estáveis.

Exemplos:

- `git tag 1.0.0`
- `git push origin 1.0.0`

Também foram apresentadas boas práticas de versionamento, como:

- realizar commits pequenos e frequentes;
- escrever mensagens de commit claras;
- utilizar branches para novas funcionalidades;
- testar o código antes de realizar merge. :contentReference[oaicite:6]{index=6}

---

# Visual Studio Code

O Visual Studio Code foi apresentado como o ambiente de desenvolvimento utilizado durante a disciplina.

Embora seja um editor de código, ele pode funcionar como um IDE completo através da instalação de extensões e ferramentas adicionais. :contentReference[oaicite:7]{index=7}

---

# Node.js e NPM

O Node.js permite executar JavaScript fora do navegador, possibilitando o desenvolvimento de aplicações no servidor.

Junto com ele é instalado automaticamente o **NPM (Node Package Manager)**, responsável pelo gerenciamento das dependências do projeto através do arquivo `package.json`. :contentReference[oaicite:8]{index=8}

---

# Criação de um Projeto React

Foi demonstrado o processo de criação de uma aplicação React utilizando o comando:

```bash
npx create-react-app meu-projeto-react
```

Em seguida foram apresentados os principais comandos para iniciar o projeto:

```bash
cd meu-projeto-react

code .

npm start
```

Também foi explicada a estrutura básica criada automaticamente pelo React:

- `src/`
- `public/`
- `node_modules/`
- `.gitignore`
- `package.json`
- `package-lock.json` :contentReference[oaicite:9]{index=9}

---

# Deploy com Vercel

A plataforma Vercel foi apresentada como solução para hospedagem de aplicações Front-end.

Entre suas principais características estão:

- integração automática com GitHub;
- deploy a cada novo push;
- hospedagem gratuita para projetos pessoais;
- CDN global;
- alta performance e escalabilidade. :contentReference[oaicite:10]{index=10}

---

# Atividade da aula

Como atividade prática, foi solicitado o desenvolvimento de uma aplicação React utilizando o Visual Studio Code.

Após a implementação, o projeto deveria:

1. ser versionado com Git;
2. ser enviado para um repositório no GitHub;
3. ser publicado na plataforma Vercel;
4. ficar disponível através de uma URL pública. :contentReference[oaicite:11]{index=11}

---

# Principais conceitos aprendidos

- Controle de versão.
- Git e GitHub.
- Versionamento Semântico (SemVer).
- Tags e branches.
- Visual Studio Code.
- Node.js.
- NPM.
- React.
- Estrutura inicial de um projeto React.
- Deploy utilizando Vercel.

---

# Conclusão

A segunda aula apresentou toda a infraestrutura necessária para o desenvolvimento de aplicações Front-end. Além da instalação das ferramentas utilizadas durante a disciplina, foram introduzidas boas práticas de versionamento com Git, organização de projetos em React e publicação de aplicações na Web utilizando a plataforma Vercel. Esses conhecimentos servirão como base para o desenvolvimento dos projetos ao longo do semestre.