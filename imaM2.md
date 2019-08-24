Sage/Macaulay2 interfaces and interactions
==========================================
**IMA Coding Sprint Proposal by**

* [Anton Leykin](mailto:leykin@math.gatech.edu) Georgia Tech

* [Dmitrii Pasechnik](mailto:dimpase@cs.ox.ac.uk) University of Oxford, UK

* [Franco Saliola](mailto:saliola.franco@uqam.ca) Université du Québec à Montréal, Canada

* [Markus Wageringel](mailto:markus.wageringel@uni-osnabrueck.de) Universität Osnabrück, Germany

Basic commutative algebra computations in Sage are presently done (mostly)
using the (lib)Singular. There is considerable interest in bringing into Sage
commutative algebra capabilities, such as homological algebra computations,
numerical algebraic geometry, of Macaulay2 (M2, for short) which are otherwise not available.
The most natural approach would be to create a possibility to use M2 as
an alternative commutative algebra backend in Sage.
This task is tracked on [Sage's #28284](https://trac.sagemath.org/ticket/28284). 

A related task is to facilitate installation of M2 via Sage (more precisely,
*Sage the distribution*, as opposed to *Sage a Python library*).
This is becoming feasible with [M2 eigen branch](https://github.com/antonleykin/M2/tree/eigen),
which removes the need to patch
many needed libraries for compatibility with Boehm GC. (It used to be possible to install M2 in Sage
[many years ago](https://trac.sagemath.org/ticket/11710)).
This task is tracked on [Sage's #28255](https://trac.sagemath.org/ticket/28255).

The purpose of the proposed coding sprint is to make progress on #28284, and, time/resources
allowing, on #28255, as well as on the "dual" task of interfacing Sage from M2.
As a side task it might be useful to leverage the experience of D.Pasechnik on [unvendoring
Sage components](https://trac.sagemath.org/ticket/27330) in the realm of M2, to streamline its
installation.

M2's commutative algebra in Sage
--------------------------------

Currently Sage has a capability to interface with M2 and convert few basic data types, such as
multivariate polynomials, back and force. However, much more is needed.


* Use M2's *betti* and friends command in Sage. This prompts the task of interfacing
[M2's ChainComplex](https://faculty.math.illinois.edu/Macaulay2/doc/Macaulay2-1.14/share/doc/Macaulay2/Macaulay2Doc/html/_chain__Complex.html) with
[Sage's ChainComplex](http://doc.sagemath.org/html/en/reference/homology/sage/homology/chain_complex.html)

* Sage's commutative algebra support lacks a concept of backends. They need to be specified and implemented,
so that e.g. it's possible to interchangeably use libSingular and M2 Groebner bases engines for basic
computations.

* Interface between Sage's and M2's quotient rings.

* Numerical algebraic geometry support is hardly existing in Sage. It would be great to explore the possibilities to
have it in Sage in a face-to-face meeting with a primary developer of this functionality in M2, A.Leykin.

Working with Sage in M2 
-----------------------

Currently Sage can't be accessed from an M2 session.

* A rudimentary python interface exists in M2. This requires compiling M2 with
  optional flags which was functional in some release, but doesn't work in
1.14 version. 

* We need to discuss possible ways to invoke Sage in M2.  

* Sage-specific python interface is a possibility: one may envision converters from main Sage types to those of M2. 

