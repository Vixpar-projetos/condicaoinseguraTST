# Vixpar | Condição Insegura

Sistema Next.js preparado para Netlify e Supabase, com formulário público por QR Code, painel administrativo, editor de formulário, tratamento de ocorrências, apresentação de indicadores e exportação XLSX.

## 1. Configurar Supabase
1. Crie um projeto novo no Supabase.
2. Abra o SQL Editor e execute `supabase/schema.sql`.
3. Em Storage, crie um bucket **privado** chamado `occurrence-photos`.
4. Copie a Project URL e a Service Role Key.

## 2. Variáveis de ambiente
Copie `.env.example` para `.env.local` e preencha:
- `NEXT_PUBLIC_SUPABASE_URL`
- `SUPABASE_SERVICE_ROLE_KEY`
- `ADMIN_USERNAME`
- `ADMIN_PASSWORD`
- `ADMIN_SESSION_SECRET` com pelo menos 32 caracteres
- `NEXT_PUBLIC_APP_URL` com a URL final do Netlify

A Service Role fica apenas no servidor. Não use a chave no navegador.

## 3. Rodar localmente
```bash
npm install
npm run dev
```
Acesse `http://localhost:3000`.

## 4. Publicar no Netlify
1. Envie o projeto para GitHub/GitLab ou faça deploy manual do repositório.
2. No Netlify, importe o projeto.
3. Build command: `npm run build`.
4. O arquivo `netlify.toml` já está incluído.
5. Cadastre no Netlify as mesmas variáveis do `.env.local`.
6. Faça o deploy.
7. Depois de receber a URL definitiva, ajuste `NEXT_PUBLIC_APP_URL` e faça novo deploy para o QR Code apontar para o endereço correto.

## Rotas
- `/formulario` formulário público
- `/login` login administrativo
- `/admin` painel
- `/admin/formulario` editor dinâmico
- `/admin/apresentacao` indicadores
- `/admin/ocorrencias/[id]` tratamento

## Segurança
- APIs administrativas protegidas por cookie HTTP-only assinado.
- Dados e fotos são manipulados server-side usando Service Role.
- Bucket de fotos deve permanecer privado.
- QR Code dá acesso somente ao formulário público.
- RLS está habilitado sem policies públicas.

## Logos
Os arquivos enviados foram incorporados em `public/`:
- `logo-vix-55.png`
- `cuidar-e-agir-modelo.png`
# vixpar-condicaoinsegura
# condicaoinseguraTST
# condicaoinseguraTST
