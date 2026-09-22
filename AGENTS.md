# AGENTS.md — vyo-ceo

Este repositório documenta a camada estratégica e de negócio da VYO (marca, produto, preço, mercado, jurídico, metas). Ele **não contém código de produto** — isso vive em [`github.com/XandeJvSIlva/VYO`](https://github.com/XandeJvSIlva/VYO).

## Regras para qualquer IA ou colaborador editando este repositório

1. **Decisões críticas exigem aprovação de Nathan E Xande.** Preço e posicionamento nunca viram conteúdo `[DECISÃO]`/STATUS "Oficial" com base só em uma conversa, proposta, ou na aprovação de um único sócio — precisam de validação explícita e registrada dos dois. Na dúvida, mantenha como `[PROPOSTA]` e STATUS "Em validação".
2. **Use os dois eixos de classificação definidos em [`docs/10-fontes-e-rastreabilidade.md`](docs/10-fontes-e-rastreabilidade.md):**
   - **STATUS** do documento: Oficial · Em validação · Pesquisa · Arquivado.
   - **CONFIANÇA** da informação: Confirmada · Fonte secundária · Inferência · Não verificada.
   - Esses dois eixos são independentes — não confunda "pesquisa concluída" com "decisão oficial" (ver regra central em `docs/10`).
3. **Não invente dados reais.** Datas de fundação, valores de contrato fechado, nomes de clientes — se não estiver confirmado na fonte (Notion/Google Docs), marque como `[PENDENTE]` em vez de preencher com um palpite. Nunca transforme um dado provável ou contraditório em fato institucional — registre a contradição explicitamente.
4. **Notion é a fonte primária do dia a dia.** Este repositório é o snapshot versionado. Antes de declarar algo desatualizado ou de reescrever uma seção inteira, verifique a página (ou, quando aplicável, a database) correspondente no workspace **VYO • Central de tarefas**.
5. **Não duplique código ou specs técnicas de produto aqui.** Isso pertence ao repositório `XandeJvSIlva/VYO`. Este repositório referencia esse conteúdo quando relevante para uma decisão de negócio, mas não o reproduz — e, quando o fizer, marque como CONFIANÇA "Fonte secundária" a menos que o arquivo real tenha sido lido diretamente na sessão.
6. **Preserve o vocabulário de marca já aprovado** (ver `docs/01-identidade-marca.md`) em qualquer texto novo escrito para uso externo: evite "disruptivo", "revolucionário", "sinergia", "plataforma robusta", "paradigma".
7. **Use as tags de rastreabilidade** (`[FATO]`, `[DECISÃO]`, `[PROPOSTA]`, `[HIPÓTESE]`, `[IA-INFERÊNCIA]`, `[PENDENTE]` — ver `docs/10-fontes-e-rastreabilidade.md`) em qualquer afirmação com impacto estratégico. Toda decisão estratégica relevante deve conseguir apontar para sua origem.

## Protocolo Multiagente

### Papéis

- **NATHAN** — CEO / autoridade humana de direção.
- **XANDE** — Sócio / autoridade humana nas decisões que exigem validação conjunta.
- **GPT** — Orquestrador + Auditor. Analisa contexto, define tarefas, detecta inconsistências, audita entregas, emite nova ordem, determina se os critérios de conclusão foram atingidos.
- **CLAUDE** — Executor. Pesquisa fontes autorizadas, edita arquivos, implementa alterações, executa tarefas, reporta exatamente o que foi alterado, declara inferências e limitações.

### Regra

**Claude não declara unilateralmente que uma etapa estratégica está "100% concluída".** Claude entrega → GPT audita → GPT aprova ou devolve correções. Decisões reservadas aos humanos continuam reservadas aos humanos — nenhuma IA aprova, em nome de Nathan ou Xande, conteúdo marcado como decisão crítica.

Fluxo completo, estados e Definition of Done: ver [`docs/11-protocolo-multiagente.md`](docs/11-protocolo-multiagente.md).

## Estrutura

Ver [`README.md`](README.md) para o índice completo dos documentos em `docs/`.
