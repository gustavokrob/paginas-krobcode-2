# Page: lp-do-sobral

URL: `/lp-do-sobral/`

## Brief

- **Purpose:** Captura de inscrições (nome + e-mail) para o evento online "A Nova Gestão de Tráfego" — réplica visual da LP de referência do Pedro Sobral (`ads-a-v2`).
- **Offer:** Vaga gratuita no evento de 18 a 24 de maio, às 20h. Conteúdo inédito sobre tráfego pago.
- **CTA URL:** (formulário inline — destino do POST ainda não definido)
- **Integrations:** Pendentes — ver TODOs abaixo.
- **Deadline / launch date:** —

## TODOs antes de publicar

- [ ] **Foto do palestrante:** substituir `assets/hero.webp` (placeholder atualmente) pela foto real do Sobral. Aspect ratio esperado: ~520×600 (já fixado nos atributos `width`/`height` para evitar CLS).
- [ ] **OG image:** substituir `assets/og.jpg` (placeholder).
- [ ] **Endpoint do form:** o handler em `<script defer>` no fim do HTML faz fake-submit no client. Conectar a destino real (Mailchimp, ConvertKit, webhook, etc.) e ajustar/remover o handler.
- [ ] **Páginas legais:** os 3 links do footer (`Política de Privacidade`, `Política de Cookies`, `Termos de Uso`) apontam para `#`. Trocar pelas URLs reais.
- [ ] **Trackers:** Meta Pixel, GA4, etc. Slots de `<link rel="preconnect">` já estão comentados no `<head>` para quando entrarem.
- [ ] **Link do grupo do WhatsApp:** o `<a id="quizWhats">` no final do quiz aponta para `#`. Substituir pela URL real do grupo (`https://chat.whatsapp.com/...`).
- [ ] **Persistir respostas do quiz:** o quiz hoje só guarda `{ leadData, answers }` em memória. Ponto de integração marcado por `// TODO` em `showFinish()` no `<script defer>` — enviar pro banco quando pronto.

## Notes

- **Identidade própria:** esta página NÃO segue a paleta Stripe-style do resto do repo (`/captura`, `/vendas`, `/links`). Fonte é `Barlow` via Google Fonts; fundo preto + bloco azul royal (`#1e40af`) + CTA verde-limão (`#84cc16`).
- **Layout:** desktop é split 2 colunas (esquerda preta com headline + form; direita azul com logo + chips + foto), com 2 faixas verticais decorativas de 32px nas bordas. Mobile (≤900px) faz stack vertical e some com as faixas.
- **Logo do evento:** composição em CSS puro (`<div class="logo">`), não é imagem. Linha "A NOVA" + régua + "GESTÃO *de* TRÁFEGO" (com "de" em itálico). Reaproveitada no header da coluna direita e no footer.
- **Faixas decorativas:** texto `#ANOVAGESTAODETRAFEGO` repetido na vertical via `writing-mode: vertical-rl`. Texto exato da referência era ilegível nos screenshots — ajustar quando confirmado.
- **Form:** 2 inputs (nome + e-mail) em grid 2-col no desktop, 1-col no mobile. CTA full-width abaixo. Validação HTML5 + handler client-side. No submit válido, esconde o form e abre o quiz modal (ver abaixo).
- **Quiz de qualificação pós-form:** modal não-fechável (sem X, sem ESC, sem backdrop-close) com até 5 perguntas single-choice em sequência (idade, gênero, escolaridade, conhecimento prévio sobre tráfego pago, experiência subindo anúncios). UI: card branco sobre overlay escuro, radios custom, botão azul "Próxima" (desabilitado até selecionar) + "Voltar" (some na Q1). Lista de perguntas hardcoded no array `QUESTIONS` dentro do `<script defer>`. Respostas ficam em memória (`answers`) — destino futuro é banco.
- **Bifurcação por escolaridade (Q3):** o quiz tem dois desfechos. Se a resposta de Q3 for exatamente `Superior completo` (constante `QUALIFYING_EDUCATION`), o lead segue pra Q4 e Q5 e termina na tela `#quizFinish` com o CTA verde "Entrar no grupo do WhatsApp" (`<a id="quizWhats" href="#">` — TODO trocar pelo link real). Qualquer outra resposta encerra o quiz logo após Q3 e mostra `#quizDecline` ("Obrigado pela sua participação… inscrição confirmada por e-mail") — sem CTA pro WhatsApp. Q4 e Q5 não são coletadas nesse caminho. Para mudar o critério, ajustar `EDUCATION_QUESTION_INDEX` / `QUALIFYING_EDUCATION` no topo da IIFE do `<script defer>`.
- **Acessibilidade:** labels com `.sr-only`, `<noscript>` com fallback, contraste OK (verde lime sobre preto + branco sobre azul royal). Modal usa `role="dialog"` + `aria-modal="true"` + `aria-labelledby` apontando pra pergunta atual; `h2.quiz-question` com `tabindex="-1"` recebe foco programático a cada step.

## Change log

- 2026-05-07 — initial scaffold
- 2026-05-07 — add post-signup qualification quiz modal (5 perguntas → CTA WhatsApp)
- 2026-05-07 — quiz: bifurcar por escolaridade (Q3). Só "Superior completo" segue pra Q4/Q5 + CTA WhatsApp; demais encerram com tela de agradecimento
