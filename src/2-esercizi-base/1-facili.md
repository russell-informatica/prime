---
layout: cover
---

# Esercizi Python
per iniziare

<div class="pt-12">
  <span class="px-2 py-1 rounded bg-primary text-[#141418]">Informatica 2c</span>
</div>

---

# Regole di sintassi

Negli esercizi valgono queste regole:

- Niente "zucchero sintattico": scrivi `i = i + 1`, non `i += 1`.
- Niente funzioni o metodi integrati avanzati: no `sum()`, `max()`, `min()`, `.count()`, `.index()`, né l'operatore `in`.
- I cicli solo con `for i in range(...)` oppure con `while`.
- Accesso agli elementi della lista **solo tramite indice**: `lista[i]`.

> **N.B.** Lo scopo è allenarsi a costruire la logica passo passo, non a trovare la scorciatoia.

---
layout: two-cols-header
class: table-sm
---

# Esercizio 1 — Voto sufficiente o insufficiente

Inizializza una variabile intera `voto`. Stampa:

- `Sufficiente` se il voto è maggiore o uguale a `6`;
- `Insufficiente` se il voto è minore di `6`;
- `Errore` se il voto **non** è nel range consentito `0`–`10`.

::left::

| Input | Output         |
| ----- | -------------- |
| `7`   | `Sufficiente`  |
| `4`   | `Insufficiente`|
| `12`  | `Errore`       |

::right::

> **Nota** Controlla prima il caso di errore usando `or`: `voto < 0 or voto > 10`.

---

# Esercizio 1 — Soluzione

```python
voto = 7

if voto < 0 or voto > 10:
    print("Errore")
elif voto >= 6:
    print("Sufficiente")
else:
    print("Insufficiente")
```

> **Nota** L'`elif` viene controllato solo se il primo `if` è falso: l'ordine dei controlli conta.

---
layout: two-cols-header
class: table-sm
---

# Esercizio 2 — Primo, ultimo e centrale

Data una lista, crea una **nuova lista** che contenga il primo elemento, l'ultimo elemento e l'elemento centrale della lista di partenza. Stampa la nuova lista.

::left::

| Input                   | Output           |
| ----------------------- | ---------------- |
| `[10, 20, 30, 40, 50]`  | `[10, 50, 30]`   |

::right::

> **Nota** L'ultimo indice è `len(lista) - 1`, l'indice centrale è `len(lista) // 2`.

---

# Esercizio 2 — Soluzione

```python
lista = [10, 20, 30, 40, 50]

centrale = len(lista) // 2

nuova_lista = []
nuova_lista.append(lista[0])
nuova_lista.append(lista[len(lista) - 1])
nuova_lista.append(lista[centrale])

print(nuova_lista)
```

---
layout: two-cols-header
class: table-sm
---

# Esercizio 3 — Conta da `0` a `n - 1`

Dato un intero `n`, stampa i numeri da `0` a `n - 1`, uno per riga. Usa **solo** un ciclo `while`.

::left::

| Input | Output                                     |
| ----- | ------------------------------------------ |
| `5`   | `0`<br>`1`<br>`2`<br>`3`<br>`4`            |

::right::

> **Nota** Non dimenticare `i = i + 1`, altrimenti il ciclo non termina mai.

---

# Esercizio 3 — Soluzione

```python
n = 5

i = 0
while i < n:
    print(i)
    i = i + 1
```

---
layout: two-cols-header
class: table-sm
---

# Esercizio 4 — Conta da `n - 1` a `0`

Dato un intero `n`, stampa i numeri da `n - 1` a `0`, uno per riga. Usa **solo** un ciclo `while`.

::left::

| Input | Output                                      |
| ----- | ------------------------------------------- |
| `5`   | `4`<br>`3`<br>`2`<br>`1`<br>`0`             |

::right::

> **Nota** Parti da `n - 1` e continua finché `i >= 0`, decrementando `i`.

---

# Esercizio 4 — Soluzione

```python
n = 5

i = n - 1
while i >= 0:
    print(i)
    i = i - 1
```

---
layout: two-cols-header
class: table-sm
---

# Esercizio 5 — Una lista, un elemento per riga

Data una lista con un numero arbitrario di elementi, stampala mettendo ogni elemento su una riga diversa.

::left::

| Input              | Output                                     |
| ------------------ | ------------------------------------------ |
| `[2, 4, 6, 8, 10]` | `2`<br>`4`<br>`6`<br>`8`<br>`10`           |

::right::

> **Nota** Usa `range(len(lista))` e accedi con l'indice `lista[i]`.

---

# Esercizio 5 — Soluzione

```python
lista = [2, 4, 6, 8, 10]

for i in range(len(lista)):
    print(lista[i])
```

---
layout: two-cols-header
class: table-sm
---

# Esercizio 6 — Lista al contrario

Data una lista di interi, stampala in ordine invertito, dall'ultimo elemento al primo.

::left::

| Input            | Output                                     |
| ---------------- | ------------------------------------------ |
| `[1, 2, 3, 4, 5]`| `5`<br>`4`<br>`3`<br>`2`<br>`1`            |

::right::

> **Nota** Parti dall'ultimo indice `len(lista) - 1` e vai a ritroso fino a `0`.

---

# Esercizio 6 — Soluzione

```python
lista = [1, 2, 3, 4, 5]

i = len(lista) - 1
while i >= 0:
    print(lista[i])
    i = i - 1
```

---
layout: two-cols-header
class: table-sm
---

# Esercizio 7 — Cerca un numero

Data una lista di interi e un numero `x`, cerca `x` nella lista. Se è presente almeno una volta stampa `{x} è contenuto nella lista`, altrimenti stampa `{x} non è contenuto nella lista`.

::left::

| Input                      | Output                          |
| -------------------------- | ------------------------------- |
| `[4, 8, 15, 16]` e `x = 15`| `15 è contenuto nella lista`    |
| `[1, 2, 3]` e `x = 7`      | `7 non è contenuto nella lista` |

::right::

> **Nota** Senza usare l'operatore `in`. Usa una variabile booleana `trovato`.

---

# Esercizio 7 — Soluzione

```python
lista = [4, 8, 15, 16]
x = 15

trovato = False
for i in range(len(lista)):
    if lista[i] == x:
        trovato = True

if trovato == True:
    print(x, "è contenuto nella lista")
else:
    print(x, "non è contenuto nella lista")
```

---
layout: two-cols-header
class: table-sm
---

# Esercizio 8 — Conta le occorrenze

Data una lista di interi e un numero `x`, conta quante volte `x` compare nella lista e stampa il risultato.

::left::

| Input                        | Output |
| ---------------------------- | ------ |
| `[5, 10, 15, 10, 20, 10]` e `x = 10` | `3` |

::right::

> **Nota** Senza usare `.count()`. Incrementa un contatore quando l'elemento è uguale a `x`.

---

# Esercizio 8 — Soluzione

```python
lista = [5, 10, 15, 10, 20, 10]
x = 10

conta = 0
for i in range(len(lista)):
    if lista[i] == x:
        conta = conta + 1
print(conta)
```

---
layout: two-cols-header
class: table-sm
---

# Esercizio 9 — Il valore massimo

Data una lista di interi, calcola e stampa il valore massimo presente nella lista.

::left::

| Input            | Output |
| ---------------- | ------ |
| `[3, 7, 2, 9, 5]`| `9`    |

::right::

> **Nota** Senza usare `max()`. Parti dal primo elemento e aggiorna il massimo quando ne trovi uno più grande.

---

# Esercizio 9 — Soluzione

```python
lista = [3, 7, 2, 9, 5]

massimo = lista[0]
for i in range(len(lista)):
    if lista[i] > massimo:
        massimo = lista[i]
print(massimo)
```

---
layout: two-cols-header
class: table-sm
---

# Esercizio 10 — La lista è crescente?

Data una lista di interi, stampa `la lista è crescente` se ogni elemento è **maggiore o uguale** al precedente, altrimenti stampa `la lista non è crescente`.

::left::

| Input          | Output                    |
| -------------- | ------------------------- |
| `[1, 3, 5, 7]` | `la lista è crescente`    |
| `[1, 3, 2, 7]` | `la lista non è crescente` |

::right::

> **Nota** Confronta ogni elemento `lista[i]` con il precedente `lista[i - 1]`: parti da `i = 1`.

---

# Esercizio 10 — Soluzione

```python
lista = [1, 3, 5, 7]

crescente = True
for i in range(1, len(lista)):
    if lista[i] < lista[i - 1]:
        crescente = False

if crescente == True:
    print("la lista è crescente")
else:
    print("la lista non è crescente")
```

---
layout: two-cols-header
class: table-sm
---

# Esercizio 11 — Conta i numeri pari

Data una lista di interi, conta quanti valori pari contiene e stampa il risultato.

::left::

| Input                | Output |
| -------------------- | ------ |
| `[1, 2, 3, 4, 5, 6]` | `3`    |

::right::

> **Nota** Un numero è pari quando `lista[i] % 2 == 0`.

---

# Esercizio 11 — Soluzione

```python
lista = [1, 2, 3, 4, 5, 6]

conta = 0
for i in range(len(lista)):
    if lista[i] % 2 == 0:
        conta = conta + 1
print(conta)
```
