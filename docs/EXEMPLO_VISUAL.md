# Exemplo Visual da Planilha

## Dashboard - Exemplo Completo

### Seleção: FII + Conservador

```
╔═══════════════════════════════════════════════════════════════╗
║            CARTEIRA DE INVESTIMENTOS - DASHBOARD              ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  ┌─────────────────────┬──────────────────────┐             ║
║  │ TIPO DE ATIVO       │ FII              ▼   │             ║
║  ├─────────────────────┼──────────────────────┤             ║
║  │ PERFIL DE RISCO     │ Conservador      ▼   │             ║
║  └─────────────────────┴──────────────────────┘             ║
║                                                               ║
║  ┌───────────────────────────────────────────────────────┐  ║
║  │                 CARTEIRA RECOMENDADA                  │  ║
║  ├──────────────────────────┬────────────────────────────┤  ║
║  │ ATIVO                    │ ALOCAÇÃO (%)               │  ║
║  ├──────────────────────────┼────────────────────────────┤  ║
║  │ HGLG11                   │ 15                         │  ║
║  │ KNRI11                   │ 15                         │  ║
║  │ XPML11                   │ 20                         │  ║
║  │ MXRF11                   │ 25                         │  ║
║  │ PVBI11                   │ 25                         │  ║
║  ├──────────────────────────┼────────────────────────────┤  ║
║  │ TOTAL                    │ 100                        │  ║
║  └──────────────────────────┴────────────────────────────┘  ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### Seleção: Criptomoedas + Agressivo

```
╔═══════════════════════════════════════════════════════════════╗
║            CARTEIRA DE INVESTIMENTOS - DASHBOARD              ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  ┌─────────────────────┬──────────────────────┐             ║
║  │ TIPO DE ATIVO       │ Criptomoedas     ▼   │             ║
║  ├─────────────────────┼──────────────────────┤             ║
║  │ PERFIL DE RISCO     │ Agressivo        ▼   │             ║
║  └─────────────────────┴──────────────────────┘             ║
║                                                               ║
║  ┌───────────────────────────────────────────────────────┐  ║
║  │                 CARTEIRA RECOMENDADA                  │  ║
║  ├──────────────────────────┬────────────────────────────┤  ║
║  │ ATIVO                    │ ALOCAÇÃO (%)               │  ║
║  ├──────────────────────────┼────────────────────────────┤  ║
║  │ Bitcoin                  │ 30                         │  ║
║  │ Ethereum                 │ 25                         │  ║
║  │ BNB                      │ 15                         │  ║
║  │ Cardano                  │ 10                         │  ║
║  │ Solana                   │ 10                         │  ║
║  │ Polkadot                 │ 5                          │  ║
║  │ Chainlink                │ 5                          │  ║
║  ├──────────────────────────┼────────────────────────────┤  ║
║  │ TOTAL                    │ 100                        │  ║
║  └──────────────────────────┴────────────────────────────┘  ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

## Planilha de Dados - Exemplo

### Dados_FII

```
┌──────────────┬──────────┬──────────────┬────────────┐
│ TipoAtivo    │ Ativo    │ PerfilRisco  │ Percentual │
├──────────────┼──────────┼──────────────┼────────────┤
│ FII          │ HGLG11   │ Conservador  │ 15         │
│ FII          │ KNRI11   │ Conservador  │ 15         │
│ FII          │ XPML11   │ Conservador  │ 20         │
│ FII          │ MXRF11   │ Conservador  │ 25         │
│ FII          │ PVBI11   │ Conservador  │ 25         │
│ FII          │ HGLG11   │ Moderado     │ 10         │
│ FII          │ KNRI11   │ Moderado     │ 15         │
│ FII          │ XPML11   │ Moderado     │ 15         │
│ FII          │ MXRF11   │ Moderado     │ 20         │
│ FII          │ PVBI11   │ Moderado     │ 15         │
│ FII          │ VISC11   │ Moderado     │ 15         │
│ FII          │ BTLG11   │ Moderado     │ 10         │
│ FII          │ HGLG11   │ Agressivo    │ 8          │
│ FII          │ KNRI11   │ Agressivo    │ 7          │
│ FII          │ XPML11   │ Agressivo    │ 10         │
│ FII          │ MXRF11   │ Agressivo    │ 15         │
│ FII          │ PVBI11   │ Agressivo    │ 10         │
│ FII          │ VISC11   │ Agressivo    │ 15         │
│ FII          │ BTLG11   │ Agressivo    │ 15         │
│ FII          │ KNCR11   │ Agressivo    │ 10         │
│ FII          │ VILG11   │ Agressivo    │ 10         │
└──────────────┴──────────┴──────────────┴────────────┘
```

## Interação do Usuário

### Passo 1: Abrir Dashboard
```
Ao abrir a planilha, você verá:
- Duas listas suspensas (B1 e B2)
- Área vazia para resultados (A5:B5 em diante)
```

### Passo 2: Selecionar Tipo de Ativo
```
Clique em B1 → Aparece dropdown:
┌─────────────────┐
│ FII             │ ← Opção 1
│ Criptomoedas    │ ← Opção 2
└─────────────────┘
```

### Passo 3: Selecionar Perfil de Risco
```
Clique em B2 → Aparece dropdown:
┌─────────────────┐
│ Conservador     │ ← Opção 1
│ Moderado        │ ← Opção 2
│ Agressivo       │ ← Opção 3
└─────────────────┘
```

### Passo 4: Ver Resultados
```
Instantaneamente, a área abaixo se preenche:
┌──────────────┬──────────────┐
│ ATIVO        │ ALOCAÇÃO (%) │
│ [Lista...]   │ [Valores...] │
└──────────────┴──────────────┘
```

## Comparação Visual dos Perfis

### FII - Todos os Perfis

```
CONSERVADOR (5 ativos)        MODERADO (7 ativos)           AGRESSIVO (9 ativos)
═══════════════════════       ═══════════════════════       ═══════════════════════
HGLG11 ████████████ 15%       HGLG11 ██████ 10%             HGLG11 ████ 8%
KNRI11 ████████████ 15%       KNRI11 ████████████ 15%       KNRI11 ███ 7%
XPML11 ████████████████ 20%   XPML11 ████████████ 15%       XPML11 █████ 10%
MXRF11 ████████████████████25%MXRF11 ████████████████ 20%   MXRF11 ████████████ 15%
PVBI11 ████████████████████25%PVBI11 ████████████ 15%       PVBI11 █████ 10%
                              VISC11 ████████████ 15%       VISC11 ████████████ 15%
                              BTLG11 ██████ 10%             BTLG11 ████████████ 15%
                                                            KNCR11 █████ 10%
                                                            VILG11 █████ 10%
```

### Criptomoedas - Todos os Perfis

```
CONSERVADOR (3 ativos)        MODERADO (5 ativos)           AGRESSIVO (7 ativos)
═══════════════════════       ═══════════════════════       ═══════════════════════
Bitcoin  ████████████████50%  Bitcoin  ████████████████40%  Bitcoin  ████████████30%
Ethereum ████████████ 30%     Ethereum ████████████ 30%     Ethereum ██████████ 25%
USDT     ████████ 20%         BNB      ██████ 15%           BNB      ██████ 15%
                              Cardano  ████ 10%             Cardano  ████ 10%
                              USDT     ██ 5%                Solana   ████ 10%
                                                            Polkadot ██ 5%
                                                            Chainlink██ 5%
```

## Comportamento Dinâmico

### Mudança de Seleção

```
Estado Inicial:
B1: [FII]          B2: [Conservador]
↓
Resultados: 5 FIIs conservadores

Usuário muda B1 para [Criptomoedas]:
B1: [Criptomoedas] B2: [Conservador]
↓
Resultados: ATUALIZAÇÃO AUTOMÁTICA
           3 Criptos conservadoras

Usuário muda B2 para [Agressivo]:
B1: [Criptomoedas] B2: [Agressivo]
↓
Resultados: ATUALIZAÇÃO AUTOMÁTICA
           7 Criptos agressivas
```

## Exemplo com Gráfico (Opcional)

```
╔═══════════════════════════════════════════════════════════════╗
║            CARTEIRA DE INVESTIMENTOS - DASHBOARD              ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  ┌─────────────────┐  ┌─────────────────────────────────┐   ║
║  │ TIPO: FII   ▼   │  │     DISTRIBUIÇÃO                │   ║
║  │ RISCO: Mod. ▼   │  │                                 │   ║
║  └─────────────────┘  │        ████                     │   ║
║                       │      ██    ██                   │   ║
║  ATIVO      ALOCAÇÃO  │    ██ 20%   ██                  │   ║
║  HGLG11        10%    │   ██   15%    █                 │   ║
║  KNRI11        15% ←──┼──█             ██               │   ║
║  XPML11        15% ←──┼─██              ██              │   ║
║  MXRF11        20% ←──┼─█      10%       █              │   ║
║  PVBI11        15%    │ █       15%      █              │   ║
║  VISC11        15%    │ ██               █              │   ║
║  BTLG11        10% ←──┼──██            ██               │   ║
║  ─────────────────    │    ████      ███                │   ║
║  TOTAL        100%    │        ████████                 │   ║
║                       └─────────────────────────────────┘   ║
╚═══════════════════════════════════════════════════════════════╝
```

## Dica de Uso

Para melhor experiência visual no Excel:
1. Use zoom de 100% ou 120%
2. Congele as 4 primeiras linhas (para ver seleções ao rolar)
3. Aplique cores alternadas (zebrado) nos resultados
4. Use negrito nos cabeçalhos
5. Centre o texto nas células de seleção

---

**Nota:** Estas são representações visuais em texto. No Excel real, você terá:
- Cores vibrantes
- Dropdowns interativos
- Atualização instantânea
- Formatação profissional
