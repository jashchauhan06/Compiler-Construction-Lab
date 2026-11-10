# Compiler Construction Lab

| | |
|---|---|
| **Name** | Jash Chauhan |
| **PRN** | 24070521242 |
| **Subject** | Compiler Construction Lab |
| **Tools used** | Lex (Flex), Yacc (Bison), GCC, Vim on Linux |

This repository contains all the experiments I performed for the **Compiler Construction Lab**.
Each experiment folder holds the source code (`.l` / `.y` / `.c`) and a `README.md`
with the terminal session showing how it was compiled and the output it produced.

---

## Experiments

| Exp | Title | Tools | Source files |
|:---:|-------|:-----:|--------------|
| 1 | Number word recognizer (`one` → `1`, case-insensitive) | Lex | `exp1_1242.l` |
| 2 | Lexical analyzer (counts lines, spaces, words, keywords, identifiers, comments) | Lex | `analyzer1242.l`, `input1242.c` |
| 3 | Word matcher: words starting with `a` / `A` (matched vs. not matched count) | Lex | `Exp3_1242.l` |
| 4 | Introduction to the YACC tool and the format of a YACC program (theory) | Yacc | `theory_exp4.txt` |
| 5 | Case toggler (swaps upper/lower case of the input string) | Lex | `case-242.l` |
| 6 | Decimal to hexadecimal converter | Lex | `exp6_242.l` |
| 7 | Checker for strings ending with `com` | Lex | `exp7_1242.l` |
| 8 | Postfix (Reverse Polish) expression evaluator with division-by-zero and syntax-error handling | Lex + Yacc | `postfix242.l`, `postfix242.y` |
| 9 | Desk calculator with `+ - * /`, parentheses, operator precedence and error handling | Lex + Yacc | `cal_1242.l`, `cal_1242.y` |
| 10 | Syntax validator for a C-style `for` loop | Lex + Yacc | `exp10_242.l`, `exp10_242.y` |

---

## Repository structure

```
COMPILER-CONSTRUCTION-LAB/
├── Exp 1/    README.md, exp1_1242.l
├── Exp 2/    README.md, analyzer1242.l, input1242.c
├── Exp 3/    README.md, Exp3_1242.l
├── Exp 4/    README.md, theory_exp4.txt
├── Exp 5/    README.md, case-242.l
├── Exp 6/    README.md, exp6_242.l
├── Exp 7/    README.md, exp7_1242.l
├── Exp 8/    README.md, postfix242.l, postfix242.y
├── Exp 9/    README.md, cal_1242.l, cal_1242.y
└── Exps 10/  README.md, exp10_242.l, exp10_242.y
```

---

## How to build and run

**Lex-only programs (Experiments 1, 2, 3, 5, 6, 7)**

```bash
lex <file>.l
gcc lex.yy.c -ll -o <output>
./<output>
```

**Lex + Yacc programs (Experiments 8, 9, 10)**

```bash
yacc -d <file>.y        # generates y.tab.c and y.tab.h
lex  <file>.l           # generates lex.yy.c
gcc y.tab.c lex.yy.c -o <output> -ll
./<output>
```

Example (Experiment 9):

```bash
yacc -d cal_1242.y
lex cal_1242.l
gcc y.tab.c lex.yy.c -o cal_1242 -ll
./cal_1242
```

> On some systems `flex` / `bison` replace `lex` / `yacc`, and the library flag may be `-lfl` instead of `-ll`.

---

## Sample outputs

**Experiment 8 — Postfix evaluator**
```
5 4 +
Result = 9
12 50 * 95 + 10 2 / -
Result = 690
```

**Experiment 9 — Desk calculator**
```
50*60+2
Result = 3002
12*50+95-10/2
Result = 690
```

**Experiment 10 — For loop validator**
```
for(i=0; i<10; i++)
Valid for loop
```

---

## Submitted by

**Jash Chauhan**
PRN: **24070521242**
Subject: **Compiler Construction Lab**
