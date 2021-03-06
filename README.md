Berenger Bramas - Inria - berenger.bramas@inria.fr

## AVX-512 sort functions

This project is a small library that provides fast functions to sort arrays of int or double or int[2] using AVX-512.
A paper describes the different strategies and has been published in International Journal of Advanced Computer Science and Applications(IJACSA), Volume 8 Issue 10, 2017
http://thesai.org/Publications/ViewPaper?Volume=8&Issue=10&Code=IJACSA&SerialNo=44
and a draft is also available here https://arxiv.org/abs/1704.08579 for the KNL (older report).
If you use this software, we would appreciate that you cite the related IJACSA paper.


The branch `paper` contains some not very clean files that were used for benchmarks,
wherease the current master branch provides an header only library:
- sort512.hpp : the library that can be directly included in any code to sort integer or double
- sort512kv.hpp : the library that can be directly included in any code to sort key/value pairs of integers
- sort512test.cpp : some unit tests (can be used for examples)

Note that the official repository is https://gitlab.inria.fr/bramas/avx-512-sort

##  Functions
- Sort512::Sort(); to sort an array
- Sort512::SortOmp(); to sort in parallel (need openmp)
- Sort512::Partition512(); to partition
- Sort512::SmallSort16V(); to sort a small array (should be less than 16 AVX512 vectors)


## AVX 512 compilation flags (KNL)
- Gcc : -mavx512f -mavx512pf -mavx512er -mavx512cd
- Intel : -xCOMMON-AVX512 -xMIC-AVX512

## AVX 512 compilation flags (SKL)
- Gcc : -mavx512f -mavx512cd -mavx512vl -mavx512bw -mavx512dq
- Intel : -xCOMMON-AVX512 -xCORE-AVX512

## ARCH compilation flags

Use "-march=native -mtune=native" if you are already on the right platform ("native can be replaced by "knl" or "skylake")

## OpenMP compilation flags
In case you want to use the parallel sort, you need to add the flag:
- Gcc :  -fopenmp
- Intel :  -qopenmp

## Using Intel SDE

Anyone can test the code without having a KNL by using the Intel SDE

## Knowing more about the number of instructions

Please checkout the branch "feature/counters" to have access to counters.
