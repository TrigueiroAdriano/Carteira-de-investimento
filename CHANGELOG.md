# Changelog

Todas as mudanças notáveis neste projeto serão documentadas neste arquivo.

O formato é baseado em [Keep a Changelog](https://keepachangelog.com/pt-BR/1.0.0/),
e este projeto adere ao [Semantic Versioning](https://semver.org/lang/pt-BR/).

## [1.0.0] - 2025-12-16

### Adicionado
- Estrutura inicial do projeto
- Arquivos de dados CSV para FII (21 ativos em 3 perfis de risco)
- Arquivos de dados CSV para Criptomoedas (15 ativos em 3 perfis de risco)
- Documentação completa em português:
  - README.md com visão geral do projeto
  - GUIA_INICIO_RAPIDO.md para setup rápido (5 minutos)
  - GUIA_CONSTRUCAO.md com instruções detalhadas passo-a-passo
  - COMO_USAR.md com manual do usuário
  - DOCUMENTACAO_TECNICA.md com explicação das fórmulas Excel
  - MODELO_ESTRUTURA.md com layout visual da planilha
  - DIAGRAMA_FLUXO.md com diagramas explicativos
  - FAQ.md com perguntas frequentes
- CONTRIBUTING.md com guia de contribuição
- LICENSE (MIT License)
- .gitignore para arquivos temporários

### Estrutura
- `/dados/` - Arquivos CSV com dados dos ativos
- `/docs/` - Documentação completa do projeto

### Características
- Seleção dinâmica de tipo de ativo (FII ou Criptomoedas)
- Seleção dinâmica de perfil de risco (Conservador, Moderado, Agressivo)
- Uso da função FILTRAR do Excel para listagem automática
- Estrutura extensível para adicionar novos tipos de ativos
- Dados de exemplo prontos para uso

### Perfis de Risco Incluídos

**FII:**
- Conservador: 5 fundos
- Moderado: 7 fundos  
- Agressivo: 9 fundos

**Criptomoedas:**
- Conservador: 3 ativos
- Moderado: 5 ativos
- Agressivo: 7 ativos

### Requisitos
- Microsoft Excel 2021 ou superior (ou Microsoft 365)
- Alternativas: Google Sheets, LibreOffice Calc 7.0+

### Notas
- Esta é a versão inicial do projeto
- Os dados são exemplos educacionais, não recomendações de investimento
- Todas as documentações estão em português brasileiro

---

## [Não Lançado]

### Planejado para Futuras Versões
- Arquivo Excel de exemplo pronto para download
- Gráficos de alocação pré-configurados
- Calculadora de rebalanceamento
- Histórico de performance
- Mais tipos de ativos (Ações, Renda Fixa, ETFs)
- Traduções para outros idiomas
- Vídeo tutorial
- Planilha com acompanhamento de investimentos reais
- Integração com APIs de cotação

### Contribuições Bem-Vindas
Veja [CONTRIBUTING.md](CONTRIBUTING.md) para saber como contribuir.

---

## Tipos de Mudanças
- `Adicionado` - para novas funcionalidades
- `Alterado` - para mudanças em funcionalidades existentes
- `Obsoleto` - para funcionalidades que serão removidas
- `Removido` - para funcionalidades removidas
- `Corrigido` - para correção de bugs
- `Segurança` - para vulnerabilidades de segurança
