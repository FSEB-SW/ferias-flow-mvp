# Backlog do Produto — FeriasFlow

Fonte em markdown para transcricao no Jira (gera `product-backlog.pdf`).
Derivacao direta da Lean Inception: **epicos = ondas do Sequenciador**; **features = features
do MVP Canvas**; historias no formato "Como / Quero / Para" com identificador [USnn].

> **Backlog emergente:** apenas o epico MVP (topo da prioridade) esta refinado em historias
> com criterios de aceitacao. Os epicos Incremento 1 e 2 permanecem no nivel de feature, a
> refinar quando se aproximarem do topo — o detalhamento e proporcional a prioridade.

---

## Visao geral (hierarquia)

```
E1  MVP (Onda 1)                          <- refinado em historias
├── EN01 Enabler — Setup do projeto
├── F1  Autenticacao e perfis             US01, US02
├── F2  Cadastro de colaborador e saldo   US03, US04
├── F3  Solicitacao de ferias             US05, US06
├── F4  Calendario de equipe              US07
├── F5  Decisao do gestor                 US08, US09
└── F6  Notificacoes de status            US10, US11

E2  Incremento 1 (Onda 2)                 <- nivel de feature (a refinar)
├── F7  Deteccao de conflito de cobertura
├── F8  Validacao de saldo e regras CLT (RH)
├── F9  Fila de validacao do RH
└── F10 Dashboard agregado (diretoria)

E3  Incremento 2 (Onda 3)                 <- nivel de feature (a refinar)
├── F11 Fracionamento CLT e periodo aquisitivo
├── F12 Exportacao para a folha
├── F13 Historico por colaborador
└── F14 Log de auditoria
```

Prioridade: E1 > E2 > E3; dentro do E1, ordem EN01 -> F1 -> F2 -> F3 -> F4 -> F5 -> F6
(dependencia tecnica e de valor: sem auth nao ha perfis; sem cadastro nao ha saldo; a jornada
do colaborador precede a decisao do gestor).

---

## Epico E1 — MVP (Onda 1)

**Objetivo do epico:** validar a hipotese central — o gestor decide ferias com visao de saldo e
sobreposicao, e o colaborador acompanha saldo e status sem acionar o RH.

### EN01 — Enabler tecnico: setup do projeto — 5 SP

Preparacao que habilita as historias de usuario (nao entrega valor direto ao usuario, por isso
e enabler e nao historia): repositorio, esqueleto front (SPA) + API + banco, autenticacao base,
pipeline de build/teste, modelo de dados inicial (colaborador, saldo, pedido).

### F1 — Autenticacao e perfis

**[US01] — 3 SP — Sprint 1**
Como **colaboradora (Carla)**, quero **entrar no sistema com e-mail e senha**, para **acessar
minhas informacoes de ferias com seguranca**.

- Criterios de aceitacao:
  - Dado que informo e-mail e senha validos, quando confirmo o login, entao acesso minha area
    com meu nome e papel exibidos.
  - Dado que informo credenciais invalidas, quando confirmo o login, entao vejo mensagem de
    erro clara e permaneco na tela de login (sem indicar qual campo errou).
- Descricao complementar: sessao expira por inatividade; senha armazenada com hash
  (ver DoD — seguranca).

**[US02] — 3 SP — Sprint 1**
Como **gestor (Gustavo)**, quero **que cada pessoa acesse apenas as funcoes do seu papel
(colaborador, gestor)**, para **proteger dados da equipe e simplificar a experiencia de cada um**.

- Criterios de aceitacao:
  - Dado que estou autenticado como colaborador, quando acesso o sistema, entao vejo apenas
    minhas proprias informacoes e acoes (saldo, pedidos).
  - Dado que estou autenticado como colaborador, quando tento acessar uma rota de gestor
    (ex.: cadastro de equipe), entao recebo acesso negado.
  - Dado que estou autenticado como gestor, quando acesso o sistema, entao vejo as funcoes de
    equipe (cadastro, calendario, decisao).
- Descricao complementar: papeis do MVP = colaborador e gestor; RH e diretoria entram no Inc. 1.

### F2 — Cadastro de colaborador e saldo

**[US03] — 3 SP — Sprint 1 — HISTORIA DE REFERENCIA (CRUD basico = 3 SP)**
Como **gestor (Gustavo)**, quero **cadastrar, editar e remover colaboradores da minha equipe com
seu saldo de dias de ferias**, para **ter a base da equipe pronta para pedidos e decisoes**.

- Criterios de aceitacao:
  - Dado que preencho nome, e-mail e saldo inicial validos, quando salvo, entao o colaborador
    aparece na lista da equipe com o saldo informado.
  - Dado que deixo um campo obrigatorio vazio ou saldo negativo, quando tento salvar, entao o
    sistema aponta o campo invalido e nada e gravado.
  - Dado que removo um colaborador sem pedidos vinculados, quando confirmo, entao ele sai da
    lista; com pedidos vinculados, o sistema pede confirmacao e inativa em vez de excluir.
- Descricao complementar: e a referencia de estimativa do time (CRUD basico = 3 SP), usada
  como ancora no planning poker.

**[US04] — 2 SP — Sprint 1**
Como **colaboradora (Carla)**, quero **ver meu saldo de dias atualizado**, para **planejar meu
pedido sem precisar perguntar ao RH**.

- Criterios de aceitacao:
  - Dado que estou autenticada, quando abro minha area, entao vejo o saldo atual de dias e a
    data da ultima atualizacao.
  - Dado que tenho um pedido aprovado, quando consulto o saldo, entao os dias aprovados ja
    aparecem descontados.
  - **RNF (ISO 25010 — eficiencia de desempenho):** dado o acesso em rede domestica tipica,
    quando abro minha area, entao o saldo e exibido em ate 2 segundos.

### F3 — Solicitacao de ferias

**[US05] — 5 SP — Sprint 1**
Como **colaboradora (Carla)**, quero **solicitar ferias escolhendo o periodo em um calendario**,
para **formalizar meu pedido em minutos e sem e-mail**.

- Criterios de aceitacao:
  - Dado que escolho um periodo dentro do meu saldo, quando envio o pedido, entao ele e criado
    com status "Pendente" e o resumo (dias, saldo restante projetado) e exibido.
  - Dado que escolho um periodo maior que meu saldo, quando tento enviar, entao o sistema
    bloqueia e informa o saldo disponivel.
  - Dado que escolho data de inicio no passado, quando tento enviar, entao o sistema bloqueia
    com mensagem clara.
- Descricao complementar: fracionamento CLT completo fica no Inc. 2; no MVP, 1 periodo por pedido.

**[US06] — 2 SP — Sprint 1**
Como **colaboradora (Carla)**, quero **acompanhar o status dos meus pedidos (pendente, aprovado,
reprovado)**, para **saber a decisao sem "ficar no vacuo"**.

- Criterios de aceitacao:
  - Dado que tenho pedidos registrados, quando abro "Meus pedidos", entao vejo a lista com
    periodo, dias e status atual de cada um.
  - Dado que um pedido foi reprovado, quando abro seus detalhes, entao vejo a justificativa
    do gestor.
  - Dado que nao tenho pedidos, quando abro "Meus pedidos", entao vejo orientacao para criar
    o primeiro pedido (estado vazio).

### F4 — Calendario de equipe

**[US07] — 8 SP — Sprint 2 (planejada)**
Como **gestor (Gustavo)**, quero **ver os pedidos e ferias da equipe em um calendario com
sobreposicoes destacadas**, para **enxergar conflitos antes de decidir**.

- Criterios de aceitacao (alto nivel; refinar no planejamento da Sprint 2):
  - Dado que ha pedidos em periodos coincidentes, quando abro o calendario, entao os periodos
    sobrepostos aparecem destacados.
  - Dado que filtro por mes, quando navego, entao pedidos pendentes e ferias aprovadas se
    distinguem visualmente.

### F5 — Decisao do gestor

**[US08] — 5 SP — Sprint 2 (planejada)**
Como **gestor (Gustavo)**, quero **aprovar ou reprovar um pedido com justificativa**, para
**registrar a decisao com transparencia**.

**[US09] — 3 SP — Sprint 2 (planejada)**
Como **gestor (Gustavo)**, quero **ver saldo do solicitante e alertas de sobreposicao dentro do
proprio pedido**, para **decidir informado sem sair da tela**.

### F6 — Notificacoes de status

**[US10] — 3 SP — Sprint 2 (planejada)**
Como **colaboradora (Carla)**, quero **ser notificada quando meu pedido for decidido**, para
**saber o resultado imediatamente**.

**[US11] — 2 SP — Sprint 2 (planejada)**
Como **gestor (Gustavo)**, quero **ser notificado quando chegar um novo pedido**, para **nao
atrasar a decisao**.

---

## Epico E2 — Incremento 1 (Onda 2) — nivel de feature

Fecha o ciclo com RH e cobertura. A refinar quando o MVP validar a hipotese central.

- **F7 — Deteccao de conflito de cobertura:** regra de cobertura minima por equipe/papel;
  bloqueio ou alerta forte na decisao.
- **F8 — Validacao de saldo e regras CLT (RH):** antecedencia minima, periodo aquisitivo.
- **F9 — Fila de validacao do RH:** pedidos aprovados pelo gestor aguardam confirmacao do RH.
- **F10 — Dashboard agregado (diretoria):** visao consolidada por area/periodo.

## Epico E3 — Incremento 2 (Onda 3) — nivel de feature

Compliance e integracao.

- **F11 — Fracionamento CLT (ate 3 periodos) e periodo aquisitivo.**
- **F12 — Exportacao para a folha de pagamento.**
- **F13 — Historico de ferias por colaborador.**
- **F14 — Log de auditoria das decisoes.**

---

## Definition of Ready (DoR)

Um item so entra em sprint quando:

1. Esta vinculado a um epico e a uma feature.
2. Tem descricao complementar suficiente (campos, regras, validacoes; referencia ao wireframe
   quando houver tela).
3. Tem criterios de aceitacao definidos no formato "Dado / Quando / Entao", cobrindo caso
   positivo e negativo.
4. Foi estimado em story points pela equipe (planning poker, escala 1-2-3-5-8-13, referencia
   US03 = 3 SP).
5. E pequeno o suficiente para caber na sprint (INVEST).

## Definition of Done (DoD)

Um item so e aceito como concluido quando:

1. Codigo revisado por outro dev (revisao aos pares) e build sem warnings.
2. Testes unitarios das regras de negocio passando.
3. Todos os criterios de aceitacao verificados em ambiente de teste.
4. **RNFs transversais atendidos (ISO 25010):**
   - **Eficiencia de desempenho:** paginas principais respondem em ate 2 s em rede tipica.
   - **Seguranca (confidencialidade):** acesso restrito por papel; senhas com hash; dados de
     ferias visiveis apenas a quem de direito.
   - **Usabilidade:** interface responsiva (desktop e mobile — persona Carla usa celular).
   - **Compatibilidade:** funciona nas versoes atuais de Chrome, Edge e Firefox.
5. Validado pelo PO (criterios + jornada da persona).
6. Documentacao curta atualizada (README do modulo / changelog).
