# Guia de Contribuição

Obrigado por considerar contribuir para o projeto Carteira de Investimento! 

## Como Contribuir

### Reportar Bugs

Se você encontrar um bug:

1. Verifique se já não existe uma Issue sobre o problema
2. Abra uma nova Issue incluindo:
   - Descrição clara do problema
   - Passos para reproduzir
   - Comportamento esperado vs. observado
   - Screenshots (se aplicável)
   - Versão do Excel que está usando

### Sugerir Melhorias

Para sugestões de novas funcionalidades:

1. Verifique se a sugestão já não foi feita
2. Abra uma Issue descrevendo:
   - O problema que a funcionalidade resolve
   - Como você imagina que funcionaria
   - Exemplos de uso

### Contribuir com Código

1. **Fork o repositório**
   ```bash
   git fork https://github.com/TrigueiroAdriano/Carteira-de-investimento.git
   ```

2. **Clone seu fork**
   ```bash
   git clone https://github.com/SEU_USUARIO/Carteira-de-investimento.git
   cd Carteira-de-investimento
   ```

3. **Crie uma branch**
   ```bash
   git checkout -b feature/minha-contribuicao
   ```

4. **Faça suas alterações**
   - Mantenha o estilo consistente
   - Teste suas mudanças
   - Documente novos recursos

5. **Commit suas mudanças**
   ```bash
   git add .
   git commit -m "Descrição clara da mudança"
   ```

6. **Push para seu fork**
   ```bash
   git push origin feature/minha-contribuicao
   ```

7. **Abra um Pull Request**
   - Descreva o que foi mudado e por quê
   - Referencie Issues relacionadas

## Tipos de Contribuição Bem-Vindas

### Dados
- Novos ativos com alocações bem fundamentadas
- Novos perfis de risco
- Novos tipos de ativos (Ações, Renda Fixa, etc.)
- **Importante:** Sempre cite suas fontes

### Documentação
- Correções de erros
- Melhorias na clareza
- Traduções para outros idiomas
- Novos guias ou tutoriais
- Vídeos explicativos

### Funcionalidades
- Melhorias nas fórmulas
- Novas visualizações
- Ferramentas auxiliares
- Scripts de automação

### Testes
- Validação em diferentes versões do Excel
- Testes em Google Sheets
- Testes em LibreOffice Calc

## Diretrizes de Estilo

### Documentação
- Use linguagem clara e objetiva
- Inclua exemplos práticos
- Mantenha formatação Markdown consistente
- Use títulos e subtítulos apropriados

### Dados CSV
- Use vírgula como delimitador
- UTF-8 como codificação
- Mantenha a estrutura de colunas existente
- Certifique-se de que percentuais somam 100% por perfil

### Nomenclatura
- Arquivos: `Snake_Case.csv` ou `PascalCase.md`
- Planilhas Excel: PascalCase (ex: `Dados_FII`)
- Células: Referências absolutas quando necessário

## Checklist do Pull Request

Antes de enviar seu PR, verifique:

- [ ] Código/documentação está clara e bem comentada
- [ ] Testei as mudanças
- [ ] Documentação foi atualizada (se necessário)
- [ ] Arquivos de dados mantêm integridade (soma = 100%)
- [ ] Não há conflitos com a branch main
- [ ] Commit messages são descritivas

## Código de Conduta

### Nossos Compromissos

- Ser respeitoso e inclusivo
- Aceitar críticas construtivas
- Focar no que é melhor para a comunidade
- Mostrar empatia com outros membros

### Comportamentos Inaceitáveis

- Linguagem ofensiva ou discriminatória
- Assédio público ou privado
- Publicar informações privadas de outros
- Conduta não profissional ou inadequada

### Aplicação

Comportamentos inaceitáveis podem ser reportados abrindo uma Issue ou entrando em contato com os mantenedores. Todas as reclamações serão revisadas e investigadas.

## Processo de Revisão

1. **Revisão Inicial**: Um mantenedor revisará seu PR em até 7 dias
2. **Feedback**: Você pode receber pedidos de mudanças ou esclarecimentos
3. **Iteração**: Faça as alterações solicitadas
4. **Aprovação**: Após aprovação, seu PR será mesclado
5. **Agradecimento**: Você será creditado nas notas de versão!

## Perguntas?

Se tiver dúvidas sobre como contribuir:

1. Leia a documentação em `docs/`
2. Consulte o FAQ em `docs/FAQ.md`
3. Abra uma Issue com sua pergunta
4. Entre em contato com os mantenedores

## Reconhecimento

Todos os contribuidores serão listados e reconhecidos. Obrigado por ajudar a melhorar este projeto! 🎉

## Licença

Ao contribuir, você concorda que suas contribuições serão licenciadas sob a mesma licença do projeto (MIT License).

---

**Obrigado por contribuir! 🚀**
