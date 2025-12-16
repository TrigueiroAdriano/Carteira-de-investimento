# Documentação Técnica - Fórmulas e Estrutura

## Função FILTRAR (FILTER)

A função FILTRAR é uma das funções de matriz dinâmica introduzidas no Excel 2021/Microsoft 365. Ela permite filtrar dados com base em critérios específicos e retornar os resultados automaticamente em células adjacentes.

### Sintaxe
```
=FILTRAR(matriz; incluir; [se_vazio])
```

**Parâmetros:**
- `matriz`: O intervalo ou matriz a ser filtrado
- `incluir`: Uma matriz booleana (VERDADEIRO/FALSO) que determina quais linhas incluir
- `se_vazio`: (Opcional) Valor a retornar se nenhum resultado for encontrado

### Uso na Planilha

#### Filtragem de Ativos
```excel
=FILTRAR(Dados_Completos!B:B; (Dados_Completos!A:A=Dashboard!B1) * (Dados_Completos!C:C=Dashboard!B2))
```

**Detalhamento:**
1. `Dados_Completos!B:B` - Coluna que será retornada (nomes dos ativos)
2. `Dados_Completos!A:A=Dashboard!B1` - Condição 1: TipoAtivo igual à seleção
3. `Dados_Completos!C:C=Dashboard!B2` - Condição 2: PerfilRisco igual à seleção
4. `*` - Operador de multiplicação, funciona como AND lógico

**Como funciona o AND lógico:**
- VERDADEIRO * VERDADEIRO = 1 = Incluir linha
- VERDADEIRO * FALSO = 0 = Excluir linha
- FALSO * VERDADEIRO = 0 = Excluir linha
- FALSO * FALSO = 0 = Excluir linha

#### Filtragem de Percentuais
```excel
=FILTRAR(Dados_Completos!D:D; (Dados_Completos!A:A=Dashboard!B1) * (Dados_Completos!C:C=Dashboard!B2))
```

Mesma lógica, mas retorna a coluna D (Percentual).

### Matriz Dinâmica

As fórmulas FILTRAR retornam uma matriz dinâmica, ou seja:
- Uma única fórmula preenche múltiplas células automaticamente
- Se os dados mudam, os resultados atualizam automaticamente
- O Excel gerencia o espaço necessário (conceito de "spill")

#### Referência a Matriz Dinâmica
Para referenciar toda a matriz retornada por FILTRAR, use `#`:
```excel
=SOMA(B5#)
```
Isso soma todos os valores retornados pela fórmula em B5.

## Estrutura de Dados

### Modelo de Dados Normalizado

A estrutura segue um modelo simples de dados:

```
TipoAtivo | Ativo | PerfilRisco | Percentual
----------|-------|-------------|------------
FII       | HGLG11| Conservador | 15
FII       | KNRI11| Conservador | 15
...
```

**Vantagens:**
- Fácil manutenção
- Permite adicionar novos ativos facilmente
- Escalável para novos tipos de ativos ou perfis

### Chaves de Filtro

A combinação de duas chaves permite filtrar precisamente:
1. **TipoAtivo** - Primeira dimensão de filtro
2. **PerfilRisco** - Segunda dimensão de filtro

Cada combinação de chaves deve ter percentuais que somam 100%.

## Validação de Dados

### Listas Suspensas (Data Validation)

As listas suspensas garantem que o usuário só possa selecionar valores válidos:

**Tipo de Ativo:**
- Valores: FII, Criptomoedas
- Impede entrada de valores inválidos

**Perfil de Risco:**
- Valores: Conservador, Moderado, Agressivo
- Impede entrada de valores inválidos

### Vantagens da Validação
1. Previne erros de digitação
2. Garante que as fórmulas FILTRAR encontrarão correspondências
3. Melhora a experiência do usuário

## Alternativas para Excel Antigo

Se você estiver usando Excel 2019 ou anterior sem suporte a FILTRAR:

### Opção 1: Usar Fórmulas Tradicionais

#### Para listar ativos (exemplo com 10 linhas):
```excel
=SE(E(Dados_Completos!$A2=$B$1; Dados_Completos!$C2=$B$2); Dados_Completos!B2; "")
```
Copie esta fórmula para baixo (A5 até A15).

#### Para listar percentuais:
```excel
=SE(E(Dados_Completos!$A2=$B$1; Dados_Completos!$C2=$B$2); Dados_Completos!D2; "")
```

**Limitação:** Você precisa copiar para muitas linhas para garantir que todos os resultados apareçam.

### Opção 2: Usar Tabela Dinâmica

1. Crie uma Tabela Dinâmica dos dados
2. Configure:
   - Filtros: TipoAtivo, PerfilRisco
   - Linhas: Ativo
   - Valores: Soma de Percentual

**Limitação:** Menos dinâmico, requer atualização manual.

### Opção 3: Usar VBA

Criar uma macro que filtra e copia os dados quando há mudança nas células B1 ou B2.

**Limitação:** Requer conhecimento de VBA e habilitação de macros.

## Otimizações Possíveis

### 1. Usar Tabelas Estruturadas
Converter os dados para Tabelas Excel:
```excel
=FILTRAR(Tabela_Dados[Ativo]; (Tabela_Dados[TipoAtivo]=Dashboard!B1) * (Tabela_Dados[PerfilRisco]=Dashboard!B2))
```

**Vantagens:**
- Referências mais claras
- Expansão automática de dados
- Melhor performance

### 2. Adicionar Tratamento de Erro
```excel
=SENÃODISP(FILTRAR(...); "Nenhum ativo encontrado")
```

### 3. Criar Nomes Definidos
Definir nomes para intervalos:
- `TipoAtivo_Selecionado` = Dashboard!B1
- `PerfilRisco_Selecionado` = Dashboard!B2

Fórmula fica mais legível:
```excel
=FILTRAR(Dados_Completos!B:B; (Dados_Completos!A:A=TipoAtivo_Selecionado) * (Dados_Completos!C:C=PerfilRisco_Selecionado))
```

## Expansão da Estrutura

### Adicionar Novo Tipo de Ativo

1. Crie nova planilha: "Dados_NovoTipo"
2. Siga a mesma estrutura de colunas
3. Adicione os dados na planilha "Dados_Completos"
4. Atualize a lista suspensa em B1 para incluir o novo tipo

### Adicionar Novo Perfil de Risco

1. Adicione linhas nos arquivos CSV com o novo perfil
2. Importe os dados atualizados
3. Atualize a lista suspensa em B2 para incluir o novo perfil

### Adicionar Coluna de Informação Extra

Exemplo: Adicionar coluna "Setor" ou "Rentabilidade"

1. Adicione a coluna nas planilhas de dados (ex: coluna E)
2. Crie nova fórmula FILTRAR no Dashboard para exibir essa coluna
3. A mesma lógica de filtro se aplica

## Performance

### Considerações
- A função FILTRAR é eficiente mesmo com milhares de linhas
- Evite usar colunas inteiras (A:A) se tiver muitos dados; use intervalos específicos
- Exemplo: Dados_Completos!B2:B1000 ao invés de Dados_Completos!B:B

### Boas Práticas
1. Mantenha os dados organizados e limpos
2. Remova linhas vazias das tabelas de dados
3. Use formatação condicional para destacar resultados
4. Proteja as planilhas de dados contra edição acidental

## Referências

- [Documentação Microsoft - Função FILTRAR](https://support.microsoft.com/pt-br/office/fun%C3%A7%C3%A3o-filtrar-f4f7cb66-82eb-4767-8f7c-4877ad80c759)
- [Matrizes Dinâmicas no Excel](https://support.microsoft.com/pt-br/office/matrizes-din%C3%A2micas-e-comportamento-de-matriz-despejada-205c6b06-03ba-4151-89a1-87a7eb36e531)
