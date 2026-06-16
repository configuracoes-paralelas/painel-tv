# Painel TV Metrocasa — App (PWA)

App instalável na tela inicial do celular/TV, com ícone de TV vermelha, abrindo em
tela cheia (sem a barra do navegador).

## Arquivos (mantenha TODOS na mesma pasta)
- `index.html` — o painel
- `manifest.webmanifest` — define nome, cores e ícones do app
- `sw.js` — service worker (necessário para instalar)
- `icon-192.png`, `icon-512.png` — ícones padrão
- `icon-maskable-192.png`, `icon-maskable-512.png` — ícones do Android (formato adaptável)
- `apple-touch-icon.png` — ícone do iPhone/iPad
- `favicon.png`, `favicon-32.png` — ícone da aba do navegador

## IMPORTANTE: precisa estar num servidor HTTPS
Para o celular oferecer "instalar app" e usar o ícone, os arquivos têm que ser
**servidos por um site (https://...)**. Abrir o `index.html` direto do arquivo
(file://) mostra o painel, mas NÃO permite instalar como app.

Opções gratuitas e simples de hospedar (é só arrastar a pasta):
- **Netlify Drop** — https://app.netlify.com/drop
- **GitHub Pages**
- **Cloudflare Pages**
Ou qualquer servidor/hospedagem que você já use, contanto que tenha HTTPS.

## Como instalar na tela inicial

### Android (Chrome)
1. Abra o endereço do painel no Chrome.
2. Menu (⋮) → **Adicionar à tela inicial** / **Instalar app**.
3. O ícone da TV vermelha aparece na tela inicial e abre em tela cheia.

### iPhone / iPad (Safari)
1. Abra o endereço no **Safari** (precisa ser o Safari).
2. Botão **Compartilhar** (quadrado com seta para cima).
3. **Adicionar à Tela de Início** → Adicionar.

### TV / computador (Chrome/Edge)
- Aparece um ícone de instalar na barra de endereço, ou em Menu → "Instalar Painel TV".

## Observações
- A primeira vez precisa de internet. Depois, se cair a conexão, o app ainda abre
  (mostra a última casca carregada); os dados do Google Sheets só atualizam com internet.
- O service worker **não** mexe nas requisições do Google Sheets — os dados continuam
  sempre vindo ao vivo da rede, nunca presos no cache.
- Se você atualizar o painel no futuro, troque a versão do cache em `sw.js`
  (linha `const CACHE = "painel-tv-v1"` → `v2`, `v3`, ...) para forçar a atualização
  nos aparelhos já instalados.
