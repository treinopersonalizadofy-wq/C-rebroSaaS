# 🤖 Automação — Prompt de IA para Montar Treinos

→ [[SAAS]]

---

## Como Funciona o Processo

1. Cliente preenche formulário na landing page
2. Gabriel recebe email com os dados via EmailJS
3. Gabriel cola os dados no prompt abaixo
4. IA (ChatGPT, Claude, Gemini) gera o rascunho do treino
5. Gabriel revisa e ajusta conforme necessário
6. Treino enviado ao cliente em 24–48h

---

## Prompt Principal — Gerador de Treino

```
Você é um personal trainer especializado em musculação com base científica.
Baseie-se nas diretrizes de Schoenfeld, Krieger e Israetel (Renaissance Periodization).

DADOS DO CLIENTE:
- Email: [EMAIL]
- Nível: [NÍVEL: iniciante / intermediário / avançado]
- Objetivo: [OBJETIVO: hipertrofia / emagrecimento / força / condicionamento]
- Dias disponíveis: [DIAS]/semana
- Tempo por sessão: [TEMPO] minutos
- Local de treino: [LOCAL: academia / casa com equipamentos / casa sem equipamentos]
- Esporte praticado: [ESPORTE]
- Dor lombar: [SIM/NÃO/LEVE]
- Dor no joelho: [SIM/NÃO/LEVE]
- Dor no ombro: [SIM/NÃO/LEVE]
- Observações: [OBSERVAÇÕES]

INSTRUÇÕES:
1. Crie um treino personalizado de 12 semanas dividido em 3 fases:
   - Fase 1 (semanas 1–4): Acumulação — volume moderado, técnica e adaptação
   - Fase 2 (semanas 5–9): Intensificação — aumento progressivo de carga
   - Fase 3 (semanas 10–11): Deload — redução de 40% no volume
   - Semana 12: Avaliação e transição

2. Para cada exercício principal, estruture em 3 camadas:
   - Aquecimento: 2×12 reps com 50–60% da carga de trabalho
   - Feeder (ajuste): 1×6 reps com 70–80% da carga de trabalho
   - Séries válidas: conforme objetivo e fase

3. Se houver dor lombar, substitua (não remova):
   - Agachamento livre → Leg Press 45°
   - Terra convencional → Terra romeno com halteres
   - Remada curvada → Remada sentada no cabo
   - Adicione: Prancha, Bird-dog, Hip thrust

4. Se houver dor no joelho, substitua:
   - Agachamento profundo → Leg press parcial (até 90°)
   - Avanço → Step-up
   - Adicione: TKE com elástico, abdução de quadril

5. Se houver dor no ombro, substitua:
   - Desenvolvimento atrás da cabeça → Desenvolvimento frontal com halteres
   - Remada alta → Face pull
   - Puxada atrás → Puxada frontal
   - Adicione: Rotação externa com cabo, Face pull

6. Se pratica esporte, ajuste as prioridades musculares:
   - Artes marciais (Boxe/BJJ/MMA): priorize core rotacional, pegada, potência
   - Corrida/Ciclismo: priorize glúteo, isquiossurais, estabilidade de quadril
   - Futebol/Coletivos: priorize explosão, isquiossurais (nordic curl), potência
   - Natação: priorize grande dorsal, manguito rotador (face pull obrigatório)
   - VOLUME MÁXIMO DE ACADEMIA: 2–3x/semana para quem pratica esporte intensamente

7. Volume semanal alvo por grupo muscular (objetivo hipertrofia):
   - Peito: 10–16 séries
   - Costas: 12–20 séries
   - Pernas: 12–18 séries
   - Ombros: 10–16 séries
   - Bíceps/Tríceps: 8–14 séries

8. Formato de entrega:
   - Título: TREINO PRO — [NOME/EMAIL] — [OBJETIVO] — [DATA]
   - Divisão de treino por dia (ex: Treino A, B, C...)
   - Cada exercício com: nome, séries, reps, descanso, observação técnica
   - Tabela de progressão por fase
   - Instruções de aquecimento geral (5–10min antes)
   - Mensagem motivacional personalizada no final

ENTREGUE O TREINO COMPLETO PARA AS 12 SEMANAS.
```

---

## Checklist Pré-Envio

Antes de enviar o treino ao cliente, verificar:

- [ ] Lesões foram tratadas com SUBSTITUIÇÃO (não remoção)
- [ ] Cada exercício principal tem aquecimento + feeder + séries válidas
- [ ] Volume por grupo está dentro dos parâmetros científicos
- [ ] Periodização de 12 semanas está clara
- [ ] Deload na semana 10–11 está incluído
- [ ] Se pratica esporte: volume da academia está em máx. 2–3x/semana
- [ ] Linguagem está em português, clara e acessível
- [ ] Treino está formatado de forma legível (tabela ou PDF)
- [ ] Email de entrega tem tom humano e motivacional

---

## Templates de Email de Entrega

### Email de Boas-Vindas (após formulário)
```
Assunto: Treino Pro — Recebemos seu pedido! ✅

Olá!

Recebemos seu formulário com sucesso. Seu treino personalizado 
está sendo preparado com base nas suas respostas.

Você receberá seu treino em até 48 horas neste email.

Qualquer dúvida, é só responder!

— Equipe Treino Pro
```

### Email de Entrega do Treino
```
Assunto: Seu Treino Pro de 12 Semanas chegou! 💪

Olá!

Seu treino personalizado está pronto. Ele foi desenvolvido 
especialmente para você, levando em conta seu objetivo, 
sua disponibilidade e suas condições físicas.

[ANEXAR TREINO EM PDF OU PLANILHA]

Pontos importantes do seu treino:
• Duração: 12 semanas (3 fases)
• [RESUMO DO OBJETIVO]
• [INFORMAR SE TEM ADAPTAÇÕES DE LESÃO]

Qualquer dúvida sobre a execução dos exercícios, responda 
este email!

Boa evolução!
— Equipe Treino Pro
```
