# LP Educação Financeira - Redesigner

Redesign da página de **Educação Financeira** da [Meu Patrimônio](https://meupatrimonio.com), construída sobre o esqueleto da home ([MP-Home-Redesigner](https://github.com/MarketingMPI/MP-Home-Redesigner)), em paleta **branco + cinza (sem verde)**.

Hoje esse conteúdo vive em `meupatrimonio.com/vitrine-de-cursos-e-materiais-gratuitos/`.

## Stack

HTML, CSS e JavaScript puros, sem framework nem build. Fonte Campton, ícones Bootstrap Icons via CDN.

## Padrão herdado da home

Header e rodapé da home são o **padrão para todas as páginas** do site.

- `styles.css` é o mesmo design system da home, com os tokens remapeados para uma escala neutra (ver abaixo). Todos os componentes (hero, pain-grid, ps-pillars, stats, offer-cards, botões, submenu, footer) vêm idênticos.
- Header, menu mobile e rodapé (5 colunas + endereços Vitória/Santos + barra legal) são cópia fiel da home.
- `app.js` é o mesmo da home (header no scroll, menu mobile, reveal, contadores, tabs, player), acrescido do accordion do FAQ.

## Estrutura das seções

| # | Seção | Equivalente na home |
|---|---|---|
| 1 | Hero | Hero |
| 2 | O problema | Dor |
| 3 | A nossa solução | Solução |
| 4 | Quem ensina | Autoridade |
| 5 | **O canal no YouTube** | exclusivo |
| 6 | Cursos e materiais | O que fazemos |
| 7 | Onde mais acompanhar | exclusivo |
| 8 | MP PRO | exclusivo |
| 9 | FAQ | exclusivo |

## Paleta (tokens remapeados)

Os **nomes** dos tokens da home foram mantidos e só os valores mudaram, para o CSS herdado funcionar sem edição:

| Token | Home (verde) | Aqui (cinza) |
|---|---|---|
| `--forest` | `#00503c` | `#5e666e` |
| `--deep` | `#003326` | `#3f464d` |
| `--signal` | `#00a611` | `#69727d` |
| `--mint` | `#61ce70` | `#c3cad0` |
| `--ink` | `#00503c` | `#26292d` |
| `--paper` / `--mist` | off-white esverdeado | `#ffffff` / `#f6f7f8` |

Fotos aplicadas em `grayscale(1)`. Exceções propositais: a capa do MP PRO (logo oficial em dourado) e a thumbnail do vídeo em destaque, ambas coloridas.

## Canal no YouTube

Fonte: [youtube.com/@Gabriel_Liberato](https://www.youtube.com/@Gabriel_Liberato) (channel ID `UCyNEaDK2LrMdO4rwBLutrAg`), apresentado por Gabriel Liberato, CFP e analista CNPI.

**Os vídeos são atualizados manualmente.** Para pegar os mais recentes:

```bash
curl -s "https://www.youtube.com/feeds/videos.xml?channel_id=UCyNEaDK2LrMdO4rwBLutrAg" -o feed.xml
grep -oP '(?<=<yt:videoId>)[^<]+' feed.xml    # IDs
grep -oP '(?<=<media:title>)[^<]+' feed.xml   # títulos
```

Thumbnail: `https://i.ytimg.com/vi/<VIDEO_ID>/hqdefault.jpg`

## Rodar localmente

```bash
python -m http.server 4181 --bind 127.0.0.1
# abrir http://127.0.0.1:4181/
```

Ao editar CSS/JS, incrementar `?v=N` no `<link>` e no `<script>` do `index.html` para furar o cache do navegador.

## Estrutura de arquivos

```
index.html      # marcação de todas as seções
styles.css      # design system (tokens + componentes)
app.js          # interações
assets/
  fonts/        # Campton (.woff2)
  img/          # fotos, logos, selos
  materiais/    # capas dos ebooks e ferramentas (768x960)
  orbit/        # logos de instituições
  products/     # capas de produtos
```
