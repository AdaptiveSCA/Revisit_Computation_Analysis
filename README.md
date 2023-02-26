# Revisit Computation Analysis

This repository contains the supporting code for the experiment of computation analysis on different internal encodings.

The attack results are recorded in "xxx_distinguisher.txt".

## Notes
- ADCA is a higher-degree computation analysis. The attack degree of ADCA can be modified by the param 'attack_degree' of the ADCA funcion in 'ENCA.c' file.
- ADCA also supports to sum the results of different attack degrees for maximizing the probability of the correct key guess.

## Update Infos
1. Fixed the following errors when building in Linux:
 - Multiple definition of "randseed".
 - Undifened references to "sqrt" (Library - <math.h>).

2. Added the new experiment of different computation analyses on internal encodings with algebraic degrees from 1 to 7.

## New Results (Updating)

1. Different attacks against internal encodings with ***degree 1 to 7*** are illustrated as follows. Each attack case is executed over 1,000 times on randomly generated encodings.

| Attack/Degree   | 1    | 2    | 3    | 4    | 5    | 6    |7    |
| :----: | :----: | :----: | :----: | :----: | :----: | :----: | :----: |
| DCA    | 222    | 842    | 544    | 505    | 583    | 186    | 4      |
| IDCA   | 1000   | 1000   | 958    | 905    | 1000   | 518    | 1      |
| CPA    | 229    | 843    | 527    | 487    | 571    | 168    | 5      |
| CA     | 229    | 843    | 527    | 487    | 571    | 168    | 5      |
| MIA    | 229    | 843    | 527    | 487    | 571    | 168    | 5      |
| BCA    | 230    | 55     | 1      | 16     | 15     | 10     | 0      |
| SA     | 1000   | 1000   | 1000   | 1000   | 1000   | 1000   | 4      |
| MSA    | 1000   | 940    | 742    | 757    | 878    | 441    | 4      |
| ISA    | 1000   | 1000   | 1000   | 1000   | 1000   | 1000   | 4      |
| ADCA   | 1000   | 1000   | 1000   | 1000   | 1000   | 1000   | 4      |

2. The following table depicts the ***more precisely*** computed time complexity of ADCA. The time complexity is computed by $N\times p\times T\times k$, where $p$ is the number of the degree $d$ closure. Thus, the time complexity of ADCA is related to the degree value.

| Degree | Complexity |
| :----: | :----:     |
| 1      | $2^{22.2}$ |
| 2      | $2^{24.2}$ |
| 3      | $2^{25.5}$ |
| 4      | $2^{24.2}$ |
| 5      | $2^{26.3}$ |
| 6      | $2^{26.8}$ |
| 7      | $2^{26.9}$ |

## Build

```
$ mkdir build
$ cd build
$ cmake ..
$ make
```

## Run

```
$ ./ENCA
```
