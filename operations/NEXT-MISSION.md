# NEXT-MISSION

**Estado:** `AGUARDANDO ENTRADA DO CEO`

Nenhuma missão foi aberta ainda. Este arquivo não é, ele mesmo, uma missão — existe para que o GPT saiba exatamente o que fazer assim que Nathan trouxer a próxima solicitação.

## Instruções mínimas para o GPT

Quando Nathan trouxer uma solicitação (ex.: "quero estruturar o CRM da VYO Menu", "precisamos montar o calendário editorial", "analise essa ideia"):

1. **Interpretar o pedido** — extrair objetivo, contexto disponível, e o que precisa existir ao final.
2. **Atribuir o próximo ID disponível**, seguindo o padrão `VYO-YYYY-NNN` (o primeiro será `VYO-2026-001` — regra de não reutilização em [`README.md`](README.md)).
3. **Copiar [`mission-template.md`](mission-template.md)** para um novo arquivo em `operations/active/VYO-2026-001.md` (ajustando ano/número conforme o caso) e preencher: Objetivo, Contexto, Fontes autorizadas, Restrições, Critérios de sucesso, Decisões humanas necessárias (se houver) e Nível de autonomia.
4. **Definir o nível de autonomia** (A1/A2/A3 — ver `README.md`) com base na natureza do pedido; decisões críticas (preço, contrato, posicionamento oficial, gasto, jurídico, credenciais, publicação irreversível) sempre param em `HUMAN_DECISION_REQUIRED`, independentemente do nível.
5. **Marcar o estado como `MISSION READY`** e passar para Claude executar.
6. Seguir o ciclo completo descrito em [`README.md`](README.md) (execução → SELF-CHECK → `REVIEW_GPT` → aprovação ou `REVISION`, até `MAX_AUTONOMOUS_CYCLES = 5`; depois disso, `HUMAN_REVIEW_REQUIRED`).
7. Ao final, decidir **PROMOVER PARA DOCS** ou **NÃO PROMOVER** o conhecimento gerado, e só então instruir Claude a mover a missão de `operations/active/` para `operations/completed/`.

**Não invente uma missão para preencher este arquivo.** Ele permanece neste estado até que Nathan efetivamente peça algo.
