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

## New Results

1. Different attacks against internal encodings with ***degree 1 to 7*** are illustrated as follows. Each attack case corresponds to the same 1,000 randomly generated encodings. The results depict the number of the passed tests for each attack.

| Attack/Degree   | 1    | 2    | 3    | 4    | 5    | 6    |7    |
| :----: | :----: | :----: | :----: | :----: | :----: | :----: | :----: |
| DCA    | 223    | 827    | 535    | 530    | 579    | 170    | 8      |
| IDCA   | 1000   | 977    | 951    | 925    | 1000   | 478    | 2      |
| CPA    | 223    | 840    | 540    | 521    | 578    | 162    | 7      |
| CA     | 223    | 840    | 540    | 521    | 578    | 162    | 7      |
| MIA    | 223    | 840    | 540    | 521    | 578    | 162    | 7      |
| BCA    | 237    | 70     | 4      | 12     | 15     | 12     | 0      |
| SA     | 1000   | 1000   | 1000   | 1000   | 1000   | 1000   | 3      |
| MSA    | 1000   | 968    | 712    | 786    | 835    | 438    | 1      |
| ISA    | 1000   | 1000   | 1000   | 1000   | 1000   | 1000   | 3      |
| ADCA   | 1000   | 1000   | 1000   | 1000   | 1000   | 1000   | 0      |

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
