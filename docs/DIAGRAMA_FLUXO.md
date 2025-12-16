# Fluxo de Funcionamento da Planilha

## Diagrama de Arquitetura

```
┌─────────────────────────────────────────────────────────────┐
│                        USUÁRIO                               │
│                  (Interage com Dashboard)                    │
└───────────────┬─────────────────────┬───────────────────────┘
                │                     │
                ▼                     ▼
        ┌──────────────┐      ┌──────────────┐
        │  Seleciona   │      │  Seleciona   │
        │ Tipo Ativo   │      │Perfil Risco  │
        │   (B1)       │      │   (B2)       │
        └──────┬───────┘      └──────┬───────┘
               │                     │
               └──────────┬──────────┘
                          ▼
                  ┌───────────────┐
                  │ Fórmula       │
                  │ FILTRAR       │
                  │ (A5 e B5)     │
                  └───────┬───────┘
                          │
                          ▼
                  ┌───────────────┐
                  │ Busca em      │
                  │Dados_Completos│
                  └───────┬───────┘
                          │
                          ▼
                  ┌───────────────┐
                  │ Retorna       │
                  │ Ativos e      │
                  │ Percentuais   │
                  └───────────────┘
```

## Fluxo de Dados

```
┌─────────────┐     ┌──────────────┐
│FII_Ativos   │────▶│              │
│   .csv      │     │              │
└─────────────┘     │              │     ┌──────────────┐
                    │ Dados_FII    │────▶│              │
┌─────────────┐     │              │     │              │
│Cripto_Ativos│────▶│              │     │  Dados_      │
│   .csv      │     └──────────────┘     │  Completos   │
└─────────────┘                          │              │
                    ┌──────────────┐     │              │
                    │ Dados_Cripto │────▶│              │
                    │              │     └──────┬───────┘
                    └──────────────┘            │
                                                │
                                                ▼
                                        ┌──────────────┐
                                        │  Dashboard   │
                                        │  (FILTRAR)   │
                                        └──────────────┘
```

## Lógica da Função FILTRAR

```
Entrada do Usuário:
┌─────────────┐
│ TipoAtivo   │ = "FII"
└─────────────┘
┌─────────────┐
│ PerfilRisco │ = "Conservador"
└─────────────┘

Processamento:
┌─────────────────────────────────────────────────┐
│ FILTRAR analisa cada linha de Dados_Completos: │
├─────────────────────────────────────────────────┤
│ Linha 1: FII + Conservador? ✅ INCLUIR          │
│ Linha 2: FII + Conservador? ✅ INCLUIR          │
│ Linha 3: FII + Moderado?    ❌ EXCLUIR          │
│ Linha 4: Cripto + Conserv.? ❌ EXCLUIR          │
│ ...                                             │
└─────────────────────────────────────────────────┘

Resultado:
┌──────────────┬──────────────┐
│ Ativo        │ Percentual   │
├──────────────┼──────────────┤
│ HGLG11       │ 15           │
│ KNRI11       │ 15           │
│ XPML11       │ 20           │
│ MXRF11       │ 25           │
│ PVBI11       │ 25           │
└──────────────┴──────────────┘
```

## Estrutura de Múltiplas Condições

```
Condição 1: TipoAtivo = Seleção
     ↓
Dados_Completos!A:A = Dashboard!B1
     ↓
[VERDADEIRO, VERDADEIRO, FALSO, FALSO, ...]

                    *  (AND lógico)

Condição 2: PerfilRisco = Seleção
     ↓
Dados_Completos!C:C = Dashboard!B2
     ↓
[VERDADEIRO, FALSO, VERDADEIRO, FALSO, ...]

                    =

Resultado Final:
[VERDADEIRO, FALSO, FALSO, FALSO, ...]
   ✅         ❌      ❌      ❌

Apenas linhas com VERDADEIRO são incluídas.
```

## Matriz Dinâmica (Spill)

```
Célula com Fórmula:
┌────────────────┐
│ A5: =FILTRAR() │
└────────────────┘
        │
        │ Retorna múltiplos valores
        ▼
┌────────────────┐
│ A5:  HGLG11    │ ← Fórmula aqui
├────────────────┤
│ A6:  KNRI11    │ ← Valor "derramado"
├────────────────┤
│ A7:  XPML11    │ ← Valor "derramado"
├────────────────┤
│ A8:  MXRF11    │ ← Valor "derramado"
├────────────────┤
│ A9:  PVBI11    │ ← Valor "derramado"
└────────────────┘

Para referenciar todos: A5#
```

## Exemplo Completo de Seleção

```
╔═══════════════════════════════════════════════════════╗
║                      DASHBOARD                         ║
╠═══════════════════════════════════════════════════════╣
║ TIPO DE ATIVO:    │ Criptomoedas         ▼│           ║
║ PERFIL DE RISCO:  │ Moderado             ▼│           ║
║                                                        ║
║ ┌────────────────────────────────────────────────┐    ║
║ │ ATIVO          │ ALOCAÇÃO (%)              │    ║
║ ├────────────────────────────────────────────────┤    ║
║ │ Bitcoin        │ 40                          │    ║
║ │ Ethereum       │ 30                          │    ║
║ │ BNB            │ 15                          │    ║
║ │ Cardano        │ 10                          │    ║
║ │ USDT           │ 5                           │    ║
║ └────────────────────────────────────────────────┘    ║
╚═══════════════════════════════════════════════════════╝
```

## Relação Entre Planilhas

```
┌───────────────┐
│  Dashboard    │ ← Interface do usuário
└───────┬───────┘
        │ lê
        ▼
┌───────────────┐
│Dados_Completos│ ← Base de dados consolidada
└───┬───────┬───┘
    │       │
    │ copia │ copia
    ▼       ▼
┌──────┐ ┌────────┐
│Dados │ │ Dados  │ ← Importados dos CSVs
│ FII  │ │ Cripto │
└──────┘ └────────┘
   ▲         ▲
   │         │
   │ importa │ importa
   │         │
┌──────┐  ┌────────┐
│FII_  │  │Cripto_ │ ← Arquivos de origem
│Ativos│  │Ativos  │
│.csv  │  │.csv    │
└──────┘  └────────┘
```

## Ciclo de Atualização

```
   ┌─────────────────────────────────────────┐
   │                                         │
   ▼                                         │
Usuário muda    Sistema             Resultado
   seleção  ──▶ recalcula  ──▶      atualiza
   (B1/B2)      fórmulas            (A5:B5)
      │            │                    │
      │            │                    │
      └────────────┴────────────────────┘
             Ciclo automático
```

## Validação de Dados

```
┌────────────────────────────────────────┐
│ Célula B1: Validação de Lista         │
├────────────────────────────────────────┤
│ Valores Permitidos:                    │
│   ✓ FII                                │
│   ✓ Criptomoedas                       │
│   ✗ Qualquer outro valor               │
└────────────────────────────────────────┘

┌────────────────────────────────────────┐
│ Célula B2: Validação de Lista         │
├────────────────────────────────────────┤
│ Valores Permitidos:                    │
│   ✓ Conservador                        │
│   ✓ Moderado                           │
│   ✓ Agressivo                          │
│   ✗ Qualquer outro valor               │
└────────────────────────────────────────┘

Benefício: Garante que FILTRAR sempre
           encontre correspondências
```

## Expansibilidade

```
Adicionar Novo Tipo de Ativo (ex: "Ações"):

1. Criar dados/Acoes_Ativos.csv
            │
            ▼
2. Importar para Dados_Acoes
            │
            ▼
3. Copiar para Dados_Completos
            │
            ▼
4. Atualizar validação B1: "FII,Criptomoedas,Ações"
            │
            ▼
5. Testar selecionando "Ações" em B1

✅ A fórmula FILTRAR funciona automaticamente!
```
