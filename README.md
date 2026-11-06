# Masterclass Impulse · IA aplicada à barbearia

Página de vendas (`/`) e página de obrigado (`/obrigado/`) da masterclass de Silvana Rosa e Mateus Barone.
Site estático servido por **Nginx** em **Docker**, pronto para o **Easypanel**.

Rastreamento já instalado nas duas páginas:
- Google Tag Manager: `GTM-NFG6G89X`
- Pixel da Meta: `1316986016846604` (PageView + InitiateCheckout na LP e Purchase na página de obrigado)

## Deploy no Easypanel

1. **Create Project** → dê um nome (ex.: `masterclass`).
2. **+ Service → App**.
3. Aba **Source → GitHub**:
   - Owner: `inscricaoworkshopbarber-creator`
   - Repository: `masterclass-impulse`
   - Branch: `main`
   - Build Path: `/`
4. Aba **Build → Dockerfile** (arquivo `Dockerfile` na raiz).
5. Clique em **Deploy**.
6. Aba **Domains**: adicione o seu domínio (ex.: `masterclass.seudominio.com.br`) com **Port 80** e HTTPS ligado.
7. No DNS do domínio, crie um registro **A** apontando para o IP do servidor do Easypanel.

Para atualizar a página: envie as alterações para a branch `main` e clique em **Deploy** (ou ative o Auto Deploy).

## Estrutura

```
site/index.html            página de vendas
site/obrigado/index.html   página de obrigado (configure como URL de obrigado na Greenn)
Dockerfile                 imagem nginx:alpine
nginx.conf                 configuração do servidor
```

## Testar localmente

```bash
docker build -t masterclass-impulse .
docker run -p 8080:80 masterclass-impulse
# abra http://localhost:8080
```
