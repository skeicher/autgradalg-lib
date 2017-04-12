# autgradalg.lib

`autgradalg.lib` is a library for the free computer algebra system [Singular](#http://singular.uni-kl.de) to compute automorphism groups of pointedly graded algebras and of Mori dream spaces.


## Table of contents
* [Introduction](#Introduction)
    * [Summary and references](#summary-and-references)
    * [Assumptions](#assumptions)
* [How to use the library](#Installation-and-usage)
    * [Installation](#installation)
    * [Usage: Example](#usage:-example)
    * [Documentation](#documentation)
    * [Testing](#testing)

## Introduction

### Summary and references

`autgradalg.lib` provides a framework for computing automorphisms of integral, finitely generated algebras `R` that are graded by a finitely generated abelian group. This library also contains functions to compute automorphism groups of Mori dream spaces. The results are ideals `I` such that the respective automorphism group is isomorphic to the subgroup `V(I)` in some `GL(n)`. 

The methods can be used to compute symmetries of homogeneous ideals.

 `autgradalg.lib` and the necessary background have been described [in this paper](#http://arxiv.org/abs/).
 It is an implementation of the algorithms developed in  [Computing automorphisms of Mori dream spaces](#http://arxiv.org/abs)


### Assumptions
Please refer to [the detailed description](#http://arxiv.org/abs/) for the full list of assumptions. 
They include

* `R` is given as factor algebra `S/I0` with a graded polynomial ring `S` over the rationals.
* `R` must be *minimally presented*, i.e., I is contained in `<T_1,...,T_r>^2`.
* the grading is *pointed*, i.e., no generator has degree `0` and the cone over all generator degrees is pointed.
* For all `1 <= i <= r` the homogeneous component `I_{w_i}` is trivial where `w_i` is the degree of the i-th generator of `R`.
* For Mori dream spaces `X`, we assume them to be given as `X = X(R,w)` with the Cox ring `R` of `X` and the free part of an ample class `w`.


## How to use the library

### Installation

* You need to have [Singular](#http://singular.uni-kl.de) installed. The library has been developed for version 4.0.2. We assume it has been installed it on a UNIX machine and is available from the command line.
* Either
    * download the file `lib/autgradalg.lib` and `cd` to the folder containing it 
    * or clone this repository and `cd` to the `lib` folder.
* Try out the lib by running the following [example](#usage:-example).

### Usage: Example

Execute `Singular` and then load the library with the commands
```C++
LIB 'gfanlib.so'
LIB 'autgradalg.lib'
```


### Documentation

#### Procedures: Overview

* `autKS()`: compute the automorphism group of the basering (must be a polynomial ring) as an algebraic subgroup V(I) of some GL(n)
* `autGradAlg(I0, TOR)`: compute the automorphism group of R as an algebraic subgroup V(I) of some GL(n).
* `autGeneratorWeights(TOR)`: compute the automorphisms of the grading group that fix the generator degrees.
* `stabilizer(I0, TOR)`: compute the stabilizer of the given ideal
* `autXhat(I0, w)`: compute the automorphism group of \widehat X as an algebraic subgroup V(I) of some GL(n).
* `autX(I0, w)`: compute the automorphism group of X=X(R,w) as an algebraic subgroup V(I) of some GL(n).

#### Full Documentation

The full documentation including examples is available in the folder `doc`.

### Testing
