# REG — Stripe

Conta: `acct_1TPZ5OKtWahGMnv9` ("Caio Borges"), **modo live** (mesma conta do Winlist).

## Produtos

| Item | Produto ID | Preço | Price ID |
|---|---|---|---|
| REG Diagnóstico | `prod_V6LzhZi4RDCuJk` | R$497,00 (BRL, pagamento único) | `price_1U6DJxKtWahGMnv9OBnQKFRl` |

**Payment Link ativo:** `plink_1U6DKOKtWahGMnv9TtkNQm8E` → https://buy.stripe.com/9B628s2xe9xk4wG2HI6Ri02 — funcionando de verdade, cartão. Pix/boleto não ativados (mesma pendência do Winlist).

**Payment Link antigo (R$297), desativado:** `plink_1U69HgKtWahGMnv9wesPCWqv` — `active: false`, mantido só como histórico. Price antiga `price_1U69HYKtWahGMnv9ZN6XhyjH` também não usar mais (Stripe não permite editar preço de um Price existente — sempre criar um novo).

## Por que Gerenciado não tem checkout

Retainer de venda assistida — o CTA abre e-mail pra agendar conversa, não Payment Link. Faz sentido criar o checkout recorrente **depois** da conversa de onboarding, quando o escopo com o cliente estiver alinhado (evita vender algo genérico demais pra um serviço que é, por natureza, personalizado).

## Próximos passos

- Publicar GitHub Pages (mesmo processo do Winlist — `git push` bloqueado no ambiente, rodar manualmente).
- Ativar Pix.
- Se/quando o Gerenciado fechar o primeiro cliente: criar Price recorrente (`recurring: month`) específico e, aí sim, decidir se vira Payment Link ou Checkout Session com fatura manual.
