# Governança

**STATUS:** Em validação (reduzido de "Oficial" — ver correção abaixo)
**CONFIANÇA:** Mista — ver por seção. Ver [`10-fontes-e-rastreabilidade.md`](10-fontes-e-rastreabilidade.md).

**Correção em relação à versão anterior:** este documento estava marcado como "✅ Oficial" por inteiro. Parte do conteúdo é, de fato, fato verificável (sócios, regra de decisão crítica citada em outras páginas). Mas a seção "Divisão entre os dois repositórios" e "Fontes de verdade e atualização" são estrutura proposta por Claude ao montar este repositório — nunca foram aprovadas por Nathan ou Xande como política. Por isso o status geral foi reduzido para "Em validação", com tags por seção abaixo.

## Sócios — [FATO]

A VYO é comandada por dois sócios: **Nathan** e **Alexandre "Xande"**, com apoio de IAs em execução, pesquisa e organização.

*Fonte: consistente em múltiplas páginas Notion (tarefas, resumos, histórico).*

## Decisões críticas — [FATO], com ressalva de fonte

Preço e posicionamento são citados como **decisões críticas** em pelo menos duas páginas Notion (ex.: o callout da página "Pesquisa & Proposta de Precificação" afirma: *"Preço é classificado como decisão crítica no AGENTS.md do repositório — exige aprovação prévia de Nathan e Xande antes de virar padrão oficial"*). Isso é tratado como `[FATO]` de que a regra existe e é referenciada pelos sócios/IAs no dia a dia.

**Ressalva de CONFIANÇA:** o arquivo `AGENTS.md` real do repositório de produto (`github.com/XandeJvSIlva/VYO`), onde essa regra supostamente vive, **não foi lido diretamente nesta sessão** — apenas citado por outras páginas. CONFIANÇA: Fonte secundária para o texto exato da regra; Confirmada para o fato de que a regra é referenciada e seguida na prática (citada em múltiplos documentos independentes).

Documentos afetados por essa regra neste repositório: [`03-precificacao.md`](03-precificacao.md), [`06-estrategia-comercial.md`](06-estrategia-comercial.md), a seção "Posicionamento" de [`01-identidade-marca.md`](01-identidade-marca.md).

## Processo de trabalho — [FATO]

Fonte: página "Histórico de Tarefas VYO", seção Governança & Processo de Trabalho (Issues #10, #15, #23, #26).

- Branch/worktree obrigatórias para qualquer mudança, com confirmação passo a passo.
- Revisão assíncrona: merge sozinho é permitido em tarefa comum, com validação posterior; decisões críticas exigem validação prévia dos dois sócios.
- Título de Issue/PR em português, com nomenclatura padronizada.

## Divisão entre os dois repositórios — [IA-INFERÊNCIA]

**Esta seção não é uma decisão aprovada.** É a estrutura que Claude propôs ao organizar este repositório, com base em observar que existe um repositório de produto separado (`XandeJvSIlva/VYO`) e que este repositório (`vyo-ceo`) foi pedido como algo novo e distinto. Nenhum sócio aprovou formalmente esta divisão de responsabilidades entre os dois repositórios.

| Repositório | Conteúdo proposto | Fonte de verdade proposta |
|---|---|---|
| `XandeJvSIlva/VYO` | Engenharia do produto: especificações por Issue, código, PRs, `AGENTS.md`/`CONTRIBUTING.md` técnicos | GitHub |
| `vyo-ceo` (este) | Camada estratégica e de negócio: marca, produto (visão), preço, mercado, jurídico, metas, governança | Notion (**VYO • Central de tarefas**) + Google Docs vinculados |

## Fontes de verdade e atualização — [IA-INFERÊNCIA]

Também proposta por Claude, não aprovada pelos sócios:

O dia a dia da empresa — tarefas, metas, histórico — é gerido no workspace Notion **VYO • Central de tarefas**, com documentos longos vinculados em Google Docs. A proposta é que este repositório funcione como **snapshot versionado e navegável** dessas decisões, atualizado sob demanda (não há sincronização automática hoje).

Se esta proposta for aprovada, regras sugeridas para manter a rastreabilidade:

1. Confirmar no Notion se a página-fonte mudou desde a última sincronização.
2. Preservar as tags de [`10-fontes-e-rastreabilidade.md`](10-fontes-e-rastreabilidade.md) — não promover `[PROPOSTA]` a `[DECISÃO]` sem registrar a fonte da aprovação.
3. Referenciar a tarefa/documento de origem quando relevante, para rastreabilidade.

## Protocolo multiagente — [FATO] (definido nesta sessão, formalizado em AGENTS.md)

A partir desta auditoria, o processo de trabalho entre Nathan, Xande, GPT (orquestrador/auditor) e Claude (executor) segue o protocolo definido em [`AGENTS.md`](../AGENTS.md) e detalhado em [`11-protocolo-multiagente.md`](11-protocolo-multiagente.md).
