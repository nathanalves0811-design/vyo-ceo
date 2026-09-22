# VYO — Ecossistema

Este repositório é a **camada estratégica e de negócio da VYO**: identidade, produto, precificação, mercado, jurídico, metas e governança, consolidados a partir do que já foi decidido (ou está em decisão) entre os sócios.

Ele **não** contém código de produto — a engenharia do VYO Menu (specs, issues, PRs) vive em [`github.com/XandeJvSIlva/VYO`](https://github.com/XandeJvSIlva/VYO). Este repositório é o "cérebro" da empresa: a versão versionada e navegável do que hoje está espalhado entre o Notion (tarefas do dia a dia) e o Google Docs (documentos longos).

## Como ler isto

Cada documento tem um status no topo:

- ✅ **Oficial** — aprovado por Nathan e Xande, pode ser usado como referência final.
- 🟡 **Rascunho** — pendente de validação conjunta. Não comunicar a cliente nem tratar como decisão fechada.
- 🔴 **Bloqueado** — depende de uma decisão externa (jurídica, dado real, etc.) antes de avançar.

Preço e posicionamento são sempre **decisões críticas**: exigem aprovação explícita de Nathan **e** Xande antes de virar padrão oficial (ver [`AGENTS.md`](./AGENTS.md)).

## Estrutura

| Documento | Conteúdo | Status |
|---|---|---|
| [`docs/00-visao-geral.md`](docs/00-visao-geral.md) | Fundação, propósito, história | 🔴 datas reais pendentes |
| [`docs/01-identidade-marca.md`](docs/01-identidade-marca.md) | Slogans, tom de voz, vocabulário, posicionamento | ✅ Oficial |
| [`docs/02-produto-vyo-menu.md`](docs/02-produto-vyo-menu.md) | Planos, módulos, pipeline 3D/AR | 🟡 Rascunho (specs em evolução) |
| [`docs/03-precificacao.md`](docs/03-precificacao.md) | Preços, proposta por plano, preço de validação | 🟡 Rascunho — decisão crítica |
| [`docs/04-mercado-concorrencia.md`](docs/04-mercado-concorrencia.md) | Anota AI, Goomer, Saipos, ARK Menu, referências de AR | ✅ Pesquisa concluída |
| [`docs/05-cliente-ideal.md`](docs/05-cliente-ideal.md) | ICP, qualificação de lead, diretrizes comerciais | 🟡 Rascunho |
| [`docs/06-estrategia-comercial.md`](docs/06-estrategia-comercial.md) | Vendas, entrega, princípio "nunca conceda, troque" | 🟡 Rascunho — decisão crítica |
| [`docs/07-propriedade-intelectual.md`](docs/07-propriedade-intelectual.md) | Situação no INPI, risco VYOX, rota recomendada | ✅ Pesquisa concluída |
| [`docs/08-metas-roadmap.md`](docs/08-metas-roadmap.md) | Horizonte 1 (validação) e Horizonte 2 (escala) | 🟡 Rascunho |
| [`docs/09-governanca.md`](docs/09-governanca.md) | Sócios, processo de decisão, fontes de verdade | ✅ Oficial |

## A empresa, em uma frase

**VYO** é tecnologia para restaurantes. Seu primeiro produto, o **VYO Menu**, é um cardápio digital com visualização 3D e realidade aumentada — o cliente vê o prato em escala real sobre a própria mesa antes de pedir.

> "Tecnologia que serve experiências."

## Fontes

Todo o conteúdo aqui foi sintetizado a partir do workspace Notion **VYO • Central de tarefas** (tarefas, metas, documentos-filhos) e dos Google Docs vinculados a cada tarefa concluída. Quando uma decisão mudar no Notion, este repositório deve ser atualizado para refletir a nova fonte de verdade — ver [`docs/09-governanca.md`](docs/09-governanca.md).
