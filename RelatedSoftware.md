# Linear Solvers #
Linear solvers of A\*x=b, where A is symmetric positive semi-definite, large, sparse.

  * [pyamg](http://code.google.com/p/pyamg/) - algebraic multigrid solvers in python. Nathan Bell, Luke Olson, Jacob Schroder. python.
  * [AGMG](http://homepages.ulb.ac.be/~ynotay/AGMG/) - iterative solution with AGgregation-based algebraic Multi Grid. Y. Notay, A. Napov. Fortran, MATLAB.
  * [MATLAB's backslash operator](http://www.mathworks.com/help/techdoc/ref/mldivide.html).  Mathworks. Proprietary. MATLAB.
  * [Hypre](http://acts.nersc.gov/hypre/). Library for solving large, sparse linear systems of equations on massively parallel computers. Livermore National Lab. Open Source. Fortran, C.
  * [EpetraExt-Petsc](http://trilinos.sandia.gov/packages/docs/dev/packages/epetraext/doc/html/epetraext_petsc_interface.html). Sandia National Labs. Open-source. C++.
  * [SparSol](http://www.sparsol.com). Neurok Software company. Neurok Software has a legal right to license this code. C++, Fortran.

# Eigensolvers #
Eigensolvers of A\*x=lam\*B\*x where A is symmetric positive semi-definite and B is symmetric positive definite. A,B large, sparse. Find the K largest or smallest eigenpairs.

  * [MATLAB's eigs](http://www.mathworks.com/help/techdoc/ref/eigs.html). Mathworks. Proprietary. MATLAB.
  * [LOBPCG ](http://www.mathworks.com/matlabcentral/fileexchange/48-lobpcg-m). Locally Optimal Block Preconditioned Conjugate Gradient Method (LOBPCG). Andrew Knyazev. Open source. MATLAB.
  * [FILTRAN ](http://www-users.cs.umn.edu/~saad/software/filtlan/index.html). Software library written in C/C++ for computing extreme or interior eigenvalues of a symmetric matrix by a polynomial filtered Lanczos procedure. Haw-ren Fang and Yousef Saad. C++; mex files for  MATLAB and OCTAVE.