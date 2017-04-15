# autgradalg.lib

`autgradalg.lib` is a library for the free computer algebra system [Singular](#http://singular.uni-kl.de) to compute automorphism groups of pointedly graded algebras and of Mori dream spaces.


## Table of contents
* [Introduction](#Introduction)
    * [Summary and references](#summary-and-references)
    * [Assumptions](#assumptions)
* [How to use the library](#Installation-and-usage)
    * [Installation](#installation)
    * [Usage: Examples](#usage:-examples)
    * [Procedures](#procedures)
    * [Testing](#testing)
    * [Logging](#logging)


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
* Try out the lib: Execute `Singular` and then load the library with the commands
    ```C++
    LIB 'gfanlib.so'
    LIB 'autgradalg.lib'
    ```

### Usage: Examples

You can find examples in the folder `examples`.
To run any file, say `FOO.sing`, `cd` to the corresponding directory, and run `Singular FOO.sing` on the command line.
* the folder `examples/paper` lists files to recompute the examples used in the [paper](#http://arxiv.org).
* the folder `examples/fanos` lists the files to verify the results on Fano varieties listed in the Proposition in the [paper](#http://arxiv.org).


### Documentation

The following functions are available from our library:
type `help FUNCTIONNAME;` to see further information.
Again, more information and examples can be found [here](#http://arxiv.org/abs/).


* `autKS()`: compute the automorphism group of the basering (must be a polynomial ring) as an algebraic subgroup `V(I)` of some `GL(n)`.
* `autGradAlg(I0, TOR)`: compute the automorphism group of the algebra `basering/I0` as an algebraic subgroup `V(I)` of some `GL(n)`.
* `autGenWeights(TOR)`: compute the automorphisms of the grading group of the `basering` that fix the generator degrees.
* `stabilizer(I0, TOR)`: compute the stabilizer of the given ideal `I0`.
* `autXhat(I0, w, TOR)`: compute the automorphism group of `\widehat X` as an algebraic subgroup `V(I)` of some `GL(n)`.
* `autX(I0, w, TOR)`: compute the automorphism group of `X=X(R,w)` as an algebraic subgroup `V(I)` of some `GL(n)`.
* `shrink(J)`: returns a new ring  obtained from the old one by removing variables  appearing as generators in `J`.


### Testing


To test all of the previously listed procedures, go to the `test` folder, and execute
```shell
Singular test.sing
```

You can test only one of the previously listed procedures, say `foo`, by starting `Singular`, loading the library and then running 
```C++
example foo;
```

### Logging

You can increase the loglevel with
```C++
printlevel = 2;
```

