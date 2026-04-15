# Circula — Gerador de Comunicados Escolares

Sistema SaaS com IA para geração de comunicados escolares padronizados.

## Deploy via GitHub Pages

### 1. Criar repositório no GitHub
- Acesse github.com → New repository
- Nome: `circula-app` (público)
- Não inicialize com README

### 2. Subir os arquivos
```bash
git init
git add .
git commit -m "🚀 Circula — lançamento inicial"
git branch -M main
git remote add origin https://github.com/SEU_USUARIO/circula-app.git
git push -u origin main
```

### 3. Ativar GitHub Pages
- Settings → Pages → Source: "Deploy from branch" → main → / (root)
- Aguarde ~2 min → acesse: `https://SEU_USUARIO.github.io/circula-app/`

## Configuração do Firebase

### 1. Criar projeto
- Acesse console.firebase.google.com
- Create project → "circula-app"
- Ativar Authentication → Email/Password + Google
- Ativar Firestore → modo de produção

### 2. Regras do Firestore
```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /users/{userId} {
      allow read, write: if request.auth != null && request.auth.uid == userId;
    }
  }
}
```

### 3. Cole as credenciais em app.html
Substitua as linhas `COLE_SEU_*` pelas credenciais do seu projeto Firebase.

## Estrutura de cobrança (Stripe — futuro)
- Plano Free: 10 comunicados/mês (controlado via Firestore)
- Plano Pro: R$ 97/escola/mês — ilimitado
- Campo `plan` no Firestore: 'free' | 'pro'

## Domínio personalizado (opcional)
- Compre `circula.app` ou similar em registro.br
- Adicione CNAME no GitHub Pages Settings
