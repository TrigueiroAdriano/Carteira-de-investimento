# 📊 Projeto: Seletor Dinâmico de Carteira (FII e Criptomoedas)

Este projeto implementa, em **Excel**, um sistema dinâmico de seleção de carteiras de investimento, permitindo ao usuário alternar entre **FII** e **Criptomoedas** e escolher o **perfil de risco** (Conservador, Moderado ou Agressivo). A partir dessas escolhas, o Excel **lista automaticamente** os ativos e seus percentuais correspondentes.

O objetivo é oferecer uma base **organizada, reutilizável e escalável**, ideal para dashboards financeiros pessoais.

---

## 🎯 Objetivo do Projeto

* Centralizar regras de alocação de carteira (FII e Crypto)
* Utilizar **duas chaves seletoras** no Excel
* Evitar fórmulas complexas por linha (PROCV repetido)
* Permitir expansão futura (novos perfis, novos ativos)

---

## 🧱 Estrutura do Arquivo Excel

O arquivo é dividido em **3 abas principais**:

### 1️⃣ `Planilha2` — Base de Dados

Esta aba contém **todos os dados brutos**. Não deve conter fórmulas complexas.

| Coluna | Nome                | Descrição                                             |
| ------ | ------------------- | ----------------------------------------------------- |
| A      | CHAVE_SELETORA      | Combinação de CLASSE + PERFIL (ex: `FII-Conservador`) |
| B      | ATIVO               | Classe principal (`FII` ou `CRYPTO`)                  |
| C      | PERFIL              | Conservador / Moderado / Agressivo                    |
| D      | TIPO DE FII / MOEDA | Papel, Tijolo, BTC, ETH etc                           |
| E      | %                   | Percentual de alocação                                |

### 📌 Exemplo:

```
FII-Conservador | FII | Conservador | PAPEL | 30%
CRYPTO-Moderado | CRYPTO | Moderado | Bitcoin (BTC) | 30%
```

---

### 2️⃣ `APP` (ou Tela Principal)

Área de interação do usuário.

#### 🔑 Chaves Seletoras

| Célula | Função                                          |
| ------ | ----------------------------------------------- |
| D31    | Tipo de Ativo (`FII` ou `CRYPTO`)               |
| D32    | Perfil (`Conservador`, `Moderado`, `Agressivo`) |

Essas células utilizam **Validação de Dados → Lista**.

---

### 3️⃣ Área de Resultado (na própria `APP`)

A lista dinâmica começa na **linha 38**.

| Coluna | Conteúdo                   |
| ------ | -------------------------- |
| A      | Tipo de FII ou Criptomoeda |
| B      | Percentual                 |

---

## 🧠 Fórmulas Utilizadas

### 🔹 Listar Ativos (A38)

```excel
=FILTRAR(
Planilha2!D:D;
Planilha2!A:A=$D$31&"-"&$D$32
)
```

### 🔹 Listar Percentuais (B38)

```excel
=FILTRAR(
Planilha2!E:E;
Planilha2!A:A=$D$31&"-"&$D$32
)
```

📌 **Importante:**

* As fórmulas devem ser inseridas **somente na primeira célula** (A38 e B38)
* **Não arrastar**
* O Excel fará o preenchimento automático (SPILL)

---

## ⚠️ Erro #TRANSPOSIÇÃO! (SPILL)

Este erro **não indica problema na fórmula**, apenas que o espaço abaixo está bloqueado.

### ✔️ Como Resolver

1. Limpar as células abaixo (A39:A60 e B39:B60)
2. Remover células mescladas
3. Garantir que não seja uma **Tabela do Excel (Ctrl + T)**
4. Inserir a fórmula novamente apenas na célula inicial

---

## 🚫 Por que NÃO usar PROCV?

* O PROCV retorna **apenas o primeiro resultado encontrado**
* Não funciona para listas dinâmicas
* Causa repetição de valores (ex: BTC em todas as linhas)

✅ `FILTRAR` é a solução correta para este cenário.

---

## 📈 Expansões Futuras

Este modelo permite facilmente:

* Inclusão de novos perfis
* Inclusão de novos ativos
* Criação de gráficos automáticos
* Simulação de aportes mensais
* Dashboard consolidado (FII + Crypto)

---

## 🛠️ Requisitos

* Excel 365 ou Excel 2021
* Funções dinâmicas habilitadas (`FILTRAR`)

---

## 👤 Autor / Contexto

Projeto desenvolvido como parte de um sistema pessoal de organização financeira, com foco em:

* Clareza visual
* Facilidade de uso
* Manutenção simples

---

## ✅ Status do Projeto

✔️ Funcional
✔️ Escalável
✔️ Pronto para dashboard

---

