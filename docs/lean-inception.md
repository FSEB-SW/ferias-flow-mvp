# Lean Inception — FeriasFlow

Fonte em markdown para transcricao no Miro (template Lean Inception do Miroverse).
Sequencia de atividades conforme Paulo Caroli. Cada secao vira um quadro no board.

---

## Atividade 1 — Visao do produto (elevator pitch)

> **Para** gestores de equipes e seus colaboradores
> **cujo** planejamento de ferias hoje e feito no escuro, espalhado em planilhas e e-mails,
> **o FeriasFlow** e uma aplicacao web de gestao de ferias
> **que** centraliza pedido, saldo, calendario da equipe e aprovacao num unico fluxo, mostrando
> sobreposicao e cobertura antes da decisao.
> **Diferente de** planilhas manuais e do modulo burocratico do sistema de RH,
> **o nosso produto** dá ao gestor uma decisao informada em segundos e ao colaborador transparencia
> de saldo e status em tempo real.

---

## Atividade 2 — E / Nao e / Faz / Nao faz

| E | NAO E |
|---|-------|
| Um planejador visual de ferias de equipe | Um sistema de folha de pagamento |
| Uma ferramenta de decisao para o gestor | Um ponto eletronico / controle de jornada |
| Um registro do saldo e do status do pedido | Um ERP de RH completo |
| Um app web responsivo | Um app mobile nativo (nesta fase) |

| FAZ | NAO FAZ |
|-----|---------|
| Registra pedidos de ferias e saldo | Calcula folha / provisiona 1/3 de ferias |
| Mostra calendario da equipe com sobreposicao | Integra com eSocial (fora do MVP) |
| Aprova/reprova com trilha de decisao | Gerencia banco de horas ou licencas medicas |
| Notifica mudancas de status | Substitui a homologacao juridica das ferias |

---

## Atividade 3 — Objetivos do produto

1. **Reduzir o tempo de decisao** do gestor sobre um pedido de ferias (de horas/dias para minutos).
2. **Eliminar conflitos de cobertura** — nenhuma aprovacao que deixe a equipe descoberta.
3. **Dar transparencia** de saldo e status ao colaborador, reduzindo idas ao RH.
4. **Reduzir risco trabalhista** garantindo antecedencia e saldo validos.
5. **Validar a hipotese de negocio:** existe disposicao a pagar por uma camada leve de decisao
   sobre ferias, separada do ERP de RH.

---

## Atividade 4 — Personas

### Persona 1 — Carla, a Colaboradora
- **Cargo:** analista de uma equipe tecnica.
- **Objetivo:** pedir ferias no periodo que quer, saber o saldo e ser avisada da decisao rapido.
- **Dor:** hoje manda e-mail e "fica no vacuo"; nao sabe o saldo exato.
- **Tech:** confortavel com apps web; usa mais celular que desktop.

### Persona 2 — Gustavo, o Gestor de Equipe (persona principal)
- **Cargo:** coordenador de ~8 pessoas.
- **Objetivo:** aprovar ferias sem descobrir a operacao; planejar o ano da equipe.
- **Dor:** decide no escuro; descobre sobreposicao tarde; retrabalho com o RH.
- **Tech:** intermediario; quer poucos cliques e visao de calendario.

### Persona 3 — Renata, o RH / DP
- **Cargo:** analista de departamento pessoal.
- **Objetivo:** garantir saldo e regras da CLT; fechar com a folha sem surpresa.
- **Dor:** recebe pedidos incompletos/fora do prazo; concilia planilhas manualmente.
- **Tech:** avancado em sistemas de RH; valoriza consistencia de dados.

### Persona 4 — Diretor Paulo (stakeholder, nao operador)
- **Objetivo:** visao agregada de ferias por area, sem operar o sistema.
- **Dor:** falta de visibilidade consolidada em periodos criticos (fim de ano).

---

## Atividade 5 — Jornadas do usuario

### Jornada A — Colaborador solicita ferias (Carla)
1. Acessa o app e ve seu saldo de dias.
2. Escolhe periodo desejado no calendario.
3. Envia o pedido.
4. Recebe notificacao quando o gestor decide.
5. Consulta o historico/status a qualquer momento.

### Jornada B — Gestor decide (Gustavo) — jornada critica do MVP
1. Recebe notificacao de novo pedido.
2. Abre o calendario da equipe e ve o pedido sobreposto aos demais.
3. Enxerga saldo do colaborador e alertas de sobreposicao/cobertura.
4. Aprova ou reprova (com justificativa).
5. O colaborador e notificado automaticamente.

### Jornada C — RH valida (Renata)
1. Ve a fila de pedidos aprovados pelo gestor.
2. Confere saldo/CLT (antecedencia, fracionamento).
3. Confirma ou devolve com apontamento.

---

## Atividade 6 — Brainstorm de features

1. Autenticacao e perfis (colaborador, gestor, RH, diretoria)
2. Cadastro de colaboradores e saldo de dias
3. Solicitacao de ferias (colaborador)
4. Calendario/visao de equipe com sobreposicao
5. Aprovacao/reprovacao pelo gestor (com justificativa)
6. Notificacoes de status (pedido, aprovacao, reprovacao)
7. Deteccao automatica de conflito de cobertura (regra de cobertura minima)
8. Validacao de saldo e regras da CLT (RH)
9. Fila de validacao do RH
10. Relatorio/dashboard agregado (diretoria)
11. Fracionamento CLT (ate 3 periodos) e periodo aquisitivo
12. Exportacao para a folha de pagamento
13. Historico de ferias por colaborador
14. Log de auditoria das decisoes

---

## Atividade 7 — Revisao das features (esforco x valor de negocio x UX)

Escala: A (baixo) a C (alto) para Esforco; 1 (baixo) a 3 (alto) para Valor.

| # | Feature | Esforco | Valor | UX | Onda |
|---|---------|:-------:|:-----:|:--:|------|
| 1 | Auth e perfis (colaborador+gestor) | B | 3 | media | MVP |
| 2 | Cadastro de colaborador + saldo | B | 3 | media | MVP |
| 3 | Solicitacao de ferias | A | 3 | alta | MVP |
| 4 | Calendario de equipe c/ sobreposicao | B | 3 | alta | MVP |
| 5 | Aprovacao/reprovacao (gestor) | A | 3 | alta | MVP |
| 6 | Notificacoes de status | B | 2 | media | MVP |
| 7 | Deteccao de conflito de cobertura | C | 3 | alta | Inc. 1 |
| 8 | Validacao saldo/CLT (RH) | C | 3 | media | Inc. 1 |
| 9 | Fila de validacao do RH | B | 2 | media | Inc. 1 |
| 10 | Dashboard agregado (diretoria) | B | 2 | media | Inc. 1 |
| 11 | Fracionamento CLT + aquisitivo | C | 2 | media | Inc. 2 |
| 12 | Export para folha | B | 2 | baixa | Inc. 2 |
| 13 | Historico por colaborador | A | 1 | baixa | Inc. 2 |
| 14 | Log de auditoria | B | 1 | baixa | Inc. 2 |

---

## Atividade 8 — Sequenciador (ondas)

**Onda 1 — MVP** (valida a hipotese central: gestor decide com visao de saldo + sobreposicao)
- Auth e perfis (colaborador + gestor)
- Cadastro de colaborador + saldo
- Solicitacao de ferias
- Calendario de equipe com sobreposicao
- Aprovacao/reprovacao pelo gestor
- Notificacoes de status

**Onda 2 — Incremento 1** (fecha o ciclo com RH e cobertura)
- Deteccao de conflito de cobertura
- Validacao saldo/CLT + fila do RH
- Dashboard agregado (diretoria)

**Onda 3 — Incremento 2** (compliance e integracao)
- Fracionamento CLT + periodo aquisitivo
- Export para folha
- Historico e log de auditoria

---

## Atividade 9 — MVP Canvas

**Nome do MVP:** FeriasFlow — decisao de ferias com visao de equipe

| Bloco | Conteudo |
|-------|----------|
| **1. Proposta do MVP (visao)** | Permitir que o gestor aprove/reprove ferias enxergando saldo e sobreposicao da equipe no mesmo lugar, e que o colaborador acompanhe saldo e status. |
| **2. Personas (segmento)** | Gustavo (gestor — principal), Carla (colaboradora). RH e diretoria entram no Inc. 1. |
| **3. Jornadas** | A) Colaborador solicita ferias; B) Gestor decide vendo sobreposicao (jornada critica). |
| **4. Proposta de valor** | Decisao informada em minutos; zero aprovacao que descubra a equipe; transparencia de saldo/status. |
| **5. Features** | Auth+perfis, cadastro+saldo, solicitacao, calendario com sobreposicao, aprovacao/reprovacao, notificacoes. |
| **6. Custo & Cronograma** | Time de 5 pessoas; ~3 sprints de 2 semanas para o MVP (estimativa da Onda 1). |
| **7. Metricas p/ validar hipoteses** | Tempo medio de decisao por pedido; % de pedidos sem conflito de cobertura; % de colaboradores que consultam saldo sem acionar o RH; NPS do gestor. |
| **8. Resultado esperado (aprendizado)** | Confirmar se a camada leve de decisao reduz tempo e retrabalho o suficiente para justificar evoluir (Inc. 1) e cobrar pelo produto. |
