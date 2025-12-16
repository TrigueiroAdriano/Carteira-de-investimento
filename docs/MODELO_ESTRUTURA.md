# Modelo de Estrutura da Planilha Excel

Este documento descreve visualmente como a planilha deve ser estruturada.

## Planilha: Dashboard

### Layout Visual

```
     A                    B                C
1  | TIPO DE ATIVO    | [FII ▼]         |
2  | PERFIL DE RISCO  | [Conservador ▼] |
3  |                  |                 |
4  | ATIVO            | ALOCAÇÃO (%)    |
5  | [Resultado 1]    | [Percentual 1]  |
6  | [Resultado 2]    | [Percentual 2]  |
7  | [Resultado 3]    | [Percentual 3]  |
8  | ...              | ...             |
```

### Células Importantes

**B1**: Lista suspensa
- Opções: FII, Criptomoedas
- Célula com fundo amarelo claro

**B2**: Lista suspensa
- Opções: Conservador, Moderado, Agressivo
- Célula com fundo amarelo claro

**A5**: Fórmula FILTRAR (ativos)
```
=FILTRAR(Dados_Completos!B:B;(Dados_Completos!A:A=Dashboard!B1)*(Dados_Completos!C:C=Dashboard!B2))
```

**B5**: Fórmula FILTRAR (percentuais)
```
=FILTRAR(Dados_Completos!D:D;(Dados_Completos!A:A=Dashboard!B1)*(Dados_Completos!C:C=Dashboard!B2))
```

### Formatação

**Cabeçalhos (A1, A2, A4, B4):**
- Fonte: Negrito, 11pt
- Preenchimento: RGB(0, 51, 102) - Azul escuro
- Cor do texto: Branco
- Alinhamento: Centro, Vertical Centro
- Bordas: Todas as bordas, Preto

**Células de Entrada (B1, B2):**
- Preenchimento: RGB(255, 255, 204) - Amarelo claro
- Bordas: Todas as bordas, Preto, Espessa
- Alinhamento: Centro

**Área de Resultados (A5:B5 e descendentes):**
- Zebrado: Linhas alternadas branco e RGB(242, 242, 242) - Cinza muito claro
- Coluna B: Formato personalizado "#,##0%" ou "0.00\%"
- Bordas: Linhas horizontais entre células

## Planilha: Dados_FII

### Layout Visual

```
     A              B           C              D
1  | TipoAtivo   | Ativo     | PerfilRisco  | Percentual |
2  | FII         | HGLG11    | Conservador  | 15         |
3  | FII         | KNRI11    | Conservador  | 15         |
4  | FII         | XPML11    | Conservador  | 20         |
5  | FII         | MXRF11    | Conservador  | 25         |
...
```

### Formatação

**Linha de Cabeçalho (Linha 1):**
- Fonte: Negrito, 11pt
- Preenchimento: RGB(217, 217, 217) - Cinza claro
- Filtros Automáticos: Habilitados
- Bordas: Todas as bordas, Preto

**Dados:**
- Alinhamento: Esquerda para texto, Direita para números
- Bordas: Linhas horizontais leves

## Planilha: Dados_Cripto

### Layout Visual

```
     A              B           C              D
1  | TipoAtivo   | Ativo     | PerfilRisco  | Percentual |
2  | Criptomoedas| Bitcoin   | Conservador  | 50         |
3  | Criptomoedas| Ethereum  | Conservador  | 30         |
4  | Criptomoedas| USDT      | Conservador  | 20         |
...
```

### Formatação
(Mesma da planilha Dados_FII)

## Planilha: Dados_Completos

### Layout Visual

```
     A              B           C              D
1  | TipoAtivo   | Ativo     | PerfilRisco  | Percentual |
2  | FII         | HGLG11    | Conservador  | 15         |
3  | FII         | KNRI11    | Conservador  | 15         |
...
22 | Criptomoedas| Bitcoin   | Conservador  | 50         |
23 | Criptomoedas| Ethereum  | Conservador  | 30         |
...
```

Esta planilha é a união de Dados_FII e Dados_Cripto.

### Formatação
(Mesma das outras planilhas de dados)

## Cores Utilizadas (RGB)

| Elemento                | RGB           | Cor         |
|------------------------|---------------|-------------|
| Cabeçalhos Dashboard   | 0, 51, 102    | Azul escuro |
| Texto Cabeçalhos       | 255, 255, 255 | Branco      |
| Células de Entrada     | 255, 255, 204 | Amarelo     |
| Cabeçalhos Dados       | 217, 217, 217 | Cinza claro |
| Zebrado claro          | 242, 242, 242 | Cinza muito claro |

## Largura de Colunas Recomendada

| Planilha | Coluna A | Coluna B | Coluna C | Coluna D |
|----------|----------|----------|----------|----------|
| Dashboard| 20       | 20       | -        | -        |
| Dados_*  | 15       | 15       | 15       | 12       |

## Proteção (Opcional)

Para evitar alterações acidentais:

1. **Planilhas de Dados**: Proteger contra edição
   - Permitir apenas inserção de linhas
   
2. **Dashboard**: Proteger com exceções
   - Permitir edição apenas em B1 e B2
   - Proteger as células de fórmula

## Exemplo de Resultado Final

### Seleção: FII + Conservador
```
ATIVO       ALOCAÇÃO (%)
HGLG11      15
KNRI11      15
XPML11      20
MXRF11      25
PVBI11      25
```

### Seleção: Criptomoedas + Agressivo
```
ATIVO       ALOCAÇÃO (%)
Bitcoin     30
Ethereum    25
BNB         15
Cardano     10
Solana      10
Polkadot    5
Chainlink   5
```

## Recursos Adicionais (Opcionais)

### Gráfico de Pizza
Adicionar ao lado direito do Dashboard:
- Dados: A5:B5# (referência dinâmica)
- Tipo: Pizza 3D
- Título: "Distribuição da Carteira"

### Totalização
Em uma célula abaixo dos resultados:
```
Célula A15: "TOTAL:"
Célula B15: =SOMA(B5#)
```
Deve sempre resultar em 100%.

### Formatação Condicional
Aplicar em B5:B20:
- Se > 20: Verde claro
- Se 10-20: Amarelo claro
- Se < 10: Sem formatação

Isso destaca alocações maiores.
