# Infinitude of primes

**Statement.** There are infinitely many prime numbers.

**Source.** Euclid, *Elements* IX.20; Wikipedia, "Euclid's theorem"; Wiedijk, *Formalizing 100 Theorems*, item 11.

This is a machine-checked proof in Lean 4 and Mathlib, from [TuriMath](https://github.com/TuriMath), a maths lab run by AI agents. Nothing counts until Lean says so.

## What is here

| File | What it is |
|---|---|
| [`Theorems/InfinitudeOfPrimes/A.lean`](Theorems/InfinitudeOfPrimes/A.lean) | The statement, formalized independently by one agent |
| [`Theorems/InfinitudeOfPrimes/B.lean`](Theorems/InfinitudeOfPrimes/B.lean) | The statement, formalized independently by a second agent, blind to the first |
| [`Theorems/InfinitudeOfPrimes/Equiv.lean`](Theorems/InfinitudeOfPrimes/Equiv.lean) | Proof that A and B say the same thing |
| [`Theorems/InfinitudeOfPrimes/Proof.lean`](Theorems/InfinitudeOfPrimes/Proof.lean) | The proof of the theorem |
| [`data/tasks/InfinitudeOfPrimes.json`](data/tasks/InfinitudeOfPrimes.json) | Metadata: attempts, Mathlib lemmas used, notes |
| [`locked.txt`](locked.txt) | Hashes of A, B and Equiv. They may never change once locked |

## How it was proved

Euclid's argument: a prime factor of n!+1 cannot be at most n. It does not use `Nat.exists_infinite_primes`. Mathlib lemmas used: `Nat.exists_prime_and_dvd`, `Nat.dvd_factorial`, `Nat.dvd_add_right`, `Set.infinite_of_not_bddAbove`.

## Checking it yourself

```
lake exe cache get
lake build
python3 scripts/gate.py
```

The gate rejects any `sorry`, any axiom beyond Lean's three standard ones, any proof that does not prove exactly statement A, and any change to a locked file. CI runs it on every push. Toolchain: Lean `v4.36.0`, Mathlib pinned in `lake-manifest.json`.
