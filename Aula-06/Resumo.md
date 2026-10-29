# Resumo - Aula 06: Projetos Front-End

## 1. Por que gerenciar um projeto Front-End?

Aplicações Front-End modernas envolvem múltiplos componentes, estados complexos, integrações com serviços remotos e evolução frequente de layout. À medida que um projeto cresce, a ausência de processos estruturados de planejamento pode acarretar sérios problemas para a equipe:

### Problemas comuns em projetos sem gestão:
- **Tarefas esquecidas:** Falta de registro centralizado das funcionalidades a serem desenvolvidas;
- **Requisitos confusos:** Escopo mal definido que gera interpretações divergentes entre desenvolvedores;
- **Retrabalho:** Necessidade frequente de reescrever código devido a desalinhamento de expectativas;
- **Conflitos no Git:** Múltiplos integrantes alterando simultaneamente os mesmos arquivos sem branch strategy definida;
- **Atrasos e problemas de integração:** Dificuldade em unificar componentes e telas desenvolvidos isoladamente;
- **Dificuldade de acompanhamento:** Falta de visibilidade clara sobre o progresso real da aplicação.

---

# 2. Benefícios da Gestão de Projetos Front-End

Ao adotar um processo formal de gestão, a equipe passa a atuar de maneira colaborativa e previsível:

- **Responsabilidades claras:** Cada membro sabe exatamente qual módulo ou componente está sob sua responsabilidade;
- **Prioridades definidas:** O esforço inicial é concentrado nas funcionalidades que entregam maior valor para o usuário;
- **Entregas incrementais:** A aplicação é construída e validada em pequenos blocos funcionais;
- **Acompanhamento contínuo:** Visibilidade do fluxo de trabalho e identificação precoce de impedimentos;
- **Redução de retrabalho:** Menor incidência de refatorações corretivas graças ao alinhamento prévio dos requisitos.

Gerenciar projetos Front-End significa organizar harmonicamente **pessoas**, **tarefas**, **tecnologias** e **prazos**, transformando uma ideia abstrata em um produto digital funcional e escalável.

---

# 3. Gestão de Requisitos

Todo projeto de software nasce de uma ideia ou necessidade que precisa ser refinada antes de se iniciar a codificação:

```bash
Ideia  ──►  Requisitos Claros  ──►  Backlog  ──►  Priorização  ──►  Desenvolvimento  ──►  Testes e Entrega
```

### Decomposição: Requisito, User Story e Tarefa

Para facilitar a implementação em times ágeis, os requisitos são decompostos em diferentes níveis de granularidade:

1. **Requisito (Visão do Sistema):**
   - Especifica a capacidade que o sistema deve fornecer em alto nível.
   - *Exemplo:* "O sistema deve permitir gerenciamento de tarefas."

2. **User Story / História de Usuário (Visão de Valor do Usuário):**
   - Descreve a funcionalidade a partir da perspectiva de quem a utiliza, destacando o benefício esperado.
   - *Exemplo:* "Como usuário, quero criar uma tarefa."

3. **Tarefas / Tasks (Visão Técnica do Desenvolvedor):**
   - Etapas práticas e executáveis necessárias para construir a funcionalidade.
   - *Exemplos:*
     - Criar formulário na interface;
     - Criar componente reutilizável;
     - Validar campos de entrada;
     - Integrar com a API backend;
     - Criar testes automatizados.

---

# 4. Gestão do Backlog

O **Backlog** é uma lista viva e ordenada de todas as funcionalidades, melhorias técnicas, refatorações e correções de bugs necessárias para o desenvolvimento e evolução do produto.

### Boas práticas para manutenção do Backlog:
- **Priorização contínua:** Os itens do topo devem representar o trabalho imediato de maior valor agregado;
- **Refinamento periódico:** Detalhamento progressivo das tarefas conforme se aproximam do momento de execução;
- **Transparência:** Acessível a toda a equipe técnica e partes interessadas.

---

# 5. Gestão de Prioridade e Estimativa

### Priorização
Ajuda a equipe a responder a pergunta: *"O que deve ser desenvolvido primeiro?"*
A ordenação dos itens considera os objetivos do negócio, dependências técnicas, restrições de prazo e impacto para a experiência do usuário.

### Estimativa
As estimativas permitem que a equipe compreenda a complexidade relativa de cada funcionalidade antes de se comprometer com sua entrega. No desenvolvimento ágil, as estimativas auxiliam no dimensionamento adequado da carga de trabalho para evitar sobrecarga e atrasos na equipe.

---

# 6. Definition of Done (DoD)

A **Definition of Done (Definição de Concluído)** estabelece um conjunto de critérios objetivos e padronizados que devem ser atendidos antes que uma tarefa seja considerada efetivamente finalizada dentro do projeto.

Ter critérios claros evita que tarefas parcialmente prontas sejam movidas prematuramente para o estado de concluído.

### Exemplos de critérios que compõem a DoD no Front-End:
- Código implementado e aderente ao padrão da aplicação;
- Testes unitários ou manuais realizados com sucesso;
- Revisão de código (*Code Review*) aprovada por pares;
- Responsividade verificada em diferentes resoluções (Mobile, Tablet e Desktop);
- Integração funcional com os endpoints da API concluída;
- Build de produção gerado sem avisos ou erros críticos;
- Código versionado com commit padronizado e merge na branch principal.

---

# 7. Framework Ágil Scrum no Desenvolvimento Front-End

O **Scrum** é um framework ágil amplamente utilizado para desenvolver produtos complexos por meio de ciclos iterativos e incrementais. Seus pilares fundamentais são a **transparência**, a **inspeção** e a **adaptação**.

### Aplicação prática no Front-End:
- **Sprints:** Ciclos fixos de desenvolvimento (geralmente de 1 a 2 semanas) com escopo fechado;
- **Sprint Planning:** Reunião inicial para selecionar os itens do Backlog que serão implementados no ciclo;
- **Acompanhamento com Kanban:** Utilização de quadros visuais (*To Do*, *In Progress*, *Review*, *Done*) para gerenciar o fluxo das tarefas;
- **Branch Strategy:** Criação de branches separadas no Git por funcionalidade (*feature branches*), facilitando a integração isolada e prevenindo conflitos no código principal.

---

# 8. Repositórios Complementares de Referência

A aula recomendou três repositórios desenvolvidos pelo professor para aprofundamento nos temas de engenharia de software e processos ágeis:

- **Gestão de Projetos:** [https://github.com/deivisontakatu/aula-gestao](https://github.com/deivisontakatu/aula-gestao)
- **Gestão de Produto:** [https://github.com/deivisontakatu/aula-gestao-produto](https://github.com/deivisontakatu/aula-gestao-produto)
- **Scrum:** [https://github.com/deivisontakatu/aula-scrum](https://github.com/deivisontakatu/aula-scrum)

---

# 9. Atividade Prática

A atividade proposta visa a aplicação direta das técnicas ágeis no Projeto Integrador Interdisciplinar (PII):

1. **Planejamento da Gestão:** Estruturar o fluxo de trabalho da equipe para as entregas de Front-End;
2. **Construção dos Artefatos:**
   - Elaboração do Backlog inicial de funcionalidades;
   - Definição de prioridades e atribuição de estimativas relativas;
   - Decomposição das histórias em tarefas técnicas de codificação e integração;
   - Planejamento da Sprint e configuração de quadro Kanban;
   - Definição da estratégia de branches no Git e da Definition of Done (DoD);
3. **Documentação e Acompanhamento:** Registro de todo o planejamento em documento Markdown e utilização do quadro configurado para gerenciar o andamento do projeto.

---

# 10. Resumo Geral

A Aula 06 abordou a importância crítica da gestão estruturada no desenvolvimento de aplicações Front-End. Foram discutidas as consequências da falta de planejamento e demonstrado como metodologias ágeis trazem previsibilidade e qualidade às entregas.

A aula explorou em detalhe a hierarquia de requisitos (**Requisito > User Story > Tarefa**), a priorização do Backlog, técnicas de estimativa e o papel da **Definition of Done** na garantia da qualidade técnica. Por fim, conectou o framework **Scrum** e ferramentas visuais ao planejamento prático das etapas do Projeto Integrador Interdisciplinar.

---

**Fonte:** material da Aula 06, que aborda gestão de projetos Front-End, requisitos, backlog, prioridades, estimativas, Definition of Done, Scrum e atividade prática.
