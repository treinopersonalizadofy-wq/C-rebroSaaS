# ⚙️ Automação — Setup Make.com + Claude API

→ [[SAAS]]

> Configuração completa da automação: formulário → Make.com → Claude API → email pro cliente.
> Após configurar, o cliente preenche o formulário e recebe o treino em 5–10 minutos automaticamente.

---

## VISÃO GERAL DO FLUXO

```
Cliente preenche o formulário
        ↓
Formulário dispara em paralelo:
  ① EmailJS → notificação para Gabriel (como antes)
  ② Webhook → Make.com (NOVO)
        ↓
Make.com recebe os dados estruturados do cliente
        ↓
Make.com chama a API do Claude (Anthropic)
        ↓
Claude gera o treino completo (~30 segundos)
        ↓
Make.com envia email com o treino para o cliente via Gmail
```

---

## PASSO 1 — CRIAR CONTA NA ANTHROPIC API

1. Acesse: **console.anthropic.com**
2. Crie uma conta (ou entre se já tiver)
3. Vá em **Settings → Billing** e adicione $5
4. Vá em **API Keys** → clique em **Create Key**
5. Copie a chave — ela começa com `sk-ant-...`
6. Guarde essa chave em local seguro (não compartilhe com ninguém)

**Custo por treino gerado:** ~$0,01 a $0,03 → $5 = 200 a 500 treinos

---

## PASSO 2 — CRIAR CONTA NO MAKE.COM

1. Acesse: **make.com**
2. Crie conta gratuita (não precisa cartão)
3. O plano gratuito tem 1.000 operações/mês — suficiente para começar

---

## PASSO 3 — CRIAR O CENÁRIO NO MAKE.COM

### 3.1 — Criar novo cenário

1. No Make.com, clique em **Create a new scenario**
2. Clique no **"+" grande** no centro

---

### 3.2 — Módulo 1: Webhook (receber dados do formulário)

1. Pesquise por **"Webhooks"** e selecione
2. Escolha **"Custom webhook"**
3. Clique em **"Add"** → dê o nome: `Trainfy - Novo Cliente`
4. Clique em **"Save"** — vai aparecer uma URL assim:
   ```
   https://hook.eu2.make.com/xxxxxxxxxxxxxxxxxxxx
   ```
5. **Copie essa URL** — você vai precisar dela no PASSO 5

---

### 3.3 — Módulo 2: HTTP (chamar a API do Claude)

1. Clique no **"+"** após o Webhook para adicionar outro módulo
2. Pesquise por **"HTTP"** e selecione **"Make a request"**
3. Configure assim:

**URL:**
```
https://api.anthropic.com/v1/messages
```

**Method:** POST

**Headers** (adicione os 3):
```
anthropic-version    →    2023-06-01
x-api-key            →    [SUA_CHAVE_ANTHROPIC_sk-ant-...]
content-type         →    application/json
```

**Body type:** Raw

**Content type:** JSON (application/json)

**Request content** (cole o JSON abaixo, substituindo nada por agora — as variáveis `{{1.campo}}` são preenchidas automaticamente pelo Make.com com os dados do webhook):

```json
{
  "model": "claude-haiku-4-5-20251001",
  "max_tokens": 4000,
  "messages": [
    {
      "role": "user",
      "content": "COLE_AQUI_O_PROMPT_DO_ARQUIVO_PROMPT_CLAUDE_API.md"
    }
  ]
}
```

> ⚠️ O prompt completo está no arquivo [[⚙️ Prompt - Claude API Treino]]. Cole o conteúdo daquele arquivo no lugar de COLE_AQUI_O_PROMPT.

---

### 3.4 — Módulo 3: Gmail (enviar treino ao cliente)

1. Clique no **"+"** após o HTTP para adicionar outro módulo
2. Pesquise **"Gmail"** e selecione **"Send an Email"**
3. Na primeira vez, vai pedir para conectar sua conta Google — clique em **"Add"** e autorize
4. Configure assim:

**To:** `{{1.email}}` (email do cliente, vindo do webhook)

**Subject:** `Seu treino personalizado Trainfy está pronto! 💪`

**Content:** HTML — cole isso:

```html
<div style="font-family:Arial,sans-serif;max-width:700px;margin:0 auto;padding:20px;color:#0a0a0a;">
  <div style="border-bottom:2px solid #0a0a0a;padding-bottom:16px;margin-bottom:24px;">
    <strong style="font-size:18px;letter-spacing:0.05em;">TRAINFY</strong>
  </div>
  <p style="font-size:16px;margin-bottom:8px;">Olá! Seu treino personalizado está pronto.</p>
  <p style="font-size:14px;color:#666;margin-bottom:24px;">Montado especialmente para o seu perfil, objetivo e limitações.</p>
  <div style="background:#f5f5f5;border-radius:8px;padding:24px;font-size:14px;line-height:1.8;white-space:pre-wrap;">{{2.data.content[].text}}</div>
  <p style="font-size:12px;color:#999;margin-top:24px;border-top:1px solid #e5e5e5;padding-top:16px;">Trainfy — Treinos seguros, estruturados e adaptados ao seu corpo.</p>
</div>
```

> O campo `{{2.data.content[].text}}` é onde o Make.com insere o treino gerado pelo Claude.

---

### 3.5 — Ativar o cenário

1. No canto inferior esquerdo, ative o toggle **"Scheduling"**
2. Selecione **"Immediately as data arrives"**
3. Clique em **"Save"**

O cenário agora está ativo e vai processar automaticamente cada vez que o formulário for enviado.

---

## PASSO 4 — TESTAR O CENÁRIO

Antes de colocar no formulário real, teste manualmente:

1. No Make.com, clique em **"Run once"**
2. Abra outra aba e acesse a URL do webhook diretamente, ou use o formulário com seu próprio email
3. Verifique se o email chegou com o treino gerado

---

## PASSO 5 — ATUALIZAR O FORMULÁRIO

Após ter a URL do webhook do Make.com (do Passo 3.2), diga ao Claude:

> "Adiciona o webhook do Make.com no formulário. A URL é: [cole a URL aqui]"

O Claude vai modificar o arquivo `index.html` automaticamente.

---

## ESTIMATIVA DE CUSTO

| Item | Custo |
|---|---|
| Make.com (plano gratuito) | R$0 |
| Claude API por treino gerado | ~$0,01–$0,03 |
| $5 na API | 200–500 treinos |
| Primeiro upgrade necessário | Após 200+ clientes |

---

## TROUBLESHOOTING

**Email não chegou:**
- Verifique se o cenário está ativo (toggle verde)
- Verifique a pasta Spam do cliente
- No Make.com, vá em History para ver se houve erro

**Erro na API do Claude:**
- Verifique se a chave da API está correta no header `x-api-key`
- Verifique se há saldo na conta Anthropic (console.anthropic.com → Billing)

**Dados não chegam no webhook:**
- Verifique se a URL do webhook foi colada corretamente no formulário
- No Make.com, clique em "Run once" e envie o formulário para capturar a estrutura dos dados

---

*Criado: Maio 2026 | Ver também: [[⚙️ Prompt - Claude API Treino]] | [[SAAS]]*
