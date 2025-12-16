# Guia de Início Rápido

## Para Quem Quer Usar a Planilha (5 minutos)

### Passo 1: Baixar o Projeto
```bash
git clone https://github.com/TrigueiroAdriano/Carteira-de-investimento.git
cd Carteira-de-investimento
```

### Passo 2: Criar o Arquivo Excel
1. Abra o Microsoft Excel
2. Crie uma nova pasta de trabalho
3. Salve como `Carteira_Investimentos.xlsx`

### Passo 3: Importar os Dados

**Importar FII:**
1. No Excel, vá em `Dados > Obter Dados > De Arquivo > De Texto/CSV`
2. Selecione `dados/FII_Ativos.csv`
3. Clique em `Carregar`
4. Renomeie a planilha para "Dados_FII"

**Importar Criptomoedas:**
1. Repita o processo com `dados/Cripto_Ativos.csv`
2. Renomeie a planilha para "Dados_Cripto"

### Passo 4: Criar Planilha Completa
1. Crie uma nova planilha chamada "Dados_Completos"
2. Copie todos os dados de "Dados_FII" para ela
3. Cole os dados de "Dados_Cripto" logo abaixo (na próxima linha vazia)

### Passo 5: Criar o Dashboard
1. Crie uma nova planilha chamada "Dashboard"
2. Configure conforme a tabela abaixo:

| Célula | Conteúdo |
|--------|----------|
| A1 | TIPO DE ATIVO |
| A2 | PERFIL DE RISCO |
| A4 | ATIVO |
| B4 | ALOCAÇÃO (%) |

### Passo 6: Criar Listas Suspensas

**Em B1:**
1. Selecione a célula B1
2. Vá em `Dados > Validação de Dados`
3. Permitir: Lista
4. Fonte: `FII,Criptomoedas`
5. OK

**Em B2:**
1. Selecione a célula B2
2. Vá em `Dados > Validação de Dados`
3. Permitir: Lista
4. Fonte: `Conservador,Moderado,Agressivo`
5. OK

### Passo 7: Adicionar as Fórmulas

**Em A5:**
```excel
=FILTRAR(Dados_Completos!B:B;(Dados_Completos!A:A=Dashboard!B1)*(Dados_Completos!C:C=Dashboard!B2))
```

**Em B5:**
```excel
=FILTRAR(Dados_Completos!D:D;(Dados_Completos!A:A=Dashboard!B1)*(Dados_Completos!C:C=Dashboard!B2))
```

### Passo 8: Testar
1. Em B1, selecione "FII"
2. Em B2, selecione "Conservador"
3. Verifique se aparecem 5 fundos com seus percentuais

✅ **Pronto! Sua planilha está funcionando!**

---

## Para Quem Quer Criar do Zero (30 minutos)

Siga o guia completo em: [docs/GUIA_CONSTRUCAO.md](GUIA_CONSTRUCAO.md)

---

## Solução de Problemas Rápida

### Erro: #NOME?
**Problema:** Excel não reconhece a função FILTRAR  
**Solução:** Você precisa do Excel 2021 ou Microsoft 365

### Nenhum resultado aparece
**Problema:** Fórmula não encontra dados  
**Solução:** 
- Verifique se os nomes das planilhas estão corretos
- Confirme que B1 e B2 têm valores selecionados
- Verifique se a planilha Dados_Completos tem dados

### Erro: #DESBORDAMENTO!
**Problema:** Não há espaço para os resultados  
**Solução:** Limpe as células abaixo de A5 e B5

---

## Próximos Passos

Após ter a planilha funcionando:

1. **Personalize os dados**: Edite os arquivos CSV com seus ativos preferidos
2. **Adicione formatação**: Use cores e estilos (veja [MODELO_ESTRUTURA.md](MODELO_ESTRUTURA.md))
3. **Crie gráficos**: Adicione um gráfico de pizza da alocação
4. **Leia mais**: Consulte [COMO_USAR.md](COMO_USAR.md) para dicas de uso

---

## Ajuda Adicional

- 📖 **Manual Completo**: [COMO_USAR.md](COMO_USAR.md)
- 🔧 **Detalhes Técnicos**: [DOCUMENTACAO_TECNICA.md](DOCUMENTACAO_TECNICA.md)
- 🎨 **Modelo Visual**: [MODELO_ESTRUTURA.md](MODELO_ESTRUTURA.md)

---

## Atalhos Úteis do Excel

| Ação | Atalho |
|------|--------|
| Validação de Dados | Alt + D, L |
| Inserir Função | Shift + F3 |
| Salvar | Ctrl + S |
| Ir para célula | Ctrl + G |

---

**Tempo estimado de setup**: 5-10 minutos  
**Dificuldade**: ⭐⭐☆☆☆ (Fácil)
