# Page: captura

URL: `/captura/`

## Brief

- **Purpose:** Capturar inscrições (e-mail) para as aulas ao vivo de traqueamento — toda terça-feira.
- **Offer:** Aulas ao vivo, semanais (terça), sobre traqueamento.
- **CTA URL:** (formulário — destino do POST ainda não definido)
- **Integrations:** Pendente — definir destino do formulário (ESP, webhook, CRM).
- **Deadline / launch date:** —

## Notes

- Formulário faz apenas um "fake submit" no cliente: mostra estado de sucesso inline.
  Antes de publicar, conectar o `form` a um destino real (ex.: Mailchimp, ConvertKit,
  webhook para CRM) e remover/ajustar o handler em `<script defer>` no final do HTML.
- Sem imagem de hero: o `<link rel="preload">` do template foi removido de propósito.
- Design inspirado em stripe.com/br — gradientes suaves em `::before`/`::after`,
  tipografia com `-apple-system` e headline com acento em gradiente.

## Change log

- 2026-04-21 — initial scaffold
