# REG — Playbook do Diagnóstico

Processo interno de execução do Diagnóstico (R$297). Objetivo: entregar um relatório real em até 3 dias úteis após receber acesso, que sirva como prova de valor pro upsell natural pro Gerenciado.

**Garantia ativa no site (`index.html`):** se o Diagnóstico não encontrar pelo menos 3 problemas reais e acionáveis, reembolso total, sem perguntas. Na prática o risco é baixíssimo — qualquer conta sem função de growth dedicada tem pelo menos 3 problemas reais (é raro o caso em que não tem) — mas trate o reembolso como compromisso sério se algum dia for pedido: via Stripe Dashboard → Payments → Refund, no pagamento correspondente. Não questionar, não negociar — é a promessa que está no site.

## 0. Depois do pagamento — coleta de acesso

Envie o e-mail de coleta de acesso (template no fim deste doc) pedindo, no mínimo:

- **PostHog:** convite como membro do projeto (Settings → Members) — leitura já basta, não precisa de admin.
- **GA4** (se usar em vez de/junto com PostHog): acesso de "Viewer" na propriedade.
- **Ads:** acesso de "Analista" ou "Somente leitura" em cada plataforma que ele rodar — Meta Business Manager (Ads Manager), Google Ads, TikTok Ads Manager. Não precisa de acesso de edição.

Não comece a auditoria sem pelo menos analytics + 1 plataforma de ads liberados.

## 1. Auditoria de analytics (PostHog/GA4)

Checklist — marcar cada item como OK / QUEBRADO / AUSENTE:

- [ ] **Eventos-chave disparando** — signup, ativação (primeira ação de valor), evento de conversão/compra estão sendo capturados? Testar disparando cada um manualmente se possível.
- [ ] **Identidade unificada** — `person_id`/`distinct_id` (PostHog) ou User-ID (GA4) configurados corretamente? Checar se há duplicação de usuário entre sessões anônimas e logadas (problema clássico de identity merge).
- [ ] **Funil definido** — existe um funil de onboarding/ativação configurado como insight salvo? As etapas refletem o fluxo real do produto?
- [ ] **Propriedades de UTM chegando nos eventos** — `utm_source`, `utm_medium`, `utm_campaign` estão sendo capturados nos eventos de sessão/signup? Sem isso, não dá pra saber qual canal trouxe qual usuário.
- [ ] **Retenção trackeada** — existe insight de retenção D1/D7/D30, ou visão de coorte?
- [ ] **Dashboard existe e é usado** — tem um dashboard principal? Quando foi visto pela última vez (verificar last-viewed se disponível)?
- [ ] **Qualidade do dado** — eventos duplicados, nomenclatura inconsistente (ex: `Signup` e `sign_up` coexistindo), propriedades faltando em parte dos eventos.
- [ ] **Segmentação por plano/cohort** — dá pra segmentar usuário por plano, canal de aquisição, ou está tudo misturado num blob só?

## 2. Auditoria de ads (por plataforma ativa)

- [ ] **Pixel/API de conversão instalado e validando** — Meta Pixel + Conversions API, Google Ads tag, TikTok Pixel. Checar no Events Manager/Tag Assistant se está disparando sem erro.
- [ ] **Evento de conversão = evento de negócio real** — o pixel está otimizando pro evento certo (compra/signup pago), não um proxy fraco (ex: "ViewContent")?
- [ ] **Match rate da Conversions API** (Meta) — se abaixo de ~60-70%, é sinal de tracking capenga.
- [ ] **Estrutura de campanha** — nomenclatura consistente, não há campanhas ativas sem budget/sem otimização clara, não há sobreposição de público competindo consigo mesma.
- [ ] **Métricas-chave da semana**: CAC, CPC, CTR, frequência (fadiga de criativo > 3-4 costuma ser sinal de alerta), ROAS se aplicável.
- [ ] **UTM consistente** — os UTMs usados nos anúncios batem com o que o analytics espera capturar (ver item de analytics acima)?
- [ ] **Risco de política** — algum criativo/copy com claim que pode gerar rejeição ou taxa de disputa alta (promessa de resultado financeiro específico, por exemplo)?

## 3. Auditoria de landing page / CRO

Fecha o funil que a auditoria de ads deixa em aberto — de nada adianta clique bem trackeado numa página que vaza. Referência: prática validada em escala pela V4 Company (maior rede de marketing digital do Brasil), adaptada ao escopo do REG.

- [ ] **Promessa do anúncio bate com a página** — o criativo/copy do anúncio promete a mesma coisa que a landing page entrega logo no topo? Divergência aqui é a causa nº1 de clique caro sem conversão.
- [ ] **CTA único e claro** — a página tem um caminho de conversão óbvio, ou compete consigo mesma com múltiplos CTAs concorrentes?
- [ ] **Fricção de formulário/checkout** — quantos campos até converter? Cada campo a mais é abandono a mais.
- [ ] **Velocidade de carregamento** — mobile principalmente (testar via PageSpeed Insights); tráfego pago BR é majoritariamente mobile.
- [ ] **Mystery shopper** — se fizer sentido pro caso, o próprio Caio se passa por lead (preenche o formulário, manda mensagem) e registra a experiência real de resposta: tempo até contato, qualidade do primeiro retorno. Módulo opcional, alto valor percebido, baixo esforço.

## 4. Estrutura do relatório final

Entregar como página/documento, seguindo esta ordem (achado mais crítico primeiro, sempre):

1. **Resumo executivo** — 3-5 bullets, achados mais críticos, sem jargão. Cada bullet: o que está quebrado → o impacto real (não "isso é uma boa prática", e sim "por isso você não sabe se X está funcionando").
2. **Analytics — o que está quebrado/faltando** — checklist da seção 1 preenchido, com nota de severidade (crítico/médio/nice-to-have).
3. **Ads — o que está quebrado/ineficiente** — checklist da seção 2 preenchido, mesma lógica de severidade.
4. **Landing page/CRO — onde o funil vaza depois do clique** — checklist da seção 3 preenchido; incluir achado do mystery shopper se aplicado.
5. **Quick wins (essa semana)** — 3-5 ações concretas, cada uma com o "porquê" e o esforço estimado (ex: "30 min, requer acesso admin ao PostHog").
6. **Roadmap 30-60 dias** — o que resolver depois dos quick wins, geralmente mais estrutural (redesenhar funil, unificar identidade, etc.).
7. **Fechamento natural pro Gerenciado** — só se fizer sentido genuíno pro caso (não forçar): "esses itens do roadmap são exatamente o que o Gerenciado cobre continuamente."

## Template — e-mail de coleta de acesso

```
Assunto: REG — acesso pra começar seu Diagnóstico

Oi [nome],

Recebi seu pagamento do Diagnóstico! Pra começar, preciso de acesso de leitura
(não precisa dar admin) em:

1. PostHog (ou GA4) — me convida como membro/viewer do projeto
2. [Meta Ads / Google Ads / TikTok Ads, o que você rodar] — acesso de analista
   ou somente leitura no gerenciador de anúncios

Assim que eu tiver isso, o relatório sai em até 3 dias úteis.

Qualquer dúvida sobre como dar acesso, me chama.

Caio
```
