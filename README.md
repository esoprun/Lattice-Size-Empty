# Lattice-Size-Empty

This is MAGMA code accompanying paper [1] "Lattice Size of Width One Lattice Polytopes in R^3" by Alajmi and Soprunova.

Here we implement the Basis Reduction Algorithm described in [2] "Lattice Size and Generalized Basis Reduction in Dimension 3"
by Harrison and Soprunova as well as the Brute Force Algorithm for computing the lattice size, described in the Introduction of [1].

We then run experiments to find a counterexample demonstrating that there exists a  lattice polytope P in R^3 of lattice width 1 such that there is no Minkowski reduced basis that computes its lattice size. See Example 5.1 in [1].

Functions:

Barycenter(P) Finds the barycenter of a lattice polytope P in R^3

InRadius(P)  Finds the radius of the sphere inscribed in 3D lattice polytope P and centered at the barycenter of P

MakeP(P0,P1) Creates a 3D Polytope P which is a convex hull of polygons P0 and P1 placed at the levels x=0 and x=1

BruteForceOriginal(P) Computes the lattice size of P subset R^3 using the Brute Force Algorithm described in the
Introduction to [1]

L1(P) Given a lattice polytope P in R^3, computes L1(P)=max(x+y+z)-min(x)-min(y)-min(z), where all the 
extrema are computed over (x,y,z) in P

OrderVectors(P,h1,h,2,h3) For a lattice polytope P in R^3 and lattice vectors h1, h2, h3, orders the vectors  so that Width(P,h1)<=Width(P,h2)<=Width(P,h3)

GeneralizedNLS(P)  Starts with a 3D lattice width one polytope P,  which is a convex hull of two polygons in the planes x=0 and x=1.
Applies to P each of the eight matrices M with \pm 1 in  each of the diagonal
entries. Then for each of the obtained Q, shifts its layers in x=0 and x=1 so that both  of them are in the positive orthants in these planes and touch the coordinates axes. For each such M, computes L1(Q) for the shifted Q. Find the minimum of L1. Return l=L1(Q) and matrix M*B such that Q=P*M*B and L1(Q)=L1(P*M*B).  See the definition of nls(P) in [1].

BasisReduction2D(P) Finds a reduced basis wrt a 3D lattice polytope P in the (e1,e2)-plane. Takes in a polytope P with Width(e1,P)<=Width(e2,P)<=Width(e3,P) and reduces basis (e1,e2).

BasisReductionStep2D(P) Given a 3D lattice polytope P with |e_1|<=|e2|<=|e_3|, this function provides an iteration in reducing (e1,e2).

BasisReduction3D(P) Finds a basis which is Minkowski reduced wrt given lattice polytope P in R^3.  
This is based on Algorithm 3.11 from [2].

BasisReductionStep3D(P) Provides a step in basis reduction wrt 3D lattice polytope P. This step is based on Proposition 2.7 and Theorem 2.8 from [2].

ComputeLSReduction(P0,P1) This function computes an approximation of the lattice size of 3D lattice polytope P with w(P)=1 using basis reduction.
P is the convex hull of two polygons: P0 at the level x=0 and P1 at the level x=1.

BruteForceLS(P) Uses the Brute Force Algorithm in combination with Basis 
Reduction from [2] to compute the lattice size of a lattice polytope P in R^3.

CheckReducedBruteForce(P) Checks for Example 5.1 in  [1] that there is no reduced basis that computes the lattice size of
P=Polytope([[0,2,5],[0,-2,5],[0,1,-6],[1,-8,5],[1,2,-5],[1,-4,-3]]).

Experiment1a(n), Experiment1b(n), Experiment1c(n)  Here we look at how fast the Brute Force Algorithm performs on random
polytopes P subset 3D compared to such P with w(P)=1 and then on empty lattice tetrahedra P.

Experiment2a(n) Computes the lattice size of a random empty lattice polytope P in R^3 using
BruteForceOriginal algorithm and Algorithm 3.2 from [1]. The goal is to compare the running time of the two algorithms.

Experiment2b(n) Computes the lattice size of a random empty lattice polytope P in R^3 using
Algorithm 3.2 from [1]

Experiment3a(n), Experiment3b(n) Computes the lattice size of a random lattice width one P using BruteForceLS and also its approximation using Basis Reduction and checks if the two answers match.

Experiment4(n) Computes the lattice size computation using BruteForceOriginal and BruteForceLS. The goal is to compare the running time of the two.
