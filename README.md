# vence-site

Página de divulgação do Vence. Site estático, sem build: um `index.html` com CSS/JS inline e as imagens em `assets/`.

Publicado em produção: [vence-app.com](https://vence-app.com), via GitHub Pages, com o domínio comprado na Squarespace apontando pra cá por DNS (A + CNAME `www`; o MX/TXT do Google Workspace, usado no e-mail de suporte, ficam intactos).

## Testar localmente

```bash
cd vence-site
python3 -m http.server 8000
```

Abra `http://localhost:8000`.

## Publicar mudanças

É só commitar e dar push na branch `main` — o GitHub Pages republica sozinho em alguns segundos:

```bash
git add -A
git commit -m "..."
git push
```

## DNS na Squarespace

Domínio gerenciado em **Domínios → vence-app.com → DNS → DNS Settings**. Registros custom atuais:

- 4 **A** em `@` → `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153` (IPs do GitHub Pages)
- 1 **CNAME** em `www` → `heitor-sampaio-de.github.io.`
- MX + 2 TXT (SPF/DKIM) do Google Workspace — não mexer, é o e-mail `suporte@vence-app.com`.

O domínio customizado e o certificado HTTPS ficam configurados do lado do GitHub em **Settings → Pages** do repositório.

## Trocar o badge da App Store pelo oficial (opcional)

O botão "Baixar na App Store" usa um ícone simples desenhado à mão. Se quiser o selo oficial da Apple, baixe o artwork em [tools.applemediaservices.com](https://tools.applemediaservices.com) e troque o `<a class="btn">` no hero em `index.html`.
