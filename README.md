# Clasificación de Problemas Computacionales (Teoría de Complejidad)

La idea central es: **¿cuántos recursos (tiempo, memoria) necesita un algoritmo para resolver un problema a medida que la entrada crece?**

---

## La jerarquía de clases

### **P** — Problemas "fáciles"
Son los problemas que se pueden **resolver** en tiempo polinomial, es decir, en O(nᵏ) pasos para alguna constante k.

Ejemplos:
- Ordenar una lista (O(n log n))
- Buscar el camino más corto en un grafo (Dijkstra)
- Multiplicar dos matrices

Si un problema está en P, en la práctica lo consideramos *tratable* — con una computadora normal puedes resolverlo aunque la entrada sea grande.

---

### **NP** — Problemas cuya solución es fácil de *verificar*
NP significa **Non-deterministic Polynomial**. Un problema está en NP si:
- Dada una solución candidata, puedes **verificar si es correcta** en tiempo polinomial.
- No necesariamente puedes *encontrar* esa solución rápido.

Ejemplo clásico — **Sudoku:**
- Resolver un Sudoku gigante puede ser muy difícil.
- Pero si alguien te da un tablero ya lleno, verificar si es correcto es trivial.

> **P ⊆ NP** siempre — si puedes *resolver* algo rápido, también puedes *verificarlo* rápido. La pregunta del millón es: **¿P = NP?** Nadie lo sabe. Es el problema abierto más famoso de las matemáticas. Se sospecha que no son iguales, pero no está demostrado.

---

### **NP-Completo** — Lo más difícil dentro de NP
Un problema es NP-Completo si cumple **dos cosas**:

1. Está en NP (su solución es verificable rápidamente).
2. **Todo** problema en NP se puede reducir a él en tiempo polinomial — es decir, es "tan difícil como cualquier problema en NP".

La intuición: si encontraras un algoritmo rápido para *cualquier* problema NP-Completo, automáticamente resolverías **todos** los problemas en NP. Eso probaría que P = NP.

Ejemplos famosos:
- **SAT** (satisfacibilidad booleana) — el primero demostrado NP-Completo (Cook, 1971)
- **Problema del viajante (TSP)** — encontrar el recorrido más corto que visita todas las ciudades
- **Mochila (Knapsack)** — qué objetos meter en una mochila para maximizar el valor sin exceder el peso
- **Coloración de grafos** — ¿puedes colorear un mapa con k colores sin que dos regiones vecinas tengan el mismo color?

---

### **NP-Hard** — Igual de difícil o más, pero sin restricción
Un problema es NP-Hard si todos los problemas en NP se reducen a él, **pero no necesariamente está en NP** (su solución puede ni siquiera ser verificable rápidamente).

Ejemplo: **Halting Problem** (determinar si un programa se detiene) — es NP-Hard pero ni siquiera tiene solución algorítmica, es *indecidible*.

La relación:
```
NP-Completo = NP ∩ NP-Hard
```

---

### **Co-NP** — El complemento de NP
Son problemas donde puedes verificar rápidamente que algo **no** es solución. Formalmente, el complemento del problema está en NP.

Ejemplo: demostrar que un número **no** es primo de cierta forma. (Aunque la primalidad en sí está en P.)

---

### **PSPACE** — Lo que cabe en memoria polinomial
Problemas resolubles usando cantidad polinomial de **memoria**, sin importar cuánto tiempo tome. Contiene a NP y Co-NP.

Ejemplo: juegos de dos jugadores con información perfecta (como ajedrez en tableros generalizados).

---

### **EXP** — Tiempo exponencial
Problemas que requieren tiempo O(2^n) o peor. La mayoría de los juegos de tablero generalizados viven aquí.

---

## El mapa completo

```
P ⊆ NP ⊆ PSPACE ⊆ EXP
         ↑
    NP-Completo está
    en la "frontera" de NP
```

---

## ¿Por qué importa?

Porque en la práctica, cuando te enfrentas a un problema NP-Completo:

- **No busques** un algoritmo exacto y rápido para casos grandes — probablemente no existe.
- En su lugar usas: **heurísticas**, **algoritmos de aproximación**, o explotas **estructura especial** del problema (entradas pequeñas, casos restringidos, etc.).

Reconocer que tu problema es NP-Completo te ahorra años de buscar un algoritmo "perfecto" que quizás no existe.
