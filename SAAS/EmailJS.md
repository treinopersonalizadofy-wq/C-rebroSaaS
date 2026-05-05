# ⚙️ EmailJS — Configuração Técnica

→ [[SAAS]]

---

## Credenciais

| Campo | Valor |
|---|---|
| Service ID | `service_w02priq` |
| Template ID | `template_rwj7wtr` |
| Public Key | `seqKv6AYImETCFsiu` |

**⚠️ Confirmar:** O dashboard do EmailJS deve estar logado na conta que usa esta chave pública. Verifique em Account → API Keys.

---

## Variáveis do Template

Estas variáveis precisam estar no template `template_rwj7wtr`:

| Variável | Descrição |
|---|---|
| `{{from_email}}` | Email do cliente |
| `{{nivel}}` | Nível de experiência |
| `{{objetivo}}` | Objetivo do treino |
| `{{dias_semana}}` | Dias disponíveis por semana na academia |
| `{{tempo_treino}}` | Tempo por sessão |
| `{{local_treino}}` | Academia / casa |
| `{{esporte}}` | Esporte praticado (opcional) |
| `{{foco_esporte}}` | Foco principal: Performance no esporte / Hipertrofia |
| `{{esporte_frequencia}}` | Quantas vezes/semana pratica o esporte |
| `{{esporte_dias}}` | Quais dias da semana pratica o esporte |
| `{{dor_lombar}}` | Dor lombar (sim/não) |
| `{{dor_joelho}}` | Dor no joelho (sim/não) |
| `{{dor_ombro}}` | Dor no ombro (sim/não) |
| `{{observacoes}}` | Observações adicionais |

---

## Template Sugerido (copiar no EmailJS)

**Assunto:**
```
Novo pedido de treino — {{from_email}}
```

**Corpo do email:**
```
📋 NOVO PEDIDO DE TREINO PRO

Email: {{from_email}}
Nível: {{nivel}}
Objetivo: {{objetivo}}
Dias academia/semana: {{dias_semana}}
Tempo por sessão: {{tempo_treino}}
Local: {{local_treino}}

Esporte: {{esporte}}
Foco principal: {{foco_esporte}}
Frequência do esporte: {{esporte_frequencia}}
Dias do esporte: {{esporte_dias}}

Lesões:
• Lombar: {{dor_lombar}}
• Joelho: {{dor_joelho}}
• Ombro: {{dor_ombro}}

Observações: {{observacoes}}
```

---

## Como Configurar

1. Acesse emailjs.com → Login
2. Email Services → Verificar se `service_w02priq` está ativo
3. Email Templates → Abrir `template_rwj7wtr`
4. Adicionar todas as variáveis acima no corpo do template
5. Salvar e testar

---

## Status da Landing Page
→ [[Landing Page]]

A integração está funcionando no arquivo `TREINO_PRO_Landing_Page_v4.html`.
O EmailJS é chamado na linha ~761 do arquivo com todas as variáveis acima.
