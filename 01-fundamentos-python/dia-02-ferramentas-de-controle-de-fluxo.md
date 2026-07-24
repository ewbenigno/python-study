# Dia 02 — Ferramentas de controle de fluxo

**Fonte de estudo:** [Python Docs — More Control Flow Tools](https://docs.python.org/3/tutorial/controlflow.html)

---

## O que eu estudei hoje

Hoje estudei as principais ferramentas que o Python oferece pra **controlar o fluxo** do programa, ou seja, decidir o que executa, quando executa e quantas vezes executa. Isso inclui estruturas condicionais, laços de repetição e, principalmente, como criar minhas próprias funções.

> **Pra quem tá começando:** "controle de fluxo" é só um nome bonito pra "como o programa decide o que fazer a seguir". Todo programa de verdade precisa disso, sem controle de fluxo o código só executaria de cima pra baixo uma vez só, sem poder repetir nada nem tomar decisões.

---

## 1. Estrutura condicional `if`

O `if` testa uma condição e só executa o bloco de código se ela for verdadeira. Pode ter `elif` (quantos eu quiser) pra testar outras condições, e um `else` no final pra cobrir todos os outros casos.

```python
nota = 7

if nota >= 9:
    print("Excelente")
elif nota >= 7:
    print("Bom")
elif nota >= 5:
    print("Regular")
else:
    print("Precisa melhorar")
```

**Explicando de forma simples:** o Python testa as condições na ordem, de cima pra baixo. Assim que uma delas é verdadeira, ele executa aquele bloco e ignora o resto. Se nenhuma bater, cai no `else`.

`elif` é a abreviação de "else if" (senão, se), e existe pra eu não precisar ficar aninhando vários `if` dentro de `else`, o que deixaria o código cheio de indentação.

---

## 2. Laço `for`

Diferente de outras linguagens, o `for` em Python não trabalha só com contagem numérica. Ele percorre os itens de qualquer sequência (lista, string, etc), na ordem em que aparecem.

```python
ferramentas = ["nmap", "wireshark", "burpsuite"]

for item in ferramentas:
    print(item, len(item))
```

**Explicando de forma simples:** pensa no `for` como "pra cada item dentro dessa coleção, faz isso aqui". Ele passa item por item até acabar a lista, sem eu precisar controlar manualmente um contador.

**Cuidado:** alterar uma lista enquanto estou percorrendo ela com `for` pode causar bugs difíceis de perceber. O jeito seguro é percorrer uma cópia da lista, ou construir uma lista nova com o resultado.

---

## 3. A função `range()`

Quando eu preciso de uma sequência de números (não uma lista já pronta), uso o `range()`. Ele gera os números sob demanda, sem criar uma lista inteira na memória.

```python
for i in range(5):
    print(i)   # 0, 1, 2, 3, 4
```

O valor final nunca entra na sequência: `range(5)` gera 5 números, de `0` a `4`.

Dá pra definir início, fim e "passo" (incremento):

```python
list(range(5, 10))        # [5, 6, 7, 8, 9]
list(range(0, 10, 3))     # [0, 3, 6, 9]   → pula de 3 em 3
```

**Termo técnico:** um objeto `range` é chamado de **iterável**, ou seja, um objeto que consegue entregar seus itens um de cada vez quando é percorrido, sem precisar guardar tudo de uma vez na memória. Isso economiza espaço, principalmente com sequências grandes.

---

## 4. `break` e `continue`

Dois comandos pra controlar um laço por dentro:

- `break` → interrompe o laço imediatamente, saindo dele por completo
- `continue` → pula pro próximo item do laço, sem executar o restante do bloco atual

```python
for numero in range(2, 10):
    if numero % 2 == 0:
        print(f"Número par: {numero}")
        continue
    print(f"Número ímpar: {numero}")
```

**Explicando de forma simples:** imagina que `continue` é "pula essa volta e vai pra próxima", enquanto `break` é "para tudo agora e sai do laço".

---

## 5. Cláusula `else` em laços

Essa é uma particularidade do Python que não existe na maioria das outras linguagens: `for` e `while` podem ter um bloco `else`, que só executa se o laço terminar **sem** ter sido interrompido por um `break`.

```python
for numero in range(2, 10):
    for divisor in range(2, numero):
        if numero % divisor == 0:
            print(f"{numero} não é primo")
            break
    else:
        print(f"{numero} é primo")
```

**Explicando de forma simples:** o `else` aqui pertence ao `for`, não ao `if` de dentro. Ele funciona como "se eu terminei o laço inteiro sem dar break, executa isso". É útil pra situações de busca, tipo verificar se um número é primo.

---

## 6. Comando `pass`

O `pass` não faz nada. Ele existe só pra preencher um espaço onde o Python exige um bloco de código, mas eu ainda não escrevi a lógica.

```python
def funcao_que_vou_implementar_depois():
    pass   # lembrar de implementar isso
```

**Explicando de forma simples:** é tipo um "placeholder", um espaço reservado. Uso bastante quando tô esboçando a estrutura do código e ainda não decidi o que cada função vai fazer.

---

## 7. Comando `match`

O `match` compara um valor com vários padrões possíveis (parecido com `switch/case` de outras linguagens, mas mais poderoso). Só o primeiro padrão que bater é executado.

```python
def resposta_http(status):
    match status:
        case 400:
            return "Requisição inválida"
        case 404:
            return "Não encontrado"
        case 401 | 403:
            return "Acesso negado"
        case _:
            return "Erro desconhecido"
```

**Explicando de forma simples:** o `_` funciona como um "coringa", ele bate com qualquer valor que não caiu nos casos anteriores (parecido com o `else`). O `match` também consegue "desempacotar" estruturas mais complexas, tipo tuplas e objetos, mas o uso mais comum pra quem tá começando é comparar valores simples.

---

## 8. Definindo funções

Uso a palavra-chave `def` pra criar minhas próprias funções, reaproveitando código em vez de repetir.

```python
def saudacao(nome):
    """Recebe um nome e devolve uma saudação."""
    return f"Olá, {nome}!"

print(saudacao("Jorge"))
```

**Explicando de forma simples:** uma função é um bloco de código com nome, que eu posso "chamar" quantas vezes quiser passando valores diferentes (os argumentos). A primeira linha entre aspas triplas é a **docstring**, um texto que documenta o que a função faz.

**Ponto importante:** toda função em Python devolve algum valor, mesmo quando eu não use `return`. Se eu não retornar nada explicitamente, ela devolve `None` por padrão.

### Argumentos com valor padrão

Posso definir um valor padrão pra um argumento, tornando ele opcional na hora de chamar a função:

```python
def tentar_login(usuario, tentativas=3):
    print(f"Usuário {usuario} tem {tentativas} tentativas")

tentar_login("admin")           # usa o padrão: 3 tentativas
tentar_login("admin", 5)        # sobrescreve o padrão
```

**Cuidado com um detalhe importante:** se o valor padrão for algo mutável (tipo uma lista), ele é criado **uma única vez**, na hora que a função é definida, e não toda vez que ela é chamada. Isso pode causar bugs, porque o mesmo objeto vai sendo reaproveitado entre chamadas diferentes. O jeito seguro é usar `None` como padrão e criar a lista de verdade dentro da função.

### Argumentos nomeados (keyword arguments)

Posso passar argumentos pelo nome, em vez de depender só da posição:

```python
def conexao(host, porta=443, protocolo="https"):
    print(f"Conectando em {host}:{porta} via {protocolo}")

conexao("10.0.0.1", protocolo="http")
```

### `*args` e `**kwargs`

Quando não sei quantos argumentos vou receber, uso `*args` (pra argumentos posicionais extras) e `**kwargs` (pra argumentos nomeados extras).

```python
def escanear_portas(alvo, *portas, **opcoes):
    print(f"Escaneando {alvo} nas portas {portas}")
    for chave, valor in opcoes.items():
        print(f"{chave}: {valor}")

escanear_portas("192.168.0.1", 22, 80, 443, timeout=5, verbose=True)
```

**Explicando de forma simples:** `*portas` junta tudo que sobrar de argumentos posicionais numa tupla. `**opcoes` junta tudo que sobrar de argumentos nomeados num dicionário. É muito usado quando eu quero que a função aceite uma quantidade flexível de parâmetros, como no exemplo de scanner acima.

### Funções lambda

São funções pequenas e sem nome, criadas com a palavra-chave `lambda`, úteis quando preciso de uma função rápida em um único lugar (tipo dentro de um `.sort()`).

```python
dobro = lambda x: x * 2
print(dobro(5))   # 10
```

**Explicando de forma simples:** é uma forma resumida de escrever uma função de uma linha só. Só funciona pra expressões simples, não substitui uma função normal quando a lógica é mais complexa.

---

## 9. Estilo de código (PEP 8)

O tutorial encerra o módulo com uma introdução à **PEP 8**, o guia oficial de estilo de código Python. Alguns pontos principais:

- Usar 4 espaços de indentação (nunca tabulação)
- Linhas com no máximo 79 caracteres
- Linhas em branco pra separar funções e blocos de código
- Nomes de classes em `UpperCamelCase`, nomes de funções e variáveis em `minusculas_com_underscore`
- Usar docstrings pra documentar funções

**Explicando de forma simples:** PEP 8 é basicamente um "manual de boas práticas de escrita" pro código Python. Seguir ele deixa o código mais fácil de ler pra outras pessoas (e pra mim mesmo, no futuro).

---

## Resumo do dia

| Conceito | Ponto-chave |
|---|---|
| `if` / `elif` / `else` | Testa condições em ordem, executa só o primeiro bloco verdadeiro |
| `for` | Percorre itens de qualquer sequência, não só números |
| `range()` | Gera números sob demanda, sem ocupar memória com uma lista inteira |
| `break` / `continue` | Interrompe o laço ou pula pra próxima repetição |
| `else` em laços | Executa só se o laço terminar sem `break` |
| `pass` | Placeholder, não faz nada |
| `match` | Compara um valor com vários padrões possíveis |
| `def` | Cria funções reutilizáveis |
| Valor padrão | Cuidado com objetos mutáveis como padrão |
| `*args` / `**kwargs` | Recebem quantidade flexível de argumentos |
| `lambda` | Função pequena, de uma linha, sem nome |
| PEP 8 | Guia oficial de estilo de código Python |

---

## Glossário

- **Argumento:** valor que eu passo pra uma função na hora de chamá-la.
- **Condição:** expressão que resulta em verdadeiro (`True`) ou falso (`False`), usada pelo `if` pra decidir o que executar.
- **Docstring:** texto de documentação escrito logo no início de uma função, entre aspas triplas.
- **Indentação:** espaços no início da linha que definem quais comandos pertencem a qual bloco de código (o Python usa isso em vez de chaves `{}`).
- **Iterável:** qualquer objeto que pode ser percorrido item por item, como uma lista, string ou o resultado de um `range()`.
- **Laço (loop):** estrutura que repete um bloco de código várias vezes, como o `for` e o `while`.
- **Mutável:** objeto que pode ser alterado depois de criado, como listas e dicionários (o oposto de imutável).
- **Parâmetro:** o "nome" que uma função dá a cada valor que ela espera receber (diferente de argumento, que é o valor em si passado na chamada).
- **Placeholder:** espaço reservado no código que ainda não tem lógica implementada.
- **Symbol table (tabela de símbolos):** estrutura interna do Python que guarda o nome das variáveis e a qual valor elas apontam, dentro de cada escopo.
