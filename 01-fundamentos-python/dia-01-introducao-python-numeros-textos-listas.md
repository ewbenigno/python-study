# Dia 01 — Introdução ao Python: números, textos e listas

**Fonte de estudo:** [Python Docs — An Informal Introduction to Python](https://docs.python.org/3/tutorial/introduction.html)

---

## O que eu estudei hoje

Hoje comecei oficialmente a trilha de Python, revisando a base da linguagem: como o interpretador funciona como calculadora, como manipular texto (strings) e como usar listas, a primeira estrutura de dados "de verdade" que a gente encontra no Python.

---

## 1. Números

O interpretador do Python funciona basicamente como uma calculadora. Dá pra digitar uma expressão matemática e ele já devolve o resultado na hora, sem precisar de `print()` quando tá no modo interativo.

Operadores básicos:

- `+` soma
- `-` subtração
- `*` multiplicação
- `/` divisão
- `()` pra agrupar operações, igual na matemática normal

```python
>>> 10 + 5
15
>>> 7 * 3
21
>>> (10 + 5) / 3
5.0
```

**Ponto importante:** a divisão com `/` **sempre** devolve um número decimal (`float`), mesmo que o resultado seja "redondo". Por isso `10 / 2` devolve `5.0` e não `5`.

Quando eu quero só a parte inteira da divisão, sem casas decimais, uso `//` (divisão inteira). E quando quero saber o resto da divisão, uso `%` (módulo):

```python
>>> 17 // 3   # divisão inteira, ignora o resto
5
>>> 17 % 3    # resto da divisão
2
```

Isso é bem útil, por exemplo, pra saber se um número é par ou ímpar (`numero % 2 == 0`).

Também existe o operador `**` pra potência:

```python
>>> 2 ** 10   # 2 elevado a 10
1024
```

### Tipos numéricos

- `int` → número inteiro (sem casas decimais). Ex: `5`, `20`, `-3`
- `float` → número com casas decimais. Ex: `5.0`, `3.14`

Quando misturo um `int` com um `float` numa operação, o resultado sempre vira `float`.

### Variáveis

Uso o sinal de `=` pra guardar um valor numa variável. Diferente de outras linguagens, não precisa declarar o tipo antes:

```python
>>> idade = 25
>>> altura = 1.75
```

Se eu tentar usar uma variável que ainda não existe, o Python quebra com um erro `NameError`, avisando que o nome não foi definido.

---

## 2. Texto (strings)

Texto em Python é representado pelo tipo `str`. Posso escrever entre aspas simples `'...'` ou aspas duplas `"..."`, dá no mesmo:

```python
>>> nome = 'Jorge'
>>> mensagem = "Bora estudar cyber"
```

**Quando usar cada uma?** Na prática funciona igual, mas fica mais prático usar aspas duplas quando o texto tem um apóstrofo dentro, tipo `"não é assim"`, pra não precisar escapar com `\`.

### Strings de múltiplas linhas

Pra textos grandes, com várias linhas, uso três aspas seguidas:

```python
>>> texto = """
... Primeira linha
... Segunda linha
... """
```

### Concatenação (juntar textos)

Uso o `+` pra grudar strings, e o `*` pra repetir:

```python
>>> "cyber" + "segurança"
'cyberseguranca'
>>> "ha" * 3
'hahaha'
```

### Indexação e slicing (fatiamento)

Cada caractere de uma string tem uma posição (índice), começando do **zero**:

```python
>>> palavra = "python"
>>> palavra[0]   # primeiro caractere
'p'
>>> palavra[-1]  # último caractere (índice negativo conta do final)
'n'
```

E dá pra pegar um "pedaço" da string com o fatiamento (slice), usando `[inicio:fim]`. O caractere do índice inicial entra, o do índice final **não** entra:

```python
>>> palavra[0:3]   # do índice 0 até o 3 (sem incluir o 3)
'pyt'
>>> palavra[3:]    # do índice 3 até o final
'hon'
```

**Ponto importante pra guardar:** strings em Python são **imutáveis**. Ou seja, depois que a string é criada, não dá pra trocar um caractere direto dentro dela (`palavra[0] = 'P'` dá erro). Se eu quiser mudar alguma coisa, tenho que montar uma string nova.

### Tamanho da string

A função `len()` devolve quantos caracteres tem a string:

```python
>>> len("cybersegurança")
14
```

---

## 3. Listas

Lista é a estrutura mais versátil do Python pra agrupar vários valores numa coleção só. É escrita entre colchetes `[]`, com os itens separados por vírgula.

```python
>>> ferramentas = ["nmap", "wireshark", "burpsuite"]
```

Uma lista pode misturar tipos diferentes dentro dela (números, textos, até outras listas), mas geralmente a gente usa listas com itens do mesmo tipo, pra manter organizado.

### Acessando itens (indexação e slicing)

Funciona igual string: índice começando em 0, e índice negativo conta a partir do final.

```python
>>> ferramentas[0]    # primeiro item
'nmap'
>>> ferramentas[-1]   # último item
'burpsuite'
>>> ferramentas[0:2]  # fatia do índice 0 até o 2 (sem incluir)
['nmap', 'wireshark']
```

### Listas são mutáveis

Diferente da string, a lista **pode ser alterada** depois de criada:

```python
>>> ferramentas[1] = "tcpdump"   # troquei o item da posição 1
>>> ferramentas
['nmap', 'tcpdump', 'burpsuite']
```

### Adicionando itens

Uso o método `.append()` pra adicionar um item no final da lista:

```python
>>> ferramentas.append("scapy")
>>> ferramentas
['nmap', 'tcpdump', 'burpsuite', 'scapy']
```

### Cuidado com cópia de listas

Um detalhe que achei importante: quando eu atribuo uma lista a outra variável, as duas variáveis passam a apontar pra **mesma lista** na memória. Se eu mudar uma, a outra muda junto:

```python
>>> lista_a = ["um", "dois"]
>>> lista_b = lista_a       # lista_b aponta pro mesmo lugar que lista_a
>>> lista_b.append("três")
>>> lista_a
['um', 'dois', 'três']      # lista_a também mudou!
```

Se eu quiser uma cópia de verdade, independente, uso o fatiamento completo `[:]`:

```python
>>> lista_c = lista_a[:]    # agora é uma cópia separada
```

### Listas dentro de listas (aninhadas)

É possível colocar uma lista dentro de outra:

```python
>>> letras = ["a", "b", "c"]
>>> numeros = [1, 2, 3]
>>> combinado = [letras, numeros]
>>> combinado[0]      # pega a lista de letras
['a', 'b', 'c']
>>> combinado[0][1]   # pega o item "b" dentro da lista de letras
'b'
```

---

## Resumo do dia

| Conceito | Ponto-chave |
|---|---|
| Números | `/` sempre devolve float, `//` é divisão inteira, `%` é resto, `**` é potência |
| Strings | Imutáveis, indexação começa em 0, slicing não inclui o índice final |
| Listas | Mutáveis, aceitam `.append()`, cuidado ao copiar (usar `[:]` pra cópia real) |
