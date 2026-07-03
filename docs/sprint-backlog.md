# Backlog da Sprint 1 — FeriasFlow

Fonte em markdown para transcricao no Jira (gera `sprint-backlog.pdf`).
Todos os itens selecionados atendem ao **Definition of Ready** do backlog do produto.

---

## Meta da Sprint (Sprint Goal)

> **Ao final da Sprint 1, uma colaboradora consegue entrar no sistema, ver seu saldo e
> solicitar ferias, acompanhando o status do pedido** — a Jornada A completa, de ponta a ponta.

Racional: fatia vertical de valor (colaborador atendido por inteiro) em vez de camadas tecnicas
soltas. A jornada critica do gestor (calendario + decisao + notificacoes) e a meta planejada da
Sprint 2, quando a base de autenticacao, cadastro e pedidos ja existira.

## Capacidade e premissas

- Sprint de 2 semanas (10 dias uteis); time de 5 (2 devs full-time; PO, SM e UX de apoio).
- **Sem historico de velocidade** (primeira sprint): dimensionamento cauteloso de
  **~23 story points**, a calibrar na revisao/retrospectiva. Referencia de estimativa:
  US03 (CRUD basico) = 3 SP; escala 1-2-3-5-8-13 via planning poker.
- O enabler EN01 consome parte relevante da capacidade — esperado em sprint inaugural.

## Itens selecionados (23 SP)

| Item | Descricao curta | SP | Feature / Epico |
|------|-----------------|:--:|-----------------|
| EN01 | Enabler — setup do projeto (repo, SPA+API+banco, pipeline, modelo de dados) | 5 | E1 MVP |
| US01 | Login com e-mail e senha | 3 | F1 / E1 |
| US02 | Acesso por papel (colaborador, gestor) | 3 | F1 / E1 |
| US03 | Cadastro de colaborador + saldo (gestor) — referencia CRUD | 3 | F2 / E1 |
| US04 | Colaboradora ve o saldo | 2 | F2 / E1 |
| US05 | Solicitar ferias pelo calendario | 5 | F3 / E1 |
| US06 | Acompanhar status dos pedidos | 2 | F3 / E1 |

Burndown alvo: 23 SP -> 0 em 10 dias uteis; acompanhamento no board do Jira.

---

## Detalhamento dos itens

### EN01 — Setup do projeto — 5 SP

Tarefas: criar repositorio e pipeline de build/teste; esqueleto SPA + API REST + banco;
autenticacao base (sessao/token); modelo de dados inicial (colaborador, saldo, pedido);
ambiente de teste.

Aceite do enabler: pipeline verde; aplicacao "ola mundo" autenticavel publicada em ambiente
de teste; modelo de dados criado por migracao reproduzivel.

### US01 — Login — 3 SP

Como **colaboradora (Carla)**, quero **entrar no sistema com e-mail e senha**, para **acessar
minhas informacoes de ferias com seguranca**.

- Dado que informo e-mail e senha validos, quando confirmo o login, entao acesso minha area com
  meu nome e papel exibidos.
- Dado que informo credenciais invalidas, quando confirmo o login, entao vejo mensagem de erro
  clara e permaneco na tela de login (sem indicar qual campo errou).

Tarefas: tela de login (wireframe W1); endpoint de autenticacao; sessao com expiracao;
mensagens de erro; testes.

### US02 — Acesso por papel — 3 SP

Como **gestor (Gustavo)**, quero **que cada pessoa acesse apenas as funcoes do seu papel**, para
**proteger dados da equipe e simplificar a experiencia**.

- Dado que estou autenticado como colaborador, quando acesso o sistema, entao vejo apenas minhas
  proprias informacoes e acoes.
- Dado que estou autenticado como colaborador, quando tento acessar rota de gestor, entao recebo
  acesso negado.
- Dado que estou autenticado como gestor, quando acesso o sistema, entao vejo as funcoes de
  equipe (cadastro, calendario, decisao).

Tarefas: middleware de autorizacao por papel; menus condicionais; testes de acesso negado.

### US03 — Cadastro de colaborador + saldo — 3 SP (referencia)

Como **gestor (Gustavo)**, quero **cadastrar, editar e remover colaboradores com saldo de dias**,
para **ter a base da equipe pronta para pedidos e decisoes**.

- Dado que preencho nome, e-mail e saldo validos, quando salvo, entao o colaborador aparece na
  lista da equipe com o saldo informado.
- Dado que deixo campo obrigatorio vazio ou saldo negativo, quando tento salvar, entao o sistema
  aponta o campo invalido e nada e gravado.
- Dado que removo colaborador com pedidos vinculados, quando confirmo, entao ele e inativado
  (nao excluido).

Tarefas: tela de equipe (wireframe W4); CRUD API; validacoes; testes.

### US04 — Ver saldo — 2 SP

Como **colaboradora (Carla)**, quero **ver meu saldo de dias atualizado**, para **planejar meu
pedido sem perguntar ao RH**.

- Dado que estou autenticada, quando abro minha area, entao vejo o saldo atual e a data da
  ultima atualizacao.
- Dado que tenho pedido aprovado, quando consulto o saldo, entao os dias ja aparecem descontados.
- **RNF (ISO 25010 — eficiencia de desempenho):** dado acesso em rede tipica, quando abro minha
  area, entao o saldo e exibido em ate 2 segundos.

Tarefas: card de saldo na home (wireframe W2); endpoint de saldo; teste de desempenho simples.

### US05 — Solicitar ferias — 5 SP

Como **colaboradora (Carla)**, quero **solicitar ferias escolhendo o periodo em um calendario**,
para **formalizar meu pedido em minutos e sem e-mail**.

- Dado que escolho periodo dentro do saldo, quando envio, entao o pedido e criado "Pendente" com
  resumo (dias, saldo restante projetado).
- Dado que escolho periodo maior que o saldo, quando tento enviar, entao o sistema bloqueia e
  informa o saldo disponivel.
- Dado que escolho inicio no passado, quando tento enviar, entao o sistema bloqueia com mensagem
  clara.

Tarefas: tela de solicitacao com seletor de periodo (wireframe W3); validacoes de negocio;
persistencia do pedido; testes.

### US06 — Acompanhar status — 2 SP

Como **colaboradora (Carla)**, quero **acompanhar o status dos meus pedidos**, para **saber a
decisao sem "ficar no vacuo"**.

- Dado que tenho pedidos, quando abro "Meus pedidos", entao vejo periodo, dias e status de cada um.
- Dado que um pedido foi reprovado, quando abro os detalhes, entao vejo a justificativa do gestor.
- Dado que nao tenho pedidos, quando abro "Meus pedidos", entao vejo o estado vazio com orientacao.

Tarefas: lista "Meus pedidos" (wireframe W2/W5); endpoint de listagem; estados visuais; testes.

---

## Wireframes da Sprint 1 (entregavel Figma)

| Cod | Tela | Historias atendidas |
|-----|------|---------------------|
| W1 | Login | US01 |
| W2 | Home da colaboradora (saldo + meus pedidos) | US04, US06 |
| W3 | Solicitar ferias (seletor de periodo + resumo) | US05 |
| W4 | Equipe do gestor (lista + cadastro de colaborador) | US03, US02 |
| W5 | Detalhe do pedido (status + justificativa) | US06 |

## DoR / DoD

Aplicam-se o Definition of Ready e o Definition of Done registrados no backlog do produto
(`product-backlog.md`), incluindo os RNFs transversais (desempenho, seguranca, usabilidade
responsiva, compatibilidade) que valem para todo item desta sprint.
