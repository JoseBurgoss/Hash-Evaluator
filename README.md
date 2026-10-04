# Hash Function Evaluator

Python scripts that brute-force partial preimages for MD5, SHA-1 and SHA-256 (hashes starting with `0`, `00`, `000`, `0000`) and chart how the search time grows with the prefix length.

Built for the *Cryptography and Network Security* course.

<p align="center">
  <img src="https://github.com/user-attachments/assets/23196ca8-54c4-4a75-a103-676555e247c7" alt="Time vs prefix length for MD5, SHA-1 and SHA-256" width="600">
</p>

## Features

- Partial preimage search: builds messages of the form `jose andres burgos bolivar:N`, increments `N` and hashes each one until the hex digest starts with the target prefix.
- Compares three algorithms from `hashlib`: MD5, SHA-1 and SHA-256.
- Four difficulty levels: prefixes of 1 to 4 hexadecimal zeros.
- Records the matching message, the digest, the number of attempts and the elapsed time, then prints a summary table.
- Separate plotting script that draws time vs. prefix length per algorithm and saves it as a PNG.

## Tech stack

- Python 3 (`hashlib`, `time` from the standard library)
- matplotlib and pandas (only for the chart)

## Getting started

```bash
git clone https://github.com/JoseBurgoss/Hash-Evaluator.git
cd Hash-Evaluator

# 1. Run the evaluation (no extra dependencies)
python hashes.py

# 2. Generate the chart
pip install matplotlib pandas
python gráfica_comparativa.py
```

`hashes.py` prints progress per algorithm and a final table. Output from one run:

```text
Resultados finales:
Algoritmo Prefijo Mensaje                        Intentos   Tiempo (s)
MD5      0000   jose andres burgos bolivar:66995 66995      0.0394
SHA-1    0000   jose andres burgos bolivar:91031 91031      0.0514
SHA-256  0000   jose andres burgos bolivar:97721 97721      0.0571
```

Attempt counts are deterministic for a given base message; times depend on the machine.

`gráfica_comparativa.py` saves `grafica_resultados_jose_burgos.png` and opens the chart window.

> Note: the chart script uses a hardcoded `datos` list with times from an earlier run. To chart your own results, copy the `Tiempo (s)` values printed by `hashes.py` into that list.

## Project structure

```text
Hash-Evaluator/
├── hashes.py                # Brute-force prefix search and results table
└── gráfica_comparativa.py   # Comparison chart (matplotlib + pandas)
```

To try a different input, change `NOMBRE_COMPLETO` or `PREFIXES` at the top of `hashes.py`.

## Español

Scripts en Python que buscan por fuerza bruta mensajes cuyo hash MD5, SHA-1 o SHA-256 empiece con 1 a 4 ceros hexadecimales, midiendo intentos y tiempo. Un segundo script grafica el tiempo según la longitud del prefijo. Proyecto de la materia *Criptografía y Seguridad de Redes*.

---

Author: José Burgos — https://jose-burgos-portfolio.vercel.app · https://www.linkedin.com/in/jose-burgos-/
