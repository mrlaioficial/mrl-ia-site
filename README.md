# Site do MRL.AI (GitHub Pages)

Site de vendas estático. **Este repositório deve ser separado do sistema** (que fica privado): o GitHub Pages
gratuito exige repositório público, e o código do painel, as chaves e o banco nunca podem ir para ele.

## O que editar (`public/config.json`)
| Campo | O que é |
|---|---|
| `appUrl` | Endereço do painel, com https (ex.: `https://app.seudominio.com.br`). Liga os botões "Entrar" e os links de privacidade |
| `contact.email` | E-mail de contato (aparece no rodapé) |
| `plans.solo.checkoutUrl`, `plans.duo.checkoutUrl`, `plans.agencia.checkoutUrl` | Um link de pagamento por plano (Solo R$ 39,90, Duo R$ 59,90, Agência R$ 149,90, cobrança única), criados no Asaas (veja `BILLING.md` do sistema). Precisam começar com `https://`. Plano sem link fica como "Em breve" |

Os preços (R$ 39,90, R$ 59,90 e R$ 149,90) estão escritos no `index.html`. **Se mudar o valor, troque também lá e no `ASAAS_PLAN_MAP` do sistema, se usar.**
Sem o link de pagamento, o botão da oferta fica desativado ("Em breve").

## Publicar no GitHub Pages
1. Crie um repositório **público** (ex.: `mrl-ia-site`) e envie esta pasta:
   ```powershell
   git init -b main
   git add .
   git commit -m "Site do MRL.AI"
   git remote add origin https://github.com/SEU-USUARIO/mrl-ia-site.git
   git push -u origin main
   ```
2. No GitHub: **Settings → Pages → Build and deployment → Source: GitHub Actions**.
3. O workflow `.github/workflows/pages.yml` publica a pasta `public/` a cada push na `main`.
   O endereço fica `https://SEU-USUARIO.github.io/mrl-ia-site/`.

### Domínio próprio (opcional)
Crie `public/CNAME` com uma linha, o domínio (ex.: `www.seudominio.com.br`), aponte o DNS (CNAME para
`SEU-USUARIO.github.io`) e marque **Enforce HTTPS** em Settings → Pages.

## Página de obrigado
`public/obrigado.html`: use este endereço como destino após o pagamento no link de pagamento do Asaas.

## Testar localmente
```powershell
cd public
python -m http.server 8200
```
Abra http://localhost:8200.
