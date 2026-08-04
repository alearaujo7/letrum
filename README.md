# Letrum — Ideias transformadas em palavras

Aplicação de página única (HTML + CSS + JS puro, sem build), conectada a um
projeto real no Supabase (autenticação, banco de dados e storage).

Não há passo de build: `index.html` é o site inteiro. Isso significa deploy
em qualquer host estático — GitHub Pages, Vercel, Netlify — sem configuração.

## 1. Subir para o GitHub

```bash
cd letrum-projeto
git init
git add .
git commit -m "Letrum — versão inicial"
```

Crie um repositório vazio em https://github.com/new (sem README, sem
.gitignore — já vamos ter os nossos), depois:

```bash
git remote add origin https://github.com/SEU-USUARIO/letrum.git
git branch -M main
git push -u origin main
```

## 2. Publicar no Vercel

1. Acesse https://vercel.com/new
2. Clique em **Import Git Repository** e selecione o repositório `letrum`
3. Em **Framework Preset**, escolha **Other** (site estático, sem build)
4. Não é preciso configurar variáveis de ambiente — a chave pública do
   Supabase já está no `index.html` (é a chave `publishable`/`anon`,
   feita para ficar exposta no navegador; as regras de segurança reais
   vivem no Postgres via Row Level Security)
5. Clique em **Deploy**

Em cerca de um minuto o site estará no ar em `https://letrum-xxxx.vercel.app`,
fora do sandbox do Claude — a busca, login, aplausos e tudo mais vão
funcionar normalmente, porque o navegador real não bloqueia a chamada
para o Supabase como o preview de artefato bloqueava.

## 3. Domínio próprio (opcional)

Em **Project Settings → Domains** no Vercel, adicione seu domínio e siga
as instruções de DNS que eles mostram.

## Sobre o backend

O banco (Postgres + Auth + Storage) já está criado e populado no Supabase,
projeto `me-diga` (o nome interno do projeto não aparece em lugar nenhum
pro usuário final — só no painel do Supabase). Editar o schema, políticas
de segurança ou dados segue sendo feito por lá, não neste repositório.

Contas de demonstração (senha `demo12345`): marina@medemo.app,
heitor@medemo.app, aline@medemo.app, diego@medemo.app, julia@medemo.app,
camila@medemo.app, bruno@medemo.app.
