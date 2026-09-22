# Produto — VYO Menu

**STATUS:** Pesquisa / Em validação
**CONFIANÇA:** Mista — ver tags por seção. Especificação técnica detalhada e código vivem em [`github.com/XandeJvSIlva/VYO`](https://github.com/XandeJvSIlva/VYO), **não acessado diretamente nesta sessão** (fora do escopo de repositórios autorizados). Tudo abaixo que descreve esse repositório vem de resumos feitos dentro do Notion sobre ele — CONFIANÇA: Fonte secundária, salvo indicação contrária.

Este documento distingue três tipos de conteúdo, marcados por seção:
- **[VISÃO DE NEGÓCIO]** — proposta de valor e modelo de produto, como discutido pelos sócios.
- **[TÉCNICO — NÃO VERIFICADO]** — descrições de especificação/arquitetura mencionadas no Notion, mas cuja fonte primária (o repositório de engenharia) não foi lida nesta sessão.
- **[HIPÓTESE ESTRATÉGICA]** — hipóteses ainda não testadas sobre como o produto deve funcionar ou ser cobrado.

Nenhuma lacuna técnica foi preenchida por inferência — onde a fonte não detalha algo, o documento marca `[PENDENTE]` em vez de supor.

## Propósito — [VISÃO DE NEGÓCIO]

Oferecer um cardápio digital com visualização 3D e realidade aumentada, permitindo que o cliente conheça melhor o produto antes de escolher.

*Fonte: página "PROPÓSITO DO PROJETO" (Notion). CONFIANÇA: Confirmada (conteúdo lido diretamente na página-fonte).*

## Experiências principais — [VISÃO DE NEGÓCIO]

- **Visualização 3D** — girar, aproximar e observar o produto pelo navegador.
- **Realidade aumentada** — posicionar o produto sobre a mesa, em escala real (um prato de 12 cm precisa aparecer com ~12 cm no ambiente real).
- **Exploded View** (futuro, `[HIPÓTESE ESTRATÉGICA]`) — desconstruir visualmente o produto em camadas/componentes (ex.: pão, bacon, queijo, carne, salada e molhos como camadas independentes).

Fluxo de uso: QR Code → cardápio → selecionar produto → "Ver na minha mesa" → abrir câmera → detectar superfície → posicionar modelo → visualizar em escala real.

## Planos e módulos — [TÉCNICO — NÃO VERIFICADO]

Esta seção resume o que a página Notion "💰 Pesquisa & Proposta de Precificação — VYO Menu" descreve como já existente em `docs/project-overview.md`, dentro do repositório de engenharia. **Claude não leu esse arquivo diretamente** — o conteúdo abaixo é a leitura que o próprio Notion faz dele, não uma verificação de primeira mão. CONFIANÇA: Fonte secundária.

- **Plano Cardápio** — só consulta: categorias, produtos, fotos, preços, disponibilidade. Sem pedidos nem pagamento.
- **Plano Delivery** — cardápio público completo + carrinho + entrega/retirada + pagamento + cupons + cashback opcional.
- **Módulos opcionais:** Estoque; Produção e receitas (depende de Estoque); Custos e precificação (depende dos dois anteriores); Chatbot (WhatsApp); 3D/AR (planejado, última etapa do desenvolvimento, ainda não precificado como módulo autônomo).

## Modelo de cobrança — [DECISÃO], fonte secundária

A mesma página Notion afirma que isto "já está definido": mensalidade fixa por plano, **sem comissão percentual** sobre pedidos, e uma **taxa fixa da VYO de R$ 0,99 por pedido pago online**. Referência explícita ao modelo do Anota AI. Tratado como `[DECISÃO]` porque a fonte o descreve como fechado — mas, como o restante da seção "Planos e módulos", isso é uma leitura de segunda mão do repositório de engenharia, não verificação direta. O valor das mensalidades em si é tratado em [`03-precificacao.md`](03-precificacao.md), onde segue como `[PROPOSTA]`.

## Desafio técnico central — [HIPÓTESE ESTRATÉGICA]

O ponto mais difícil do projeto, segundo o material de propósito do projeto, não é o site nem a realidade aumentada — é **transformar os produtos dos restaurantes em modelos 3D de boa qualidade de forma rápida, barata e escalável**. Um restaurante com 70 pratos inviabilizaria modelagem manual artista-a-artista em custo e tempo — isso é uma preocupação registrada, não um resultado medido.

Linhas de investigação citadas: fotogrametria, reconstrução 3D assistida por IA, Gaussian Splatting quando aplicável, automatização de tratamento/otimização dos modelos. Nenhuma delas tem resultado de teste registrado na fonte.

### Pipeline 3D — [HIPÓTESE ESTRATÉGICA], não implementado

```
Produto real → captura de imagens → reconstrução 3D → tratamento/otimização
→ correção de escala → GLB/GLTF → plataforma VYO Menu
```

Ferramentas citadas como em avaliação (não confirmadas como escolhidas): **RealityScan**, **KIRI Engine**, **Blender**. Formato final para web citado: GLB/GLTF.

### Riscos identificados — [HIPÓTESE ESTRATÉGICA]

- Qualidade das fotos dos clientes pode ser ruim/inconsistente.
- Escalabilidade dos modelos 3D — captura e tratamento precisam ser rápidos o suficiente para não virar dezenas de horas manuais por restaurante.
- Realismo — evitar aparência borrada/artificial.

Nenhum desses riscos tem mitigação testada registrada na fonte.

## Perguntas ainda sem resposta — [PENDENTE]

- Como tornar a solução atrativa para estabelecimentos com faturamento menor?
- Qual o custo real por produto 3D e o tempo de captura/preparo?
- RealityScan ou KIRI entrega melhor qualidade para alimentos?
- Quanto do processo no Blender pode ser automatizado?
- Quantos produtos 3D devem existir em cada plano?
- Qual nível de realismo é possível mantendo carregamento rápido no celular?
- Modelo de cobrança do 3D/AR: setup + mensalidade, mensalidade apenas, ou por quantidade de produtos? (ver também a proposta alternativa do Xande em [`03-precificacao.md`](03-precificacao.md))

## Próxima validação — POC — [HIPÓTESE ESTRATÉGICA], não executada

Plano descrito na fonte, sem confirmação de execução: selecionar um produto real → captura de alta qualidade → reconstrução no RealityScan → comparar com KIRI Engine se necessário → tratar no Blender → corrigir escala real → exportar GLB → testar visualização 3D no navegador → testar AR sobre uma mesa → medir tempo total, qualidade e tamanho do arquivo.

A meta "Scaneamento 3D" na database real de metas (ver [`08-metas-roadmap.md`](08-metas-roadmap.md)) está marcada como **Concluída** — mas esta seção do produto não teve acesso ao detalhe do que especificamente foi testado ou concluído dentro dela; é uma lacuna, não uma inferência preenchida.

## Modelo de negócio — [HIPÓTESE ESTRATÉGICA]

Não é "vender um site" — é digitalização 3D do cardápio + plataforma mensal, com planos variando conforme a quantidade de produtos digitalizados. Isso é uma hipótese de modelo de negócio discutida no material de propósito do projeto, não uma decisão fechada.
