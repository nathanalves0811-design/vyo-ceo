# Protocolo Multiagente

**STATUS:** Oficial (meta-documento de processo)

Este documento define o fluxo de trabalho entre os quatro papéis envolvidos na manutenção deste repositório, e os estados que uma tarefa percorre entre ser levantada e ser considerada concluída.

## Papéis

| Papel | Natureza | Responsabilidade |
|---|---|---|
| **Nathan** | Humano — CEO / autoridade de direção | Decide, junto com Xande, tudo que for decisão crítica; decide sozinho o que estiver sob sua alçada individual |
| **Xande** | Humano — sócio / autoridade em decisões conjuntas | Mesma autoridade que Nathan nas decisões que exigem os dois |
| **GPT** | Orquestrador + Auditor | Analisa contexto, define tarefas, detecta inconsistências, audita entregas, emite nova ordem, determina se os critérios de conclusão foram atingidos |
| **Claude** | Executor | Pesquisa fontes autorizadas, edita arquivos, implementa alterações, executa tarefas, reporta exatamente o que foi alterado, declara inferências e limitações |

## Fluxo

```
Nathan
  ↓
GPT — ORQUESTRA
  ↓
Claude — EXECUTA
  ↓
GPT — AUDITA
  ↓
APROVADO?
 ↙        ↘
NÃO        SIM
 ↓          ↓
Claude     registrar resultado
corrige     e avançar
 ↓
GPT audita novamente
```

## Regra central

Claude não declara unilateralmente que uma etapa estratégica está "100% concluída". Claude entrega → GPT audita → GPT aprova ou devolve correções. Decisões reservadas aos humanos (Nathan e/ou Xande) continuam reservadas aos humanos — nenhuma IA aprova, em nome deles, conteúdo marcado como decisão crítica em [`AGENTS.md`](../AGENTS.md).

## Estados de uma tarefa

| Estado | Significado |
|---|---|
| `BACKLOG` | Identificada, ainda não priorizada |
| `READY` | Priorizada e pronta para ser orquestrada pelo GPT |
| `EXECUTING` | Claude está trabalhando nela |
| `REVIEW_GPT` | Entregue por Claude, aguardando auditoria do GPT |
| `REVISION_REQUIRED` | GPT auditou e devolveu correções — volta para Claude |
| `HUMAN_DECISION_REQUIRED` | Depende de decisão de Nathan e/ou Xande antes de prosseguir |
| `APPROVED` | GPT aprovou a entrega (e, quando aplicável, humanos aprovaram a decisão) |
| `DONE` | Critérios de conclusão (ver abaixo) atingidos |

Uma tarefa pode alternar várias vezes entre `EXECUTING`, `REVIEW_GPT` e `REVISION_REQUIRED` antes de chegar a `APPROVED`. `HUMAN_DECISION_REQUIRED` pode ser acionado a partir de qualquer estado, sempre que se descobrir que a tarefa depende de uma decisão crítica ainda não tomada.

## Definition of Done

Uma tarefa só pode chegar a `DONE` quando, simultaneamente:

- [ ] a entrega solicitada existe (arquivo criado/editado conforme pedido);
- [ ] as fontes foram verificadas quando havia como verificá-las;
- [ ] nenhuma inferência está apresentada como fato (tags de [`10-fontes-e-rastreabilidade.md`](10-fontes-e-rastreabilidade.md) aplicadas onde há impacto estratégico);
- [ ] inconsistências conhecidas foram resolvidas ou explicitamente registradas como pendência;
- [ ] verificações aplicáveis passaram (ex.: `git diff` conferido, arquivos referenciados existem);
- [ ] o GPT realizou a auditoria da entrega;
- [ ] as decisões humanas necessárias (Nathan e/ou Xande) foram aprovadas, quando a tarefa depender delas.

**Se faltar decisão de Nathan e/ou Xande, o estado correto é `HUMAN_DECISION_REQUIRED` — nunca `DONE`.** Nem Claude nem GPT podem substituir essa aprovação.
