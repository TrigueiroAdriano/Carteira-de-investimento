# Guia de Construção da Planilha de Carteira de Investimentos

## Visão Geral
Este documento descreve como construir a planilha Excel para gestão dinâmica de carteira de investimentos.

## Estrutura da Planilha

### Planilha 1: "Dashboard"
Esta é a planilha principal onde o usuário interage com o sistema.

#### Área de Seleção (Células A1:B3)
- **A1:** "TIPO DE ATIVO"
- **B1:** Lista suspensa com opções: "FII", "Criptomoedas"
- **A2:** "PERFIL DE RISCO"
- **B2:** Lista suspensa com opções: "Conservador", "Moderado", "Agressivo"

#### Área de Resultados (A4 em diante)
- **A4:** "ATIVO"
- **B4:** "ALOCAÇÃO (%)"
- **A5:** Fórmula FILTRAR (ver seção de fórmulas)
- **B5:** Fórmula FILTRAR (ver seção de fórmulas)

### Planilha 2: "Dados_FII"
Contém todos os ativos de FII com suas alocações por perfil de risco.

**Colunas:**
- A: TipoAtivo (sempre "FII")
- B: Ativo (código do FII, ex: HGLG11)
- C: PerfilRisco (Conservador, Moderado, Agressivo)
- D: Percentual (percentual de alocação)

**Dados:** Importar do arquivo `dados/FII_Ativos.csv`

### Planilha 3: "Dados_Cripto"
Contém todos os ativos de Criptomoedas com suas alocações por perfil de risco.

**Colunas:**
- A: TipoAtivo (sempre "Criptomoedas")
- B: Ativo (nome da criptomoeda)
- C: PerfilRisco (Conservador, Moderado, Agressivo)
- D: Percentual (percentual de alocação)

**Dados:** Importar do arquivo `dados/Cripto_Ativos.csv`

### Planilha 4: "Dados_Completos"
Consolidação de todos os dados (união das planilhas Dados_FII e Dados_Cripto).

**Colunas:**
- A: TipoAtivo
- B: Ativo
- C: PerfilRisco
- D: Percentual

## Criação das Listas Suspensas

### Para Tipo de Ativo (célula B1 do Dashboard)
1. Selecione a célula B1
2. Vá em Dados > Validação de Dados
3. Configurações:
   - Permitir: Lista
   - Fonte: `FII,Criptomoedas`
   - Marcar "Lista suspensa na célula"
4. Clique em OK

### Para Perfil de Risco (célula B2 do Dashboard)
1. Selecione a célula B2
2. Vá em Dados > Validação de Dados
3. Configurações:
   - Permitir: Lista
   - Fonte: `Conservador,Moderado,Agressivo`
   - Marcar "Lista suspensa na célula"
4. Clique em OK

## Fórmulas FILTRAR

### Fórmula para Listar Ativos (célula A5 do Dashboard)
```excel
=FILTRAR(Dados_Completos!B:B; (Dados_Completos!A:A=Dashboard!B1) * (Dados_Completos!C:C=Dashboard!B2))
```

**Explicação:**
- `Dados_Completos!B:B`: Coluna de ativos a retornar
- `Dados_Completos!A:A=Dashboard!B1`: Filtra pelo tipo de ativo selecionado
- `Dados_Completos!C:C=Dashboard!B2`: Filtra pelo perfil de risco selecionado
- O operador `*` funciona como "E" lógico

### Fórmula para Listar Percentuais (célula B5 do Dashboard)
```excel
=FILTRAR(Dados_Completos!D:D; (Dados_Completos!A:A=Dashboard!B1) * (Dados_Completos!C:C=Dashboard!B2))
```

**Explicação:**
- Similar à fórmula anterior, mas retorna a coluna D (Percentual)

### Fórmula para Total (opcional - pode ser adicionada)
Adicione em uma célula após os resultados:
```excel
=SOMA(B5#)
```
Esta fórmula soma todos os percentuais filtrados (deve dar 100%).

## Formatação Recomendada

### Dashboard
- **Células de cabeçalho (A1, B1, A2, B2, A4, B4):**
  - Negrito
  - Preenchimento: Azul escuro
  - Texto: Branco
  - Alinhamento: Centro

- **Células de seleção (B1, B2):**
  - Preenchimento: Amarelo claro
  - Borda: Preta, espessa

- **Área de resultados (A5:B5 e expandidas):**
  - Alternância de cores nas linhas (zebrado)
  - Coluna B: Formato de porcentagem ou número com "%" ao final

### Planilhas de Dados
- **Linha de cabeçalho:**
  - Negrito
  - Preenchimento: Cinza claro
  - Texto: Preto
  - Filtros automáticos habilitados

## Passos para Criar a Planilha

1. **Criar novo arquivo Excel**
   - Abra o Microsoft Excel
   - Crie uma nova pasta de trabalho

2. **Renomear e organizar planilhas**
   - Renomeie "Planilha1" para "Dashboard"
   - Adicione três novas planilhas: "Dados_FII", "Dados_Cripto", "Dados_Completos"

3. **Importar dados**
   - Na planilha "Dados_FII": 
     - Vá em Dados > Obter Dados > De Arquivo > Do CSV
     - Selecione `dados/FII_Ativos.csv`
     - Importe os dados
   - Repita para "Dados_Cripto" com `dados/Cripto_Ativos.csv`

4. **Criar planilha Dados_Completos**
   - Copie os dados de "Dados_FII" para "Dados_Completos"
   - Abaixo, cole os dados de "Dados_Cripto"
   - Certifique-se de que as colunas estão alinhadas

5. **Configurar o Dashboard**
   - Adicione os cabeçalhos conforme descrito
   - Crie as listas suspensas
   - Adicione as fórmulas FILTRAR
   - Aplique a formatação recomendada

6. **Testar**
   - Selecione diferentes combinações de Tipo de Ativo e Perfil de Risco
   - Verifique se os ativos e percentuais são exibidos corretamente
   - Confirme que a soma dos percentuais = 100%

7. **Salvar**
   - Salve o arquivo como "Carteira_Investimentos.xlsx"

## Requisitos
- Microsoft Excel 2021 ou superior (ou Microsoft 365) para suporte à função FILTRAR
- Se usar versões antigas do Excel, será necessário substituir FILTRAR por fórmulas com ÍNDICE/CORRESP ou tabelas dinâmicas

## Solução de Problemas

### A função FILTRAR não é reconhecida
- **Problema:** Excel antigo
- **Solução:** Atualize para Excel 2021/Microsoft 365 ou use fórmulas alternativas com ÍNDICE/CORRESP

### Os dados não aparecem após a seleção
- Verifique se os nomes das planilhas estão corretos nas fórmulas
- Confirme que as células B1 e B2 contêm valores válidos
- Verifique se os dados nas planilhas de origem estão corretos

### A soma dos percentuais não dá 100%
- Revise os dados nas planilhas Dados_FII e Dados_Cripto
- Certifique-se de que cada combinação de TipoAtivo + PerfilRisco soma 100%

## Expansão Futura
- Adicionar mais tipos de ativos (Ações, Renda Fixa, etc.)
- Incluir gráficos dinâmicos da alocação
- Adicionar histórico de performance
- Incluir cálculo de rentabilidade esperada por perfil
