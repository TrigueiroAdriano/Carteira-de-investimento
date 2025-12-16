# Perguntas Frequentes (FAQ)

## Questões Gerais

### O que é este projeto?
É uma estrutura para criar uma planilha Excel dinâmica que ajuda a visualizar alocações de investimentos baseadas em tipo de ativo e perfil de risco.

### Preciso de conhecimento avançado em Excel?
Não. Se você sabe importar dados e copiar fórmulas, consegue criar a planilha seguindo os guias.

### Este projeto oferece recomendações de investimento?
**NÃO.** Este é apenas um exemplo educacional de como estruturar dados. Os ativos e percentuais são exemplos fictícios. Sempre faça sua própria pesquisa.

### Posso usar esta planilha com dinheiro real?
A estrutura é funcional, mas você deve:
1. Pesquisar cada ativo individualmente
2. Ajustar os percentuais conforme seu perfil
3. Consultar um assessor financeiro
4. Fazer sua própria análise de risco

## Requisitos Técnicos

### Qual versão do Excel preciso?
**Recomendado:** Excel 2021 ou Microsoft 365 (para função FILTRAR)

**Alternativas para versões antigas:**
- Excel 2019 ou anterior: Use fórmulas com ÍNDICE/CORRESP (veja [DOCUMENTACAO_TECNICA.md](DOCUMENTACAO_TECNICA.md))
- LibreOffice Calc: Versão 7.0+ suporta função similar
- Google Sheets: Usa função FILTER (sintaxe levemente diferente)

### Funciona no Google Sheets?
Sim, com adaptações:
- Use `FILTER` ao invés de `FILTRAR`
- Ajuste referências de planilhas: use `'Nome'!A:A`
- Validação de dados funciona de forma similar

### Funciona no LibreOffice?
Sim, no LibreOffice Calc 7.0+, mas o nome pode ser diferente. Consulte a documentação do LibreOffice.

### Funciona no Excel para Mac?
Sim, se for Microsoft 365 ou Excel 2021 para Mac.

## Uso da Planilha

### Como adiciono novos ativos?
1. Abra o arquivo CSV correspondente (`FII_Ativos.csv` ou `Cripto_Ativos.csv`)
2. Adicione novas linhas seguindo o formato:
   ```
   TipoAtivo,Ativo,PerfilRisco,Percentual
   FII,NOVO11,Conservador,10
   ```
3. Reimporte o CSV no Excel
4. Atualize a planilha `Dados_Completos`

### Como adiciono um novo tipo de ativo (ex: Ações)?
1. Crie arquivo `dados/Acoes_Ativos.csv` com a estrutura padrão
2. Importe no Excel como nova planilha `Dados_Acoes`
3. Copie os dados para `Dados_Completos`
4. Atualize a validação da célula B1: `FII,Criptomoedas,Ações`

### Como adiciono um novo perfil de risco (ex: Ultra Agressivo)?
1. Nos arquivos CSV, adicione linhas com `PerfilRisco` = "Ultra Agressivo"
2. Defina os ativos e percentuais para este perfil
3. Reimporte os dados
4. Atualize a validação da célula B2: `Conservador,Moderado,Agressivo,Ultra Agressivo`

### A soma dos percentuais não dá 100%. O que fazer?
Cada combinação de TipoAtivo + PerfilRisco deve somar 100%. Revise seus dados:
1. Filtre a planilha de dados pela combinação problemática
2. Some os percentuais manualmente
3. Ajuste até somar 100%

### Posso ter percentuais decimais?
Sim! Use formato como:
```
TipoAtivo,Ativo,PerfilRisco,Percentual
FII,HGLG11,Conservador,15.5
FII,KNRI11,Conservador,14.5
```

## Problemas Técnicos

### Erro: #NOME?
**Causa:** Excel não reconhece a função FILTRAR  
**Soluções:**
1. Atualize para Excel 2021/Microsoft 365, ou
2. Use fórmulas alternativas (veja documentação técnica), ou
3. Use Google Sheets

### Erro: #VALOR!
**Causas possíveis:**
1. Células B1 ou B2 vazias → Selecione valores válidos
2. Nomes de planilhas incorretos → Verifique nomes das planilhas
3. Tipo de dados incorreto → Certifique-se que percentuais são números

### Erro: #DESBORDAMENTO! ou #SPILL!
**Causa:** Não há espaço para exibir todos os resultados  
**Solução:** Limpe as células abaixo e ao lado de A5 e B5

### Nenhum resultado aparece
**Causas possíveis:**
1. **Valores não correspondem:** Verifique se o texto em B1/B2 é exatamente igual aos dados (cuidado com espaços extras)
2. **Dados vazios:** Confirme que `Dados_Completos` tem dados
3. **Nomes errados:** Verifique os nomes das planilhas nas fórmulas

### Os resultados não atualizam automaticamente
**Soluções:**
1. Pressione F9 para recalcular
2. Verifique se o cálculo automático está ativado: Fórmulas > Opções de Cálculo > Automático
3. Salve e reabra o arquivo

### Erro ao importar CSV
**Causas possíveis:**
1. **Codificação:** Os CSVs estão em UTF-8. Se houver problemas, tente abrir no Bloco de Notas e salvar novamente
2. **Delimitador:** Certifique-se de que o Excel está usando vírgula como delimitador
3. **Caminho:** Verifique se o arquivo CSV está no local correto

## Personalização

### Posso mudar as cores?
Sim! Veja [MODELO_ESTRUTURA.md](MODELO_ESTRUTURA.md) para sugestões de formatação e sinta-se livre para personalizar.

### Posso adicionar gráficos?
Sim! Recomendado:
1. **Gráfico de Pizza:** Selecione A5:B5#, insira gráfico de pizza
2. **Gráfico de Barras:** Para comparar alocações entre perfis

### Posso adicionar mais informações sobre cada ativo?
Sim! Adicione colunas extras nas planilhas de dados (ex: Setor, Rentabilidade, Liquidez) e crie fórmulas FILTRAR adicionais para exibi-las.

### Posso proteger as fórmulas?
Sim:
1. Selecione as células que os usuários podem editar (B1, B2)
2. Formato > Células > Proteção > Desmarque "Bloqueada"
3. Revisar > Proteger Planilha
4. Marque "Selecionar células bloqueadas" e "Selecionar células não bloqueadas"

## Performance

### A planilha fica lenta com muitos dados?
Para melhorar performance:
1. Use intervalos específicos ao invés de colunas inteiras:
   - `B2:B1000` em vez de `B:B`
2. Converta dados para Tabelas Excel
3. Evite fórmulas voláteis desnecessárias

### Quantos ativos posso adicionar?
A função FILTRAR suporta milhares de linhas sem problema. Limite prático depende do seu computador, mas facilmente 10.000+ registros.

## Dados de Exemplo

### Os ativos listados são reais?
Sim, os códigos de FII são reais (negociados na B3). As criptomoedas também são reais. Porém, os percentuais são exemplos fictícios.

### Os percentuais são recomendações?
**NÃO.** São apenas exemplos para demonstrar o funcionamento. Cada investidor deve determinar suas próprias alocações.

### Onde pesquiso mais sobre esses ativos?
- **FII:** Sites como FIIs.com.br, Investidor10, Status Invest
- **Criptomoedas:** CoinMarketCap, CoinGecko
- **Geral:** Consulte um assessor de investimentos

### Os dados estão atualizados?
Os dados são estáticos e exemplificativos. Você deve atualizá-los conforme sua pesquisa e estratégia.

## Contribuição

### Como posso contribuir?
1. Faça fork do repositório
2. Crie uma branch para sua feature
3. Faça suas alterações
4. Envie um Pull Request

### Que tipo de contribuições são bem-vindas?
- Novos perfis de alocação
- Dados adicionais (com fontes)
- Melhorias na documentação
- Traduções
- Correções de bugs
- Novos recursos

### Encontrei um erro. O que faço?
Abra uma Issue no GitHub descrevendo:
- O que você estava fazendo
- O que esperava acontecer
- O que aconteceu
- Prints de tela (se aplicável)

## Segurança e Privacidade

### Meus dados ficam seguros?
Sim. A planilha roda 100% localmente no seu computador. Nenhum dado é enviado para servidores externos.

### Posso compartilhar a planilha?
Sim, mas lembre-se:
- Não compartilhe informações pessoais sensíveis
- Se personalizou com seus investimentos reais, tenha cuidado com quem compartilha

## Suporte

### Onde obtenho ajuda?
1. Leia toda a documentação em `docs/`
2. Consulte este FAQ
3. Abra uma Issue no GitHub com sua dúvida

### Há um vídeo tutorial?
Atualmente não, mas contribuições são bem-vindas! Se você criar um tutorial, podemos adicionar link aqui.

### Posso contratar suporte?
Este é um projeto de código aberto sem suporte comercial. Para ajuda profissional, consulte um especialista em Excel ou investimentos.

## Avisos Legais

### Este é um produto regulamentado?
Não. É apenas uma ferramenta de planilha. Não é um produto financeiro.

### Há garantias?
Não. O projeto é fornecido "como está", sem garantias. Veja a licença do projeto.

### Posso usar comercialmente?
Verifique a licença do projeto. Geralmente projetos open source permitem uso comercial, mas confirme.

---

**Não encontrou sua pergunta?**  
Abra uma Issue no GitHub: [github.com/TrigueiroAdriano/Carteira-de-investimento/issues](https://github.com/TrigueiroAdriano/Carteira-de-investimento/issues)
