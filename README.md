# mykeymate.com — site estático

Site institucional do **Keymate** (quartos verificados + match de roommate, foco Irlanda).
HTML/CSS/JS puro, sem build e sem backend. Publicado em https://www.mykeymate.com

> Não confundir com o **app funcional** (Next.js + Prisma), que vive em `ahuttener/keymate-app`.

## Estrutura

- 17 páginas `.html` na raiz (`index.html` é a landing).
- `img/` — fotos dos quartos (`room1..19.webp`).
- Cada página traz embutidos: a logo (data URI), o motor de i18n `km-i18n v2` e seu dicionário PT.

## Modo comunidade brasileira

O site nasce em inglês. Ao escolher a nacionalidade "Brazilian" (em `prefs.html`/`edit-profile.html`)
ou clicar na barra 🇧🇷 da home, grava-se `localStorage.km_lang = 'pt'`: as páginas passam a
traduzir os text-nodes pelo dicionário e a logo troca para a variante verde. Persiste na navegação.

## Convenções que não dá para deduzir do código

- **Um selo de verificação por card, nunca dois:**
  - card de quarto (tem foto) → pílula `.vf` "Verified" sobre a imagem;
  - card de pessoa (`article.card.seeker`, sem foto) → ícone `svg.verified` ao lado do nome.
- **Rótulo de match** segue os limiares da legenda de `listing.html`:
  90%+ Excellent · 80–89 Great · 70–79 Good · abaixo de 70 "proceed with caution".
- Em `listing.html` o badge da galeria fica **sem** rótulo de propósito: a página já mostra
  o tier por extenso ao lado do anel de compatibilidade.
- Bandeiras são **SVG inline**, nunca emoji — Windows e vários Androids não renderizam
  emoji de bandeira de país.
- Vários badges têm `style=` inline; regex de manutenção precisa aceitar atributos extras
  (`<span class="badge-match"[^>]*>`).

## Publicar

Deploy pela Hostinger via Git (hPanel → Avançado → Git). Um `git push` na `main`
seguido de "Deploy" no painel atualiza https://www.mykeymate.com
