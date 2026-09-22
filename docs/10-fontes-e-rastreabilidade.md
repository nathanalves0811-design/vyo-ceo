# Fontes e Rastreabilidade

**STATUS:** Oficial (meta-documento de governança de conhecimento)

Este documento define como qualquer informação neste repositório deve ser classificada, para que seja sempre possível distinguir fato de proposta, decisão de hipótese, e conteúdo humano de conteúdo gerado por IA.

## Por que este documento existe

A AUDITORIA 001 (GPT, orquestrador/auditor deste projeto) identificou que a primeira versão deste repositório misturava, sem distinção clara:

- fatos confirmados em fonte primária;
- decisões efetivamente aprovadas pelos sócios;
- propostas ainda não aprovadas;
- hipóteses em teste;
- sínteses e inferências geradas pela IA que construiu o repositório (Claude);
- informações simplesmente não verificadas.

Essa mistura é o risco central de uma base estratégica "escrita por IA": ela pode soar confiável sem ser rastreável. Este documento corrige isso.

## As seis tags

Use estas tags entre colchetes junto a qualquer afirmação com impacto estratégico. Não é necessário marcar cada frase mecanicamente — use onde a distinção importa: preço, posicionamento, dados jurídicos, datas institucionais, metas.

- **[FATO]** — Informação diretamente comprovada por fonte primária (ex.: dado transcrito de um campo Notion, número de processo do INPI, nome confirmado em documento).
- **[DECISÃO]** — Decisão explicitamente aprovada pelos responsáveis necessários. Para decisões críticas (preço, posicionamento — ver [`AGENTS.md`](../AGENTS.md)), isso significa aprovação registrada de **Nathan E Xande**. Aprovação de apenas um sócio é registrada como decisão parcial, não como `[DECISÃO]` plena, até o segundo aval existir.
- **[PROPOSTA]** — Algo sugerido (por um sócio, por uma pesquisa, ou por uma IA), mas ainda não aprovado como padrão oficial.
- **[HIPÓTESE]** — Algo sendo testado ou ainda não validado na prática (ex.: hipótese de pipeline técnico, hipótese de modelo de negócio).
- **[IA-INFERÊNCIA]** — Conclusão, síntese ou estrutura criada por uma IA (nesta base, majoritariamente Claude, o agente executor) a partir de informações existentes, sem que essa conclusão específica exista, com essas palavras, na fonte original. Isso inclui decisões de arquitetura deste próprio repositório (nomeação de arquivos, agrupamento de conteúdo, texto de transição).
- **[PENDENTE]** — Informação necessária que ainda não foi confirmada por ninguém, IA ou humano.

## Regra central: "concluído no Notion" ≠ "oficial"

Uma tarefa marcada como **"Concluída"** no Notion significa que **o trabalho de pesquisa, redação ou produção terminou** — não que Nathan e Xande **aprovaram o conteúdo como política da empresa**. São coisas diferentes:

| Situação no Notion | O que isso NÃO significa automaticamente |
|---|---|
| Tarefa "Concluída" | Que o conteúdo virou decisão oficial da empresa |
| Responsável = uma pessoa só | Que os dois sócios aprovaram |
| Pesquisa "concluída" | Que a recomendação da pesquisa foi adotada |

Uma tarefa "Concluída" cujo *conteúdo* é uma pesquisa (ex.: mercado, INPI) deve ser classificada com **STATUS: Pesquisa**, não **STATUS: Oficial**. Uma tarefa "Concluída" cujo responsável é só um dos sócios deve ser tratada, no máximo, como `[DECISÃO]` parcial, salvo evidência explícita do segundo aval.

## STATUS vs. CONFIANÇA

São dois eixos independentes. Um documento pode ter STATUS "Pesquisa" com CONFIANÇA "Confirmada" (dados de mercado bem coletados, mas que não constituem decisão), ou STATUS "Em validação" com CONFIANÇA "Inferência" (proposta ainda especulativa).

### STATUS do documento (ciclo de vida)

- **Oficial** — aprovado pelos responsáveis necessários; pode ser usado como referência final.
- **Em validação** — existe, mas depende de aprovação (de um ou dos dois sócios) antes de virar padrão.
- **Pesquisa** — levantamento de dados concluído; não é, por si só, uma decisão.
- **Arquivado** — superado por uma versão mais nova ou por uma decisão que o invalidou; mantido por histórico.

### CONFIANÇA da informação (qualidade da fonte)

- **Confirmada** — verificada diretamente em fonte primária (Notion, documento oficial, base pública como o INPI).
- **Fonte secundária** — vem de um resumo ou menção de segunda mão (ex.: um resumo no Notion sobre um arquivo que vive em outro repositório, nunca lido diretamente por quem escreveu este documento).
- **Inferência** — conclusão derivada por raciocínio (humano ou IA) a partir de outras informações, sem uma fonte que a declare diretamente.
- **Não verificada** — não houve checagem nesta sessão; presente apenas porque foi mencionada em algum lugar.

## Hierarquia de fontes da VYO

Da mais para a menos autoritativa:

1. **Aprovação explícita e registrada de Nathan e Xande** — única fonte que sustenta `[DECISÃO]` em item crítico.
2. **Aprovação explícita de um sócio individual** sobre um item sob sua alçada (ex.: Nathan aprovando slogans) — sustenta `[DECISÃO]` parcial, não decisão de empresa.
3. **Documentos primários no Notion / Google Docs vinculado** — sustentam `[FATO]` quando descrevem um dado (número, data, nome) e `[PROPOSTA]`/`[HIPÓTESE]` quando descrevem uma recomendação ainda não aprovada.
4. **Bases públicas oficiais** (ex.: busca do INPI) — sustentam `[FATO]` para os dados que reproduzem.
5. **Repositório de engenharia** (`github.com/XandeJvSIlva/VYO`) — fonte primária para specs técnicas, mas **não lido diretamente nesta sessão**. Qualquer conteúdo dele citado aqui vem de resumos no Notion e deve ser tratado como CONFIANÇA "Fonte secundária" até ser verificado contra o repositório real.
6. **Síntese produzida pela IA que constrói este repositório (Claude)** — nunca é, por si só, fonte de fato ou decisão. É sempre `[IA-INFERÊNCIA]`, mesmo quando factualmente razoável.

## Como usar este documento

- Ao escrever ou revisar qualquer arquivo em `docs/`, aplique a tag mais específica possível a afirmações com impacto estratégico.
- Se uma afirmação combina dois níveis (ex.: um fato real usado para sustentar uma inferência nova), marque os dois separadamente.
- Nunca promova uma tag para uma mais forte (`[PROPOSTA]` → `[DECISÃO]`) sem registrar a fonte da aprovação que justifica a mudança.
- Ver [`AGENTS.md`](../AGENTS.md) e [`11-protocolo-multiagente.md`](11-protocolo-multiagente.md) para quem pode fazer essa promoção (Claude executa; GPT audita; decisões críticas exigem Nathan e Xande).
