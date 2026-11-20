# EOM - Espaço OM Dourado (site)

Landing page estática (HTML, CSS e JS puros, sem build). Pronta para o Vercel.

## Publicar
1. Subir esta pasta num repositório do GitHub.
2. No Vercel do cliente: Add New Project, importar o repositório, Framework Preset "Other", sem comando de build, Output Directory vazio (raiz).
3. Adicionar o domínio do cliente em Settings > Domains.

## Antes de publicar (pendências)
- **Domínio:** o site usa `https://www.espacoomdourado.com.br` como provisório no canonical, Open Graph, JSON-LD, robots.txt e sitemap.xml. Trocar todos de uma vez:
  `grep -rl "espacoomdourado.com.br" . | xargs sed -i 's#https://www.espacoomdourado.com.br#https://DOMINIO-REAL#g'`
- **Já confirmado no perfil do Google (17/11):** link do perfil (`https://www.google.com/maps?cid=5859809136633489203`), horário (seg a sex 9h às 18h, sáb 9h às 16h, dom fechado), coordenadas e as 3 avaliações usadas no site.
- **Vídeo do espaço:** o hero tem um bloco "Espaço reservado para o vídeo". Ao receber o vídeo, trocar o bloco `.video-reservado` pelo vídeo.
- **Logo:** o ícone atual é provisório; trocar pela logo do Henrique.

## Preços (futuro)
Cada tratamento tem `<span class="preco" data-preco hidden></span>`. Para exibir, preencher o texto (ex.: "A partir de R$ 000") e remover o atributo `hidden`.

## Medição
Todo clique relevante tem `data-evento`: `whatsapp_click`, `phone_click`, `location_click`, `google_profile_click` (e `instagram_click`), com `data-local` indicando a posição. O script envia para `dataLayer` (Google Tag Manager), `gtag` (GA4) e Vercel Analytics, se estiverem instalados. Basta adicionar a tag escolhida no `<head>`; a CSP do `vercel.json` já libera GTM/GA4 e Vercel Analytics.

## Arquivos
- `index.html`: página, CSS crítico e JS inline (um único arquivo para carregar rápido).
- `assets/fonts/`: Young Serif (títulos) e Figtree (texto), auto-hospedadas.
- `og-image.jpg`, ícones, `site.webmanifest`, `robots.txt`, `sitemap.xml`, `404.html`.
- `vercel.json`: cabeçalhos de segurança e cache.
