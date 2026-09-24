# vence-site

Página de divulgação do Vence (pré-lançamento). Site estático, sem build: um `index.html` com CSS/JS inline e as imagens em `assets/`.

## Testar localmente

```bash
cd vence-site
python3 -m http.server 8000
```

Abra `http://localhost:8000`.

## Publicar com domínio da Squarespace

O plano da Squarespace não permite subir uma página HTML própria inteira — só um Code Block dentro do editor. Por isso este site é hospedado de graça em outro lugar (GitHub Pages, Vercel ou Netlify) e o domínio da Squarespace só aponta para lá via DNS. O conteúdo continua 100% seu; você só usa a Squarespace como registrador do domínio.

### Opção A — GitHub Pages (mesmo esquema do vence-legal)

1. Crie um repositório novo (ex: `vence-site`) e suba esta pasta:
   ```bash
   cd vence-site
   git init
   git add .
   git commit -m "Site de divulgação do Vence"
   gh repo create vence-site --public --source=. --push
   ```
2. No GitHub, em **Settings → Pages**, source = branch `main`, pasta `/ (root)`.
3. Em **Settings → Pages → Custom domain**, informe seu domínio (ex: `vence-app.com`) — isso cria um arquivo `CNAME` no repositório.
4. Na Squarespace, em **Configurações → Domínios → [seu domínio] → DNS Settings**, adicione:
   - 4 registros **A** no `@` apontando para:
     `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - 1 registro **CNAME** em `www` apontando para `SEU-USUARIO.github.io`
5. Espere a propagação (minutos a poucas horas) e ative **Enforce HTTPS** em Pages.

### Opção B — Vercel ou Netlify

Mais simples para SSL e subdomínios: conecte o repositório (ou arraste a pasta) no painel deles, depois em **Domains** adicione seu domínio da Squarespace — cada um te dá o registro CNAME/A exato para colar no DNS da Squarespace.

## Antes de publicar de verdade

- Trocar o link `mailto:suporte@vence-app.com` do botão "Avise-me no lançamento" se o e-mail de suporte mudar.
- Trocar o pill "chegando em breve" e o botão do topo pelo badge oficial "Baixar na App Store" assim que o app for aprovado (baixe o artwork em [tools.applemediaservices.com](https://tools.applemediaservices.com)) e linkar para a ficha na App Store.
- Confirmar `og:url` em `index.html` com o domínio final.
