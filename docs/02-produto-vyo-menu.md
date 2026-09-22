# Produto — VYO Menu

**Status:** 🟡 Rascunho vivo — especificação detalhada e código vivem em [`github.com/XandeJvSIlva/VYO`](https://github.com/XandeJvSIlva/VYO) (`docs/project-overview.md`, issues por funcionalidade). Este documento resume a proposta de valor e o modelo de produto para uso estratégico.

## Propósito

Oferecer um cardápio digital com visualização 3D e realidade aumentada, permitindo que o cliente conheça melhor o produto antes de escolher.

## Experiências principais

- **Visualização 3D** — girar, aproximar e observar o produto pelo navegador.
- **Realidade aumentada** — posicionar o produto sobre a mesa, em escala real (um prato de 12 cm precisa aparecer com ~12 cm no ambiente real).
- **Exploded View** (futuro) — desconstruir visualmente o produto em camadas/componentes (ex.: pão, bacon, queijo, carne, salada e molhos como camadas independentes).

Fluxo de uso: QR Code → cardápio → selecionar produto → "Ver na minha mesa" → abrir câmera → detectar superfície → posicionar modelo → visualizar em escala real.

## Planos

- **Plano Cardápio** — só consulta: categorias, produtos, fotos, preços, disponibilidade. Sem pedidos nem pagamento.
- **Plano Delivery** — cardápio público completo + carrinho + entrega/retirada + pagamento + cupons + cashback opcional.

## Módulos opcionais (contratáveis por qualquer plano)

- **Estoque** — insumos, embalagens, movimentações.
- **Produção e receitas** — depende do módulo Estoque.
- **Custos e precificação** — depende dos dois anteriores.
- **Chatbot (WhatsApp)** — módulo à parte, só quando contratado.
- **3D/AR** — planejado, última etapa do desenvolvimento; ainda não precificado como módulo autônomo.

## Modelo de cobrança (já decidido)

Referência explícita ao Anota AI: mensalidade fixa por plano, **sem comissão percentual** sobre pedidos, e uma **taxa fixa da VYO de R$ 0,99 por pedido pago online** (descontada do restaurante, configurável por caso). O valor das mensalidades em si é tratado em [`03-precificacao.md`](03-precificacao.md).

## Desafio técnico central

O ponto mais difícil do projeto não é o site nem a realidade aumentada — é **transformar os produtos dos restaurantes em modelos 3D de boa qualidade de forma rápida, barata e escalável**. Um restaurante com 70 pratos inviabiliza modelagem manual artista-a-artista em custo e tempo.

Linhas de investigação: fotogrametria, reconstrução 3D assistida por IA, Gaussian Splatting quando aplicável, automatização de tratamento/otimização dos modelos.

### Pipeline 3D — hipótese inicial

```
Produto real → captura de imagens → reconstrução 3D → tratamento/otimização
→ correção de escala → GLB/GLTF → plataforma VYO Menu
```

Ferramentas em avaliação: **RealityScan** (captura/fotogrametria), **KIRI Engine** (alternativa de captura/reconstrução), **Blender** (limpeza, orientação, escala, otimização, exportação). Formato final para web: GLB/GLTF.

### Riscos identificados

- **Qualidade das fotos** dos clientes pode ser ruim/inconsistente — avaliar fluxo de revitalização com IA (prompts padronizados).
- **Escalabilidade dos modelos 3D** — captura e tratamento precisam ser rápidos o suficiente para não virar dezenas de horas manuais por restaurante.
- **Realismo** — evitar aparência borrada/artificial; qualidade visual é ponto central a validar nos primeiros testes.

## Perguntas ainda sem resposta

- Como tornar a solução atrativa para estabelecimentos com faturamento menor?
- Qual o custo real por produto 3D e o tempo de captura/preparo?
- RealityScan ou KIRI entrega melhor qualidade para alimentos?
- Quanto do processo no Blender pode ser automatizado?
- Quantos produtos 3D devem existir em cada plano?
- Qual nível de realismo é possível mantendo carregamento rápido no celular?
- Modelo de cobrança do 3D/AR: setup + mensalidade, mensalidade apenas, ou por quantidade de produtos? (ver também a proposta alternativa do Xande em [`03-precificacao.md`](03-precificacao.md))

## Próxima validação — POC

Antes de desenvolver toda a plataforma: selecionar um produto real → captura de alta qualidade → reconstrução no RealityScan → comparar com KIRI Engine se necessário → tratar no Blender → corrigir escala real → exportar GLB → testar visualização 3D no navegador → testar AR sobre uma mesa → medir tempo total, qualidade e tamanho do arquivo.

**Critério de sucesso:** transformar um produto real em um modelo 3D convincente, otimizado e em escala real, com um processo repetível em dezenas de produtos.

## Modelo de negócio (hipótese)

Não é "vender um site" — é **digitalização 3D do cardápio + plataforma mensal**. Nem todo item precisa de 3D: produtos simples ficam com fotos, itens de maior valor visual/comercial recebem 3D/AR. Isso permite planos diferentes conforme a quantidade de produtos digitalizados.
