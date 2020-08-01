# Sequential and  parallel DIRECT-type implementations

Sequential and parallel DIRECT-type algorithms for box and generally constrained global optimization problems

The code in this repository is based on the works in [[1]](#1)[[2]](#2)[[3]](#3)[[4]](#4)[[5]](#5)[[6]](#6)[[7]](#7)  and is written in MATLAB.

## Getting started

- Download the entire folder containing all MATLAB files and add the entire folder and subfolders to the MATLAB path. 
- Next run sequential codes `dDirect_GL`,`dDirect_G` and `dDirect_L` based on dynamic data structures [[3]](#3), which should run the pre-defined problem as defined in [[4]](#4).
- Next run sequential codes `sDirect_GL`,`sDirect_G` and `sDirect_L` based on static data structures [[2]](#2), which should run the pre-defined problem as defined in [[4]](#4).
- Next run sequential codes `dDirect_GLce`, `dDirect_GLc` and `dDirect_GLce_min` based on dynamic data structures [[3]](#3), which should run the pre-defined problem as defined in [[5]](#5).
- Next run sequential codes `sDirect_GLce`, `sDirect_GLc` and `sDirect_GLce_min` based on static data structures [[2]](#2), which should run the pre-defined problem as defined in [[5]](#5).
- Next run sequential codes `dDirect_GLh` based on dynamic data structures [[3]](#3), which should run the pre-defined problem as defined in [[5]](#5)[[7]](#7).
- Next run sequential codes `dDirect_GLh` based on static data structures [[2]](#2), which should run the pre-defined problem as defined in [[5]](#5)[[7]](#7).
- Next run parallel codes `parallel_dDirect_GL`,`parallel_dDirect_G` and  `parallel_dDirect_L` based on dynamic data structures [[3]](#3), which should run the pre-defined problem as defined in [[4]](#4).
- Next run parallel codes `parallel_dDirect_GLce`, `parallel_dDirect_GLc`  and  `parallel_dDirect_GLce_min`  based on dynamic data structures [[3]](#3), which should run the pre-defined problem as defined in [[4]](#4).

## References

[1] C. A. Baker, L. T. Watson, B. Grossman, W. H. Mason, R. T. Haftka, [Parallel global aircraft configuration design space exploration, in: A. Tentner (Ed.)](https://www.semanticscholar.org/paper/Parallel-Global-Aircraft-Configuration-Design-Space-Baker-Watson/2ca51b579b927476a21a4a751ef2ca8792f8944a), High Performance Computing Symposium 2000, Soc. for Computer Simulation Internat, 2000, pp. 54–66. <a name="1">
</a>

[2] D. E. Finkel, MATLAB source code for DIRECT, \url{http://www4.ncsu.edu/~ctk/Finkel_Direct/}, online; accessed: 2017-03-22 (2004).

[3] J. He, L. T. Watson, N. Ramakrishnan, C. A. Shaffer, A. Verstak, J. Jiang, K. Bae, W. H. Tranter, [Dynamic data structures for a DIRECT search algorithm](https://link.springer.com/article/10.1023/A:1019992822938), Computational Optimization and Applications 23 (1) (2002) 5–25. 

[4] L. Stripinis, R. Paulavičius, J. Žilinskas, [Improved scheme for selection of potentially optimal hyper-rectangles in DIRECT](https://link.springer.com/article/10.1007/s11590-017-1228-4), Optimization Letters 12 (7) (2018) 1699–1712. doi:10.1007/ s11590-017-1228-4. <a name="2">
</a>

[5] L. Stripinis, R. Paulavičius, and J. Žilinskas, [Penalty functions and two-step selection procedure based DIRECT-type algorithm for constrained global optimization](http://link.springer.com/10.1007/s00158-018-2181-2), Struct. Multidiscip. Optim., vol. 59, no. 6, pp. 2155–2175, 2019. <a name="3">
</a>

[6] L. Stripinis, J. Žilinskas, L. G. Casado, and R. Paulavičius, *On MATLAB experience in accelerating DIRECT-GLce algorithm for constrained global optimization through dynamic data structures and parallelization*, pp. 1–25. Submitted. <a name="4">
</a>

[7] L. Stripinis, R. Paulavičius, A modified DIRECT-GL algorithm for global optimization with hidden constraints, pp. 1–25. Submitted. <a name="5">
</a>

## Citing those implementations

Please use the following bibtex entry, if you consider to cite those implementations:

```
@misc{Stripinis2020directgl,
  title={Sequential and parallel DIRECT-type algorithms for box and generally constrained global optimization problems in MATLAB},
  author={Stripinis, Linas},
  year={2020},
  publisher = {GitHub},
  journal = {GitHub repository},
  howpublished={\url{https://github.com/LinasStripinis/DIRECT-GL}},
}
```
