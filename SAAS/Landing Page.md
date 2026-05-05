# 🌐 Landing Page — Status e Histórico

→ [[SAAS]]

---

## Arquivo Atual

**Arquivo:** `TREINO_PRO_Landing_Page_v4.html`
**Versão:** v4
**Status:** ✅ Pronta para uso

---

## Features Implementadas (v4)

| Feature | Status |
|---|---|
| Formulário de captação | ✅ |
| Validação com borda vermelha | ✅ |
| Scroll para campo com erro | ✅ |
| Spinner de loading no envio | ✅ |
| Página de sucesso "Parabéns!" | ✅ |
| Campo de esporte (dropdown) | ✅ |
| EmailJS integrado | ✅ |
| Tag `<base href>` removida | ✅ (bug corrigido) |

---

## Bug Corrigido na v4

**Problema:** Botão "Solicitar treino →" no topo da página redirecionava para URL externa (servidor da Creao) em vez de rolar para o formulário.

**Causa:** Tag `<base href="https://d16ilfvy4mv02r.cloudfront.net/...">` adicionada automaticamente pela Creao ao exportar o arquivo. Essa tag faz todos os links `#ancora` virarem URLs absolutas.

**Correção:** Remover a tag `<base href>` do `<head>`.

---

## Campos do Formulário

| Campo | ID | Tipo | Obrigatório |
|---|---|---|---|
| Email | `email` | input text | ✅ |
| Nível | `nivel` | select | ✅ |
| Objetivo | `objetivo` | select | ✅ |
| Dias/semana | `dias` | select | ✅ |
| Tempo por sessão | `tempo` | select | ✅ |
| Local | `local` | select | ✅ |
| Esporte | `esporte` | select | ❌ (opcional) |
| Dor lombar | `lombar` | select | ❌ |
| Dor joelho | `joelho` | select | ❌ |
| Dor ombro | `ombro` | select | ❌ |
| Observações | `observacoes` | textarea | ❌ |

---

## Configuração EmailJS
→ [[EmailJS]]

- Service: `service_w02priq`
- Template: `template_rwj7wtr`
- Public Key: `seqKv6AYImETCFsiu`

---

## Próximos Passos da Landing Page

- [ ] Publicar no domínio definitivo
- [ ] Configurar template EmailJS com todas as variáveis
- [ ] Adicionar Google Analytics ou similar
- [ ] A/B test de headline e CTA
- [ ] Adicionar depoimentos de primeiros clientes
- [ ] Versão mobile revisada
