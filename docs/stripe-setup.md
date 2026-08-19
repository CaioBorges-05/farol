# Farol — Stripe

Conta: `acct_1TPZ5OKtWahGMnv9` ("Caio Borges"), **modo live** (mesma conta do Winlist).

## Produtos

| Item | Produto ID | Preço | Price ID |
|---|---|---|---|
| Farol Diagnóstico | `prod_V6LzhZi4RDCuJk` | R$297,00 (BRL, pagamento único) | `price_1U69HYKtWahGMnv9ZN6XhyjH` |

**Payment Link:** `plink_1U69HgKtWahGMnv9wesPCWqv` → https://buy.stripe.com/00wfZi0p6fVI3sCeqq6Ri01 — funcionando de verdade, cartão. Pix/boleto não ativados (mesma pendência do Winlist).

## Por que Gerenciado não tem checkout

Retainer de venda assistida — o CTA abre e-mail pra agendar conversa, não Payment Link. Faz sentido criar o checkout recorrente **depois** da conversa de onboarding, quando o escopo com o cliente estiver alinhado (evita vender algo genérico demais pra um serviço que é, por natureza, personalizado).

## Próximos passos

- Publicar GitHub Pages (mesmo processo do Winlist — `git push` bloqueado no ambiente, rodar manualmente).
- Ativar Pix.
- Se/quando o Gerenciado fechar o primeiro cliente: criar Price recorrente (`recurring: month`) específico e, aí sim, decidir se vira Payment Link ou Checkout Session com fatura manual.
