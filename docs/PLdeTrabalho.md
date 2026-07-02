# Plano de Trabalho — MVP II (Gestao Agil de Projetos e Produtos)

**Pos-Graduacao em Engenharia de Software — PUC-Rio**
**Sprint: Gestao Agil de Projetos e Produtos**
**Produto escolhido:** FeriasFlow — app de gestao de ferias de equipe

---

## 0. Natureza da entrega

Este MVP e de **ideacao e planejamento** — nao ha software rodando. A tarefa cruza tres
disciplinas (Engenharia de Requisitos, Gestao Agil, Design/Prototipacao de UI) e produz os
artefatos de concepcao de um produto de software de livre escolha.

### Entregaveis e nota (10 pts)

| # | Entregavel | Ferramenta | Arquivo no repo | Pts |
|---|-----------|-----------|-----------------|-----|
| 1 | Lean Inception completa + MVP Canvas | Miro | `canvas-url.txt` | 3,0 |
| 2 | Backlog do Produto + DoR + DoD (>=1 requisito nao funcional) | Jira | `product-backlog.pdf` | 1,5 |
| 3 | Backlog da Sprint 1 (story points + criterios de aceitacao) | Jira | `sprint-backlog.pdf` | 1,5 |
| 4 | Wireframes (baixa fidelidade) | Figma | `wireframes/` | 2,0 |
| 5 | Video showcase 2-4 min | qualquer | raiz ou URL | 2,0 |

Capricho visual, organizacao e clareza dos documentos contam na nota.

### Estrutura do repositorio publico (GitHub org FSEB-SW)

```
ferias-flow-mvp/            <- repo publico
├── canvas-url.txt          # URL do board Miro
├── product-backlog.pdf     # export legivel do Jira
├── sprint-backlog.pdf      # export legivel do Jira
├── wireframes/             # PNGs exportados do Figma
├── video.mp4 (ou URL no README)
└── README.md
```

---

## 1. Contexto de negocio (cenario hipotetico)

### 1.1 O produto

**FeriasFlow** — aplicacao web para **planejamento e aprovacao de ferias de equipes**, com foco
em equilibrar tres tensoes que hoje vivem espalhadas em planilhas, e-mails e sistemas de RH
burocraticos:

1. **Saldo e legalidade** — cada colaborador tem um saldo de dias e regras da CLT (periodo
   aquisitivo, antecedencia minima, fracionamento em ate 3 periodos).
2. **Cobertura da operacao** — o gestor nao pode deixar a equipe descoberta; precisa enxergar
   conflitos (varios pedidos sobrepostos, papeis-chave ausentes ao mesmo tempo).
3. **Visibilidade** — RH/DP precisa fechar com a folha; a diretoria quer a visao agregada.

**Problema central:** o gestor decide ferias no escuro — sem ver saldo, sobreposicao e cobertura
no mesmo lugar. O FeriasFlow centraliza pedido, saldo, calendario de equipe e aprovacao num unico
fluxo.

**Dor de origem (real):** deriva da rotina de gestao de ferias de equipe do proprio autor
(gestor de departamento tecnico), o que torna a ideacao autentica e as dores conhecidas.

### 1.2 Stakeholders, usuarios e clientes

| Papel | Tipo | Interesse / o que espera do produto |
|-------|------|-------------------------------------|
| **Colaborador** | Usuario | Solicitar ferias sem burocracia, ver saldo e status do pedido em tempo real. |
| **Gestor de equipe** | Usuario principal + cliente | Planejar e aprovar ferias vendo saldo, sobreposicao e cobertura da equipe. E quem sente a dor e "compra" a solucao. |
| **RH / Departamento Pessoal** | Usuario secundario + stakeholder | Validar saldo legal (CLT), fechar com a folha de pagamento, garantir compliance. |
| **Diretoria** | Stakeholder | Visao agregada de ferias por area; nao opera o sistema, consome relatorio. |
| **Sponsor (Diretor de Operacoes / RH)** | Stakeholder | Patrocina e paga o produto; quer reducao de retrabalho e risco trabalhista. |
| **Time de produto (PO/SM/Devs/UX)** | Executor | Entregar o MVP enxuto, com qualidade, no menor tempo. |

> Cliente = quem paga (empresa, via Sponsor). Usuario = quem opera (colaborador, gestor, RH).
> O gestor de equipe acumula os dois papeis no cenario de PME.

### 1.3 Time Scrum (enxuto)

Equipe minima para executar o MVP com qualidade em tempo razoavel — **5 pessoas**:

| Papel | Qtd | Habilidades |
|-------|-----|-------------|
| **Product Owner** | 1 | Visao de produto, priorizacao de backlog, dominio do negocio de RH/gestao de pessoas, interlocucao com stakeholders. |
| **Scrum Master** | 1 (part-time, acumula com QA) | Facilitacao agil, remocao de impedimentos, metricas de fluxo; apoia testes/qualidade. |
| **Desenvolvedor Full-stack A** | 1 | Front-end (SPA), integracao com API, foco em UI de calendario/aprovacao. |
| **Desenvolvedor Full-stack B** | 1 | Back-end (API REST, banco), regras de saldo/CLT, autenticacao e perfis. |
| **UX/UI Designer** | 1 (part-time) | Pesquisa com usuarios, wireframes, prototipacao no Figma, design system minimo. |

Racional da equipe enxuta: 2 devs full-stack cobrem front+back com redundancia de conhecimento;
o SM acumula QA porque o escopo do MVP e pequeno; o designer entra part-time (concentrado nas
sprints iniciais de descoberta e prototipacao). PO dedicado por ser o elo com todos os
stakeholders mapeados.

---

## 2. Roteiro de execucao (ordem de dependencias)

1. [x] Contexto de negocio (este documento)
2. [ ] **Lean Inception no Miro** (todas as etapas) -> desemboca no **MVP Canvas**
3. [ ] **Backlog do Produto** (epicos -> features -> historias + enablers) + DoR + DoD -> Jira -> `product-backlog.pdf`
4. [ ] **Sprint 1** (subconjunto que atende o DoR; story points + criterios de aceitacao) -> Jira -> `sprint-backlog.pdf`
5. [ ] **Wireframes** das telas da Sprint 1 -> Figma -> `wireframes/`
6. [ ] **Video** showcase 2-4 min
7. [ ] Publicar repo publico e testar acesso; postar URL no forum

### Metodo de trabalho

Para cada artefato de ferramenta externa (Miro, Jira, Figma), o conteudo intelectual e escrito
primeiro como **fonte em markdown** neste `apoio/`. A transcricao para a ferramenta vira passo
mecanico e garante consistencia entre os artefatos (as features do Canvas = os epicos do backlog
= as telas do Figma).

### Contas necessarias

- **Miro** free — copia do template Lean Inception (Miroverse, ingles gratuito; preenchivel em PT).
- **Jira** free (Software, ate 10 usuarios).
- **Figma** free.
- **GitHub** — org `FSEB-SW` (mesmo destino da Sprint 1 / SGI BIM), usuario `jfcs-engsw`.
