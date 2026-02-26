# Aula — Introdução à Lógica de Programação

!!! info "Informações da Aula"
    **Disciplina:** PAC I / Fundamentos de Programação  
    **Data:** Fevereiro de 2026  
    **Tema:** Algoritmos e Lógica de Programação

---

## 🧠 O que é Lógica de Programação?

**Lógica de Programação** é a linha de raciocínio utilizada para criar um algoritmo. É a forma como você pensa para resolver um problema de maneira estruturada.

**Algoritmo** é o passo a passo de instruções que você passa para o computador executar.

### Analogia do dia a dia

Pense em uma receita de bolo:

1. Separar os ingredientes
2. Misturar a farinha com o açúcar
3. Adicionar os ovos
4. Bater por 5 minutos
5. Colocar no forno por 40 minutos

Isso é um **algoritmo**! Um passo a passo para chegar a um resultado.

---

## 📝 Formas de Representar a Lógica

Existem 3 formas principais de escrever um algoritmo:

| Forma | Descrição | Exemplo |
|-------|-----------|---------|
| **Descrição Narrativa** | Em português simples, como uma redação | "Primeiro, pegue o valor do tanque..." |
| **Fluxograma** | Representação visual com formas geométricas | Diagrama com setas e caixas |
| **Pseudocódigo (Portugol)** | Forma intermediária entre português e código | `capacidade_tanque = 50` |

### Fluxograma — Símbolos Básicos

```
    ┌─────────┐
    │ INÍCIO  │  ← Início/Fim (oval)
    └────┬────┘
         │
    ┌────▼────┐
    │ Processo │  ← Processamento (retângulo)
    └────┬────┘
         │
    ◇────▼────◇
   ╱ Decisão?  ╲  ← Decisão (losango)
  ╱             ╲
 Sim            Não
```

!!! tip "Ferramenta"
    O **Flowgorithm** é uma ferramenta gratuita para criar fluxogramas que você vai usar no PAC!

---

## 🎯 As 3 Perguntas Mágicas

!!! warning "Muito Importante!"
    Sempre que for resolver um problema de programação, faça estas 3 perguntas:

| # | Pergunta | O que significa |
|---|----------|-----------------|
| 1 | **Qual resultado você quer?** | O que o programa deve mostrar/fazer no final? |
| 2 | **O que preciso de informação para chegar nesse resultado?** | Quais dados de entrada são necessários? |
| 3 | **Qual o passo a passo para fazer o que quero?** | Qual a sequência lógica de operações? |

### Exemplo Prático

**Problema:** Calcular quanto custa encher o tanque do carro.

| Pergunta | Resposta |
|----------|----------|
| 1. Qual resultado? | O custo total para encher o tanque |
| 2. O que preciso? | Capacidade do tanque, litros atuais, preço do litro |
| 3. Passo a passo? | Calcular litros faltando → Multiplicar pelo preço |

---

## 📦 Variáveis e Tipos de Dados

### O que é uma Variável?

Uma **variável** é uma "caixinha" na memória do computador onde guardamos informações.

```
nome_da_variavel = valor
```

!!! warning "Regras para nomes de variáveis"
    - Não começar com número
    - Não usar espaços (use `_` no lugar)
    - Não usar caracteres especiais (#, @, !)
    - Usar nomes descritivos: `preco_produto` é melhor que `p`

### Tipos de Dados

| Tipo | O que guarda | Exemplo |
|------|--------------|---------|
| **inteiro (int)** | Números sem casas decimais | `idade = 25` |
| **float** | Números com casas decimais | `preco = 19.90` |
| **string** | Textos (entre aspas) | `nome = "João"` |
| **boolean** | Verdadeiro ou Falso | `ativo = True` |

### Estruturas de Dados (Coleções)

| Tipo | O que é | Exemplo |
|------|---------|---------|
| **Lista** | Conjunto ordenado de valores | `notas = [7, 8, 9, 10]` |
| **Dicionário** | Pares de chave e valor | `produto = {"nome": "Celular", "preco": 1500}` |

---

## ➕ Operadores

### Operadores Matemáticos

| Operador | Significado | Exemplo | Resultado |
|----------|-------------|---------|-----------|
| `+` | Soma | `5 + 3` | `8` |
| `-` | Subtração | `10 - 4` | `6` |
| `*` | Multiplicação | `6 * 2` | `12` |
| `/` | Divisão | `15 / 3` | `5` |
| `%` | Resto da divisão | `10 % 3` | `1` |
| `**` | Potência | `2 ** 3` | `8` |

### Operadores de Comparação

| Operador | Significado | Exemplo | Resultado |
|----------|-------------|---------|-----------|
| `>` | Maior que | `5 > 3` | `True` |
| `<` | Menor que | `5 < 3` | `False` |
| `>=` | Maior ou igual | `5 >= 5` | `True` |
| `<=` | Menor ou igual | `4 <= 3` | `False` |
| `==` | Igual a | `5 == 5` | `True` |
| `!=` | Diferente de | `5 != 3` | `True` |

### Operadores Lógicos

| Operador | Significado | Exemplo |
|----------|-------------|---------|
| `and` (E) | Ambos verdadeiros | `(5 > 3) and (2 < 4)` → `True` |
| `or` (OU) | Pelo menos um verdadeiro | `(5 > 3) or (2 > 4)` → `True` |
| `not` (NÃO) | Inverte o valor | `not True` → `False` |

---

## 🔀 Estruturas Condicionais (Se/Senão)

Permitem que o programa tome decisões baseadas em condições.

### Estrutura Básica

```
Se condição então {
    // código se verdadeiro
} Caso contrário {
    // código se falso
}
```

### Exemplo 1: Bônus de Funcionário

**Regra:** Se vendas > 1000, bônus = 250. Caso contrário, bônus = 50.

```
vendas = 1200
meta = 1000

Se vendas > meta então {
    bonus = 250
} Caso contrário {
    bonus = 50
}

exibir(bonus)
```

**Resultado:** 250 (porque 1200 > 1000)

### Exemplo 2: Múltiplas Condições (If dentro de If)

**Regra:** Bônus de 250 se a empresa E o funcionário baterem a meta.

```
vendas = 1200
meta = 1000
vendas_empresa = 11000
meta_empresa = 10000

Se vendas_empresa > meta_empresa então {
    Se vendas > meta então {
        bonus = 250
    } Caso contrário {
        bonus = 50
    }
} Caso contrário {
    bonus = 0
}

exibir(bonus)
```

!!! tip "Dica da aula"
    Pode colocar **if dentro de if**! A identação (espaços) é muito importante para o código funcionar corretamente.

---

## 🔁 Estruturas de Repetição (Loops)

Permitem repetir um bloco de código várias vezes.

### Para (For) — Quando você sabe quantas vezes repetir

```
Para cada item, até N vezes {
    // código a repetir
}
```

**Exemplo:** Calcular salário com 10% de aumento por 10 anos

```
salario = 2000
aumento = 0.1
tempo = 10

Para cada ano, até tempo anos {
    salario = salario * (1 + aumento)
}

exibir(salario)
```

### Enquanto (While) — Quando não sabe quantas vezes

```
Enquanto condição faça {
    // código a repetir
}
```

**Exemplo:** Quanto tempo para o salário chegar a R$10.000?

```
salario = 2000
aumento = 0.1
tempo = 0

Enquanto salario < 10000 faça {
    salario = salario * (1 + aumento)
    tempo = tempo + 1
}

exibir(tempo)
```

**Resultado:** 17 anos

---

## 🧩 Funções (Modularização)

Funções servem para **organizar o código** e **evitar repetição**.

### Por que usar funções?

- Separar código grande em pequenas funcionalidades
- Reutilizar código sem copiar/colar
- Facilitar manutenção (mudar em um lugar só)
- **Decomposição Top-Down:** dividir problema grande em problemas menores

### Estrutura de uma Função

```
Funcao nome_da_funcao(parametros) {
    // código da função
    retornar resultado
}
```

### Exemplo

```
Funcao calcular_custo_total(lista_salarios) {
    total = somar todos os itens(lista_salarios)
    exibir(total)
}

Funcao calcular_diferenca(novo_total, antigo_total) {
    diferenca = novo_total - antigo_total
    exibir(diferenca)
}
```

!!! tip "Dica da aula"
    Um código bem **encapsulado** (organizado em funções) vai te ajudar quando ocorrerem mudanças nos cálculos — você não precisa ficar caçando onde mudar!

---

## 💻 Exemplos Práticos Completos

### Exemplo 1: Cálculo de Projeto Freelancer

**Problema:** Calcular o valor de um projeto trabalhando 8h/dia por 15 dias a R$100/h.

```
horas_por_dia = 8
dias_totais = 15
horas_trabalho = horas_por_dia * dias_totais
custo_hora = 100
custo_total = horas_trabalho * custo_hora

exibir(custo_total)
```

**Passo a passo:**
1. Descobrir total de horas: 8 × 15 = 120 horas
2. Multiplicar pelo valor da hora: 120 × 100 = R$12.000

### Exemplo 2: Custo para Encher o Tanque

**Problema:** Tanque de 50L com 20L, combustível a R$5,80/L.

```
capacidade_tanque = 50
combustivel_atual = 20
valor_combustivel = 5.80

necessidade_abastecimento = capacidade_tanque - combustivel_atual
custo_tanque_cheio = necessidade_abastecimento * valor_combustivel

exibir(custo_tanque_cheio)
```

**Passo a passo:**
1. Descobrir quantos litros faltam: 50 - 20 = 30 litros
2. Multiplicar pelo preço: 30 × 5,80 = R$174,00

### Exemplo 3: Reajuste de Lista de Preços

**Problema:** Aplicar 5% de aumento em uma lista de produtos.

```
lista_precos = [100, 500, 1000, 1500]
reajuste = 0.05
lista_reajustada = []

Para cada preco na lista_precos faça {
    novo_preco = preco * (1 + reajuste)
    Adicione novo_preco na lista_reajustada
}

exibir(lista_reajustada)
```

**Resultado:** [105, 525, 1050, 1575]

---

## 📖 Glossário

| Termo | Significado |
|-------|-------------|
| **Algoritmo** | Passo a passo para o computador executar |
| **Variável** | Espaço na memória para guardar dados |
| **Condicional** | Estrutura que permite decisões (if/else) |
| **Loop** | Estrutura que repete código (for/while) |
| **Função** | Bloco de código reutilizável |
| **Identação** | Espaços no início da linha (muito importante!) |
| **Pseudocódigo** | Código em português para planejar a lógica |
| **Flowgorithm** | Ferramenta para criar fluxogramas |
| **Append** | Adiciona um item no final de uma lista |
| **Boolean** | Tipo de dado que só pode ser True ou False |

---

## ✅ Checklist de Aprendizagem

### Conceitos Básicos
- [ ] Entendo o que é lógica de programação
- [ ] Sei o que é um algoritmo
- [ ] Conheço as 3 formas de representar lógica
- [ ] Sei usar as 3 perguntas mágicas

### Variáveis e Tipos
- [ ] Sei criar variáveis
- [ ] Entendo os tipos: int, float, string, boolean
- [ ] Sei a diferença entre lista e dicionário

### Operadores
- [ ] Sei usar operadores matemáticos (+, -, *, /)
- [ ] Sei usar operadores de comparação (>, <, ==)
- [ ] Entendo operadores lógicos (and, or, not)

### Estruturas
- [ ] Sei usar if/else para decisões
- [ ] Sei usar for para repetições com contagem
- [ ] Sei usar while para repetições com condição
- [ ] Entendo o conceito de funções

---

## 🎬 Recursos Recomendados

| Recurso | Link/Descrição |
|---------|----------------|
| **Curso Hashtag** | Algoritmos e Lógica de Programação (base desta aula) |
| **Flowgorithm** | flowgorithm.org - Ferramenta para fluxogramas |
| **Portugol Studio** | portugol-webstudio.cubos.io - Praticar pseudocódigo |
| **Visualgo** | visualgo.net - Visualizar algoritmos |

---

## 🔜 Próximas Aulas

- **Flowgorithm** — Criando algoritmos visuais
- **Atividade Prática** — Lógica aplicada ao Flowgorithm
- **Revisão de Programação** — Linguagem C

---

!!! quote "Lembre-se"
    "A melhor forma de aprender é praticar junto com uma linguagem de programação, cuidando sempre da didática e seguindo um fluxo lógico de aprendizado."
