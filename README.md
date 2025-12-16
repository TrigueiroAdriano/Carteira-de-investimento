# Carteira de Investimento - Excel Dinâmico

Sistema em Excel para seleção dinâmica de carteiras de investimento (FII e Criptomoedas), utilizando chaves seletoras e fórmulas modernas para listar ativos e percentuais automaticamente conforme o perfil de risco.

## 📋 Descrição

Este projeto fornece uma estrutura completa para criar uma planilha Excel que permite:
- ✅ Selecionar o tipo de ativo (FII ou Criptomoedas) através de lista suspensa
- ✅ Selecionar o perfil de risco (Conservador, Moderado ou Agressivo) através de lista suspensa
- ✅ Visualizar dinamicamente os ativos recomendados e suas alocações percentuais
- ✅ Utilizar a função moderna FILTRAR do Excel para listagem automática

## 🎯 Características

- **Dinâmico**: Mudanças nas seleções atualizam instantaneamente os resultados
- **Fácil de usar**: Interface simples com listas suspensas
- **Flexível**: Fácil adicionar novos ativos, tipos ou perfis
- **Moderno**: Utiliza funções de matriz dinâmica do Excel 2021/Microsoft 365

## 📁 Estrutura do Projeto

```
Carteira-de-investimento/
├── dados/
│   ├── FII_Ativos.csv           # Dados dos Fundos Imobiliários
│   └── Cripto_Ativos.csv        # Dados das Criptomoedas
├── docs/
│   ├── GUIA_CONSTRUCAO.md       # Guia passo-a-passo para construir a planilha
│   ├── COMO_USAR.md             # Manual de uso para usuários finais
│   └── DOCUMENTACAO_TECNICA.md  # Documentação técnica das fórmulas
└── README.md                     # Este arquivo
```

## 🚀 Como Começar

### Requisitos
- Microsoft Excel 2021 ou superior (ou Microsoft 365)
- Versões antigas do Excel não suportam a função FILTRAR (veja alternativas na documentação)

### Passos Rápidos

1. **Clone este repositório**
   ```bash
   git clone https://github.com/TrigueiroAdriano/Carteira-de-investimento.git
   ```

2. **Leia o Guia de Construção**
   - Abra `docs/GUIA_CONSTRUCAO.md`
   - Siga os passos detalhados para criar a planilha Excel

3. **Importe os Dados**
   - Use os arquivos CSV da pasta `dados/`
   - Importe no Excel seguindo as instruções do guia

4. **Configure as Fórmulas**
   - Implemente as fórmulas FILTRAR conforme documentado
   - Configure as listas suspensas

5. **Teste e Use**
   - Selecione diferentes combinações
   - Verifique os resultados

## 📚 Documentação

- **[Guia de Construção](docs/GUIA_CONSTRUCAO.md)**: Instruções detalhadas para criar a planilha do zero
- **[Como Usar](docs/COMO_USAR.md)**: Manual do usuário final
- **[Documentação Técnica](docs/DOCUMENTACAO_TECNICA.md)**: Explicação das fórmulas e estrutura de dados

## 💡 Exemplo de Uso

1. Abra a planilha Dashboard
2. Selecione "FII" na lista de Tipo de Ativo
3. Selecione "Conservador" na lista de Perfil de Risco
4. Visualize automaticamente 5 fundos imobiliários com suas alocações

## 📊 Dados Incluídos

### FII (Fundos de Investimento Imobiliário)
- Perfil Conservador: 5 fundos
- Perfil Moderado: 7 fundos
- Perfil Agressivo: 9 fundos

### Criptomoedas
- Perfil Conservador: 3 ativos
- Perfil Moderado: 5 ativos
- Perfil Agressivo: 7 ativos

## 🔧 Personalização

Você pode facilmente:
- Adicionar novos ativos editando os arquivos CSV
- Criar novos tipos de ativos (ex: Ações, Renda Fixa)
- Adicionar novos perfis de risco
- Modificar os percentuais de alocação

Consulte a [Documentação Técnica](docs/DOCUMENTACAO_TECNICA.md) para detalhes.

## ⚠️ Avisos Importantes

- **Não é recomendação de investimento**: Esta é apenas uma ferramenta educacional
- **Faça sua própria pesquisa**: Sempre analise os ativos antes de investir
- **Considere ajuda profissional**: Consulte um assessor financeiro se necessário
- **Rentabilidade passada não garante resultados futuros**

## 🤝 Contribuindo

Contribuições são bem-vindas! Sinta-se à vontade para:
- Abrir issues com sugestões ou bugs
- Enviar pull requests com melhorias
- Adicionar novos perfis de alocação
- Melhorar a documentação

## 📄 Licença

Este projeto é de código aberto e está disponível para uso educacional e pessoal.

## 📧 Contato

Para dúvidas ou sugestões, abra uma issue neste repositório.

---

**Versão**: 1.0.0  
**Última atualização**: Dezembro 2025
