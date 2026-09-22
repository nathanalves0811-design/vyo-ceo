# VYO — Ecossistema

Este repositório é a **camada estratégica e de negócio da VYO**: identidade, produto, precificação, mercado, jurídico, metas e governança, consolidados a partir do que já foi decidido (ou está em decisão) entre os sócios.

Ele **não** contém código de produto — a engenharia do VYO Menu (specs, issues, PRs) vive em [`github.com/XandeJvSIlva/VYO`](https://github.com/XandeJvSIlva/VYO). Este repositório é o "cérebro" da empresa: a versão versionada e navegável do que hoje está espalhado entre o Notion (tarefas do dia a dia) e o Google Docs (documentos longos).

## Como ler isto

**"Concluído no Notion" não é o mesmo que "oficial neste repositório".** Uma tarefa pode estar concluída porque a pesquisa ou produção terminou, sem que isso signifique que Nathan e Xande aprovaram o conteúdo como política da empresa. Por isso, cada documento usa dois eixos de classificação — ver [`docs/10-fontes-e-rastreabilidade.md`](docs/10-fontes-e-rastreabilidade.md) para a definição completa:

- **STATUS** (ciclo de vida do documento): Oficial · Em validação · Pesquisa · Arquivado.
- **CONFIANÇA** (qualidade da fonte): Confirmada · Fonte secundária · Inferência · Não verificada.

Dentro dos documentos, afirmações com impacto estratégico também carregam uma tag: `[FATO]`, `[DECISÃO]`, `[PROPOSTA]`, `[HIPÓTESE]`, `[IA-INFERÊNCIA]` ou `[PENDENTE]`.

Preço e posicionamento são sempre **decisões críticas**: exigem aprovação explícita de Nathan **e** Xande antes de virar `[DECISÃO]`/STATUS "Oficial" (ver [`AGENTS.md`](./AGENTS.md)).

## Estrutura

| Documento | Conteúdo | STATUS | CONFIANÇA |
|---|---|---|---|
| [`docs/00-visao-geral.md`](docs/00-visao-geral.md) | Fundação, propósito, história | Em validação | Mista — fundação é `[PENDENTE]`, não fato |
| [`docs/01-identidade-marca.md`](docs/01-identidade-marca.md) | Slogans, tom de voz, vocabulário, posicionamento | Em validação | Slogans: aprovação parcial (Nathan). Posicionamento: proposta |
| [`docs/02-produto-vyo-menu.md`](docs/02-produto-vyo-menu.md) | Planos, módulos, pipeline 3D/AR | Pesquisa / Em validação | Fonte secundária (via Notion, não verificado no repo de engenharia) |
| [`docs/03-precificacao.md`](docs/03-precificacao.md) | Preços, proposta por plano, preço de validação | Em validação — decisão crítica | Proposta |
| [`docs/04-mercado-concorrencia.md`](docs/04-mercado-concorrencia.md) | Anota AI, Goomer, Saipos, ARK Menu, referências de AR | Pesquisa | Confirmada (dados); inferência nas conclusões de posicionamento |
| [`docs/05-cliente-ideal.md`](docs/05-cliente-ideal.md) | ICP, qualificação de lead, diretrizes comerciais | Em validação | Proposta |
| [`docs/06-estrategia-comercial.md`](docs/06-estrategia-comercial.md) | Vendas, entrega, princípio "nunca conceda, troque" | Em validação — decisão crítica | Proposta |
| [`docs/07-propriedade-intelectual.md`](docs/07-propriedade-intelectual.md) | Situação no INPI, risco VYOX, rota recomendada | Pesquisa | Confirmada (dados INPI); proposta nas recomendações |
| [`docs/08-metas-roadmap.md`](docs/08-metas-roadmap.md) | Metas reais da database Notion + leitura estratégica da IA | Em validação | Confirmada (Seção 1, dados reais); inferência (Seção 2) |
| [`docs/09-governanca.md`](docs/09-governanca.md) | Sócios, processo de decisão, fontes de verdade | Em validação | Mista — divisão entre repositórios é inferência da IA, não aprovada |
| [`docs/10-fontes-e-rastreabilidade.md`](docs/10-fontes-e-rastreabilidade.md) | Sistema de tags e hierarquia de fontes | Oficial (meta-documento) | — |
| [`docs/11-protocolo-multiagente.md`](docs/11-protocolo-multiagente.md) | Fluxo Nathan → GPT → Claude, estados, Definition of Done | Oficial (meta-documento) | — |

## A empresa, em uma frase

**VYO** é tecnologia para restaurantes. Seu primeiro produto, o **VYO Menu**, é um cardápio digital com visualização 3D e realidade aumentada — o cliente vê o prato em escala real sobre a própria mesa antes de pedir.

> "Tecnologia que serve experiências." *(slogan aprovado por Nathan — ver [`01-identidade-marca.md`](docs/01-identidade-marca.md))*

## Governança e protocolo multiagente

Desde a AUDITORIA 001, este repositório opera sob um protocolo com quatro papéis: **Nathan** e **Xande** (autoridade humana), **GPT** (orquestrador/auditor) e **Claude** (executor). Claude não declara unilateralmente uma etapa estratégica como concluída — toda entrega passa por auditoria do GPT antes de avançar, e decisões críticas continuam reservadas aos humanos. Ver [`AGENTS.md`](AGENTS.md) e [`docs/11-protocolo-multiagente.md`](docs/11-protocolo-multiagente.md).

## Fontes

Todo o conteúdo aqui foi sintetizado a partir do workspace Notion **VYO • Central de tarefas** (tarefas, metas, documentos-filhos) e dos Google Docs vinculados a cada tarefa concluída. Quando uma decisão mudar no Notion, este repositório deve ser atualizado para refletir a nova fonte de verdade — ver [`docs/09-governanca.md`](docs/09-governanca.md).
