# Page: vendas

URL: `/vendas/`

## Brief

- **Purpose:** Página de vendas de um curso — estrutura de copy pronta, com placeholders em lorem ipsum.
- **Offer:** Curso completo (placeholder).
- **CTA URL:** `#preco` (âncora interna) — ajustar para checkout real antes de publicar.
- **Integrations:** Pendente — botão "Quero me inscrever" precisa de destino (Hotmart/Kiwify/Stripe/etc).
- **Deadline / launch date:** —

## Structure

1. Sticky nav + wordmark
2. Hero (headline + subhead + CTA + fine print)
3. Módulos e entregáveis (grid 2×2)
4. Depoimentos (3 cards)
5. Para quem é (big quote)
6. Preço (price card com glow, lista de entregáveis, CTA)
7. Professor (card com avatar + bio + credenciais)
8. FAQ (details/summary nativo)
9. CTA final

## Notes

- Toda a copy é lorem ipsum — substituir antes de publicar.
- Avatares são placeholders em gradiente com iniciais (MS, RC, JA, LI). Trocar por imagens reais (`/vendas/assets/...`) e lembrar do `loading="lazy"`.
- Preço: R$ 497 hardcoded — ajustar.
- O `.price-wrap::before` gera um glow suave atrás da caixa de preço. Se ficar pesado em mobile, reduzir o blur ou remover.
- FAQ usa `<details>` nativo — não precisa de JS.

## Change log

- 2026-04-21 — initial scaffold
