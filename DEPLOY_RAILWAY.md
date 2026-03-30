# Deploy no Railway

## 1. Subir a API

- Crie um novo projeto no Railway.
- Escolha `Deploy from GitHub` ou suba esta pasta com o `Railway CLI`.
- Como existe um `Dockerfile`, o Railway vai usar essa imagem automaticamente.

## 2. Variaveis de ambiente

Use o arquivo `.env.example` como base e configure:

- `RESERVA_ALLOWED_ORIGINS=https://app.seudominio.com.br`
- `RESERVA_DB_URL=postgresql://...`

Se preferir, em vez de `RESERVA_DB_URL`, use:

- `RESERVA_DB_DRIVER=pgsql`
- `RESERVA_DB_HOST=...`
- `RESERVA_DB_PORT=5432`
- `RESERVA_DB_NAME=postgres`
- `RESERVA_DB_USERNAME=...`
- `RESERVA_DB_PASSWORD=...`
- `RESERVA_DB_SSLMODE=require`

## 3. Dominio customizado

- No Railway, adicione `api.seudominio.com.br`.
- Crie no Cloudflare o `CNAME api` apontando para o host informado pelo Railway.
- Para o primeiro deploy, prefira `DNS only`.

## 4. Validacao

Depois do deploy:

- `GET /` deve retornar status `ok`
- `GET /health.php` pode ser usado como healthcheck simples
- `GET /login.php` deve responder `405` se acessado com metodo incorreto

## 5. Observacao importante

Esta API agora aceita MySQL e PostgreSQL na conexao, mas a migracao completa para Supabase ainda depende de o schema do banco estar compatível com PostgreSQL.
