<p align='center'>
<img src='http://lamg.googlecode.com/files/lamg_ico.png' align='middle' alt='Logo' width='45%' />
</p>

Lean Algebraic Multigrid (LAMG) is a fast numerical algorithm for solving the linear system Ax=b, where A is a graph Laplacian matrix. LAMG's run time and storage are **linear in the number of graph edges**. LAMG now also supports symmetric diagonally-dominant (SDD) matrices with non-zero-row sums (by reducing them to a Laplacian system internally).

LAMG is developed by [Oren Livne](http://oren.multigridguide.net) (The University of Chicago) and [Achi Brandt](http://www.wisdom.weizmann.ac.il/~achi/) (The Weizmann Institute of Science). The LAMG MATLAB software was written by [Oren Livne](http://oren.multigridguide.net).

  * Download latest stable release: [LAMG 2.2.1](http://lamg.googlecode.com/files/lamg-2.2.1.zip) (supports connected graphs and SDD systems)

  * [Installation](Installation.md) Instructions of the MATLAB code
  * [Usage Example](UsageExample.md)
  * ArXiV papers describing the LAMG algorithm: [a short version](http://arxiv.org/abs/1108.1310) and [a long version](http://arxiv.org/abs/1108.0123).

---

# Links #
  * [Why are Laplacian Matrices important?](Applications.md)
  * [Publications. Citing LAMG](Publications.md)
  * [Downloading and Installing the Code](Installation.md)
  * [Usage Example](UsageExample.md)
  * [Viewing the Level Hierarchy](LevelHierarchy.md)
  * [Downloading and installing our graph collection](TestInstances.md)
  * [Performance](Performance.md)
  * [Related Software Packages](RelatedSoftware.md)

---

# Need Help? #
  * Email questions and comments to our [lamg-user Google Group](http://groups.google.com/group/lamg-user) website. Or email it directly: [lamg-user@googlegroups.com](mailto:lamg-solver@googlegroups.com)
  * Refer to the [usage example](#usage.md).
  * We currently only have a small part-time funding for this project, so documentation is scarce and is mostly in line with the MATLAB code. Please join this project as a committer and help us improve the documentation!