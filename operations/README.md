# operations/ — Manual Operacional

**STATUS:** Oficial (meta-documento de processo operacional)

## O que é este diretório

`operations/` é a camada de trabalho do sistema multiagente da VYO — onde missões pontuais (algo como "estruture o CRM da VYO Menu", "monte o calendário editorial" ou "analise essa ideia") são abertas, executadas por Claude, auditadas pelo GPT, e fechadas.

Diferença central em relação a `docs/`:

| | `operations/` | `docs/` |
|---|---|---|
| Natureza | Trabalho em andamento — o processo de executar uma missão | Conhecimento consolidado — o que a VYO sabe/decidiu, de forma durável |
| Conteúdo | Missões: objetivo, plano, execução, ciclos de revisão, auditoria | Marca, produto, preço, mercado, jurídico, metas, governança |
| Ciclo de vida | Nasce, é executada, é auditada, é arquivada em `completed/` | É atualizado quando uma decisão muda; não "termina" |
| Quem decide o que entra | Claude executa o que a missão pede | GPT decide o que da missão é promovido para cá (ver "Memória do sistema" abaixo) |

Ver [`mission-template.md`](mission-template.md) para a estrutura de cada missão, e [`NEXT-MISSION.md`](NEXT-MISSION.md) para o estado atual.

## Identificador de missão

Padrão: **`VYO-YYYY-NNN`** (ano de abertura da missão + número sequencial de 3 dígitos, ex.: `VYO-2026-001`, `VYO-2026-002`, ...).

- IDs são atribuídos em ordem, por ano, pelo GPT, ao transformar um pedido de Nathan em `MISSION READY`.
- **IDs nunca podem ser reutilizados** — mesmo que uma missão seja cancelada ou rejeitada, seu ID fica "queimado" e não volta a ser usado por outra missão.

## Ciclo automático

```
ENTRADA HUMANA
  ↓
GPT ORQUESTRADOR        (interpreta o pedido, cria a missão a partir de mission-template.md,
  ↓                       atribui ID, define nível de autonomia — ver abaixo)
MISSION READY
  ↓
CLAUDE EXECUTOR          (executa, preenche o SELF-CHECK — ver "Controle de qualidade" — e entrega)
  ↓
REVIEW_GPT               (GPT audita a entrega contra objetivo e critérios de sucesso)
  ↓
aprovado?
  ↓            ↓
 não           sim
  ↓            ↓
REVISION      APPROVED
  ↓
CLAUDE        (corrige e reentrega)
  ↓
REVIEW_GPT
  ↓
  ...
  ↓
DONE
```

### Limite de ciclos autônomos

```
MAX_AUTONOMOUS_CYCLES = 5
```

Um "ciclo" é uma volta completa `CLAUDE EXECUTOR → REVIEW_GPT → REVISION` sem chegar a `APPROVED`. **O loop não pode ser infinito.** Depois de 5 ciclos sem aprovação, a missão muda de estado automaticamente para:

```
HUMAN_REVIEW_REQUIRED
```

Nesse ponto, Nathan recebe um resumo contendo, obrigatoriamente:

- **Objetivo** original da missão;
- **Problema** — o que está impedindo a aprovação;
- **Tentativas realizadas** — o que foi feito em cada um dos ciclos;
- **Discordância ou bloqueio** — onde GPT e Claude divergem, ou o que trava o avanço;
- **Opções existentes** — caminhos possíveis para Nathan escolher.

A missão fica parada em `HUMAN_REVIEW_REQUIRED` até Nathan decidir como prosseguir (continuar, redirecionar, ou encerrar a missão).

## Níveis de autonomia

Toda missão nasce com um nível de autonomia, definido pelo GPT ao criá-la. **Nathan pode alterar o nível por missão**, a qualquer momento.

| Nível | Nome | Como funciona |
|---|---|---|
| **A1** | Assistido | A IA propõe; o humano aprova **antes** da execução. Nenhuma ação é tomada sem esse aval prévio. |
| **A2** | Supervisionado | O GPT pode mandar Claude executar e revisar automaticamente (o ciclo `CLAUDE ↔ REVIEW_GPT` roda sem parar a cada passo). Decisões críticas (ver lista abaixo) ainda param para o humano. |
| **A3** | Autônomo | GPT e Claude podem iterar livremente até a Definition of Done, sem checkpoint intermediário do humano — dentro do limite de `MAX_AUTONOMOUS_CYCLES`. |

### O que sempre para em `HUMAN_DECISION_REQUIRED`, mesmo em A3

Independentemente do nível de autonomia da missão, os itens abaixo **nunca** são decididos ou executados por GPT/Claude sozinhos:

- preço final;
- contrato;
- posicionamento oficial;
- gasto financeiro;
- ação jurídica;
- credenciais/permissões;
- publicação externa irreversível.

Qualquer missão que esbarre em um desses itens muda de estado para `HUMAN_DECISION_REQUIRED`, independentemente do nível de autonomia configurado — consistente com a regra de decisões críticas em [`../AGENTS.md`](../AGENTS.md).

## Memória do sistema — o que vira `docs/`

`operations/` é trabalho; `docs/` é conhecimento consolidado. **Nem tudo que uma missão produz deve entrar em `docs/`.**

Ao finalizar uma missão (chegar a `APPROVED`/`DONE`), o GPT decide:

- **PROMOVER PARA DOCS** — quando a missão gerou conhecimento estratégico durável (uma decisão, um fato novo confirmado, uma mudança de posicionamento aprovada) que deveria estar na base consolidada, não só no histórico da missão.
- **NÃO PROMOVER** — quando o resultado é operacional/pontual (uma peça produzida, uma tarefa executada) sem impacto na base de conhecimento.

**Claude só executa a promoção depois da decisão do GPT** — nunca promove conteúdo de `operations/` para `docs/` por conta própria. Isso evita transformar o repositório em depósito de conversas, mantendo `docs/` como a camada que reflete o que a VYO sabe, não tudo que foi feito.

Ao ser fechada, a missão é movida de `operations/active/` para `operations/completed/`, com o campo "Conhecimento gerado" do template preenchido — inclusive quando a decisão foi "não promover" (registrar essa decisão também é rastreabilidade, ver [`../docs/10-fontes-e-rastreabilidade.md`](../docs/10-fontes-e-rastreabilidade.md)).

## Controle de qualidade — SELF-CHECK

Antes de qualquer entrega ir para `REVIEW_GPT`, Claude preenche este checklist e o anexa à entrega, na seção "Execução Claude" do template de missão:

```
SELF-CHECK
[ ] executei exatamente o escopo?
[ ] consultei as fontes autorizadas?
[ ] criei alguma inferência?
[ ] marquei as inferências?
[ ] alterei algo fora do escopo?
[ ] existem decisões humanas?
[ ] existem erros/testes falhando?
[ ] consigo provar o que alterei?
```

Uma entrega sem SELF-CHECK anexado não deve ser considerada pronta para auditoria.

## Segurança operacional

Nenhum agente (GPT ou Claude) pode, em nenhuma missão e em nenhum nível de autonomia:

- apagar histórico estratégico sem autorização;
- sobrescrever decisão humana silenciosamente;
- transformar hipótese em decisão;
- divulgar credenciais;
- realizar gasto;
- assinar contrato;
- representar aprovação de Nathan/Xande;
- fazer merge de decisão crítica sem a aprovação necessária.

Essas restrições valem mesmo em missões A3 (autônomas) — autonomia de execução não é autonomia sobre decisões críticas ou sobre a integridade do histórico.

## Ver também

- [`mission-template.md`](mission-template.md) — estrutura de cada missão.
- [`NEXT-MISSION.md`](NEXT-MISSION.md) — estado atual da fila de missões.
- [`../AGENTS.md`](../AGENTS.md) — regras gerais do repositório e papéis do protocolo multiagente.
- [`../docs/11-protocolo-multiagente.md`](../docs/11-protocolo-multiagente.md) — protocolo institucional (Nathan/Xande/GPT/Claude), do qual este manual operacional é a aplicação prática para missões.
- [`../docs/10-fontes-e-rastreabilidade.md`](../docs/10-fontes-e-rastreabilidade.md) — tags de rastreabilidade, usadas também dentro de cada missão.
