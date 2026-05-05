# ⚽ Esportes — Hub de Musculação Esportiva

→ [[SAAS]]

---

## Por Que Treino Esportivo é Diferente

Quem pratica esporte tem necessidades específicas na academia:
1. **Músculos prioritários** diferentes de quem só quer hipertrofia
2. **Capacidades físicas** específicas da modalidade (potência, velocidade, resistência)
3. **Volume menor** no treino de força (não pode comprometer a recuperação do esporte)
4. **Timing** precisa respeitar a agenda de treinos e competições

---

## Modalidades Mapeadas

| Modalidade | Nó |
|---|---|
| Boxe / Kickboxing / Muay Thai | [[Esportes - Artes Marciais]] |
| BJJ / Jiu-Jitsu / MMA | [[Esportes - Artes Marciais]] |
| Corrida (5k, 10k, maratona) | [[Esportes - Corrida e Ciclismo]] |
| Ciclismo (road, MTB, spinning) | [[Esportes - Corrida e Ciclismo]] |
| Triathlon | [[Esportes - Corrida e Ciclismo]] |
| Futebol | [[Esportes - Futebol e Coletivos]] |
| Basquete | [[Esportes - Futebol e Coletivos]] |
| Vôlei | [[Esportes - Futebol e Coletivos]] |
| Natação | [[Esportes - Natação Tênis e Outros]] |
| Tênis / Padel | [[Esportes - Natação Tênis e Outros]] |
| CrossFit / Funcional | [[Esportes - Natação Tênis e Outros]] |

---

## Princípio Universal do S&C Esportivo

**S&C = Strength & Conditioning** — musculação com propósito esportivo.

Todo treino esportivo no Treino Pro prioriza:
1. **Grupos musculares mais usados na modalidade** (tabela em cada nó)
2. **Padrões de movimento** específicos do esporte (ex: rotação para artes marciais)
3. **Prevenção de lesões** características de cada esporte
4. **Volume controlado** para não comprometer o rendimento esportivo

---

## Volume Recomendado (S&C Esportivo)
- **Academia:** 2–3x/semana máximo quando há esporte na agenda
- **Séries por grupo prioritário:** 10–16/semana
- **Grupos de suporte:** 6–10/semana
- **Nunca competir com o volume do esporte** — academia é complemento

---

## Campos no Formulário
O formulário agora captura 3 informações sobre esporte:
- `esporte` — qual modalidade pratica
- `esporte_frequencia` — quantas vezes por semana pratica
- `esporte_dias` — quais dias da semana pratica

Quando `esporte` ≠ "Nenhum em específico", usar os 3 campos para montar o treino.

---

## Lógica de Distribuição de Carga por Dias

### Regra Principal
Nos dias em que o cliente pratica o esporte → **treino de academia mais leve** (grupos musculares diferentes ou volume reduzido).
Nos dias sem esporte → **treino de academia mais pesado** (compostos principais, maior intensidade).

### Como Aplicar

**Passo 1:** Mapear a semana completa com os dias de esporte
```
Exemplo — Muay Thai 3x/semana: Seg, Qua, Sex
Academia 5x/semana

Segunda  [ESPORTE]  → Academia: Braços / Core (leve, sem impacto em recuperação)
Terça    [LIVRE]    → Academia: Peito (pesado — dia de folga do esporte)
Quarta   [ESPORTE]  → Academia: Costas (moderado, puxada — não atrapalha luta)
Quinta   [LIVRE]    → Academia: Pernas (pesado — dia de folga do esporte)
Sexta    [ESPORTE]  → Academia: Ombros + Core Boxe (leve — prep para fim de semana)
```

**Passo 2:** Classificar cada dia de academia
| Tipo de Dia | Carga Academia | O que treinar |
|---|---|---|
| Dia COM esporte | **Leve** — 60–70% da intensidade normal | Grupos que não impactam a performance no esporte; braços, core isolado |
| Dia SEM esporte (folga) | **Pesado** — 100% da intensidade | Compostos principais, pernas, grupos que exigem mais recuperação |
| Dia seguinte ao esporte intenso | **Moderado** — 75–80% | Evitar pernas pesadas após luta/corrida intensa; priorizar superior |

### Regras por Frequência do Esporte

| Frequência do Esporte | Dias Academia Pesados | Estratégia |
|---|---|---|
| 1–2x/semana | A maioria dos dias | Impacto baixo — treinar normalmente nos outros dias |
| 3–4x/semana | Apenas dias sem esporte | Montar academia nos dias livres, leve nos dias de esporte |
| 5+x/semana | Poucos ou nenhum | Reduzir academia para 2–3x, sempre leve, foco em prevenção |

### Exemplo Prático — BJJ 4x/semana (Seg, Ter, Qui, Sex)
```
Segunda  [BJJ]      → Academia: NÃO ou Braços muito leve
Terça    [BJJ]      → Academia: NÃO ou Core preventivo
Quarta   [LIVRE]    → Academia: Pernas PESADO ✅
Quinta   [BJJ]      → Academia: NÃO ou Ombros leve
Sexta    [BJJ]      → Academia: NÃO
Sábado   [LIVRE]    → Academia: Peito + Costas PESADO ✅
Domingo  [LIVRE]    → Descanso total
```

### Como Sinalizar no Treino para o Cliente
Entregar o treino com a semana mapeada:
```
SEGUNDA  [Muay Thai + Academia Leve]  → Treino E: Braços + Core
TERÇA    [Academia Pesado]            → Treino A: Peito
QUARTA   [Muay Thai + Academia Mod.]  → Treino B: Costas
QUINTA   [Academia Pesado]            → Treino C: Pernas
SEXTA    [Muay Thai + Academia Leve]  → Treino D: Ombros + Core Boxe
SÁBADO   Descanso
DOMINGO  Descanso
```
