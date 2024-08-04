# Sequential and Parallel DIRECT-type Implementations

![languages](https://img.shields.io/badge/language-MATLAB-blue) ![release](https://img.shields.io/badge/release-v1.0-blue) ![OS](https://img.shields.io/badge/OS-windows,linux,macOS-blue) ![License](https://img.shields.io/badge/License-GPLv3.0-blue) ![contributions](https://img.shields.io/badge/contributions-welcome-greene) 

---

## Table of Contents

- [About](#about)
- [Documentation](#documentation)
  - [Structure  of the Repository](#structure-of-the-repository)
  - [Syntax of the Codes](#syntax-of-the-codes)
  - [Example of Running an Algorithm](#example-of-running-an-algorithm)
- [Feedback, Contributions, and Collaboration Opportunities](#feedback,-contributions,-and-collaboration-opportunities)
- [Cite repository](#cite-repository)
- [References](#references)

## About

The repository includes **MATLAB**-based implementations of sequential and parallel algorithms for solving global optimization problems under box, general, or hidden constraints. The code presented here extends the foundational research cited in references[^1][^2][^3][^4][^5][^6]. The algorithms included in this repository are the result of a PhD thesis[^7].

## Documentation

### Structure of the Repository

**Sequential Implementations Based on Static Data Structures[^1]:**

- For box-constrained global optimization[^3]; `sDirect_GL`, `sDirect_G`, and `sDirect_L`;
- For generally constrained global optimization[^4]: `sDirect_GLce`, `sDirect_GLc`, and `sDirect_GLce_min`;
- For problems with hidden constraints[^6]: `sDirect_GLh`.

**Sequential Implementations Based on Dynamic Data Structures[^2]:**

- For box-constrained global optimization[^3]; `dDirect_GL`, `dDirect_G`, and `dDirect_L`;
- For generally constrained global optimization[^4]: `dDirect_GLce`, `dDirect_GLc`, and `dDirect_GLce_min`;
- For problems with hidden constraints[^6]: `dDirect_GLh`.

**Parallel Implementations Based on Dynamic Data Structures[^2] and MATLAB SPMD[^5]:**

- For box-constrained global optimization[^3]; `parallel_dDirect_GL`, `parallel_dDirect_G`, and `parallel_dDirect_L`;
- For generally constrained global optimization[^4]: `parallel_dDirect_GLce`, `parallel_dDirect_GLc`, and `parallel_dDirect_GLce_min`;

### Syntax of the Codes

```matlab 
[fval, x, history] = algorithm(problem, bounds, options)
```

**Inputs:**

- `problem`: The structure defining the optimization problem.
- `bounds`: Specifies the lower and upper bounds for the design variables in the vector `x`.
- `options`: Minimizes with the optimization options specified in `options`.

**Outputs:**

- `fval`: The best-found value of the objective function.
- `x`: The best-found solution vector.
- `history`: Provides the iterative status and details during the optimization process.

### Example of Running an Algorithm

**Define Inputs**

```matlab
% Problem structure
problem.f = @(x) sum(x); % Objective function f(x)
problem.constraint = @(x) deal( sum(x.^2) - 3, 0 ); % inequality constraint function g(x) <= 0

% Bounds for the design variables
xL = -4*ones(3, 1); % lower bound vector
xU = 4*ones(3, 1); % upper bound vector
bounds = [xL, xU];

% Options structure
options.maxevals = 1e+4; % maximum number of function evaluations
options.maxits = 1e+4; % maximum number of algorithm iterations
options.showits = 0; % print iteration status
options.testflag = 1; % test flag if global minima is known
options.globalmin = -3; % globalmin (if known)
options.tol = 0.01; % tolerance for termination if testflag = 1
```

**Run the Algorithm**

```matlab
[fval, x] = dDirect_GLc(problem, bounds, options) % run the dDirect_GLc 
```

**Output**

```matlab
Minima was found with Tolerance: 0.01
fval =

   -2.9999

x =

   -1.0027
   -0.9950
   -1.0023
```

## Feedback, Contributions, and Collaboration Opportunities

We welcome contributions and corrections to this repository either way:

- **By email** - send the corrections, or suggestions by email: linas.stripinis@mif.vu.lt.
- **GitHub way** - fork the GitHub repository, correct the codes, then create a pull request, and I am gratefully incorporate your contribution!

Possible collaborations include:

- **Algorithm Development**: Contribute new algorithms or improve existing ones.
- **Benchmarking**: Help create and refine benchmark problems.
- **Integration**: Assist in integrating algorithms into broader systems.

## Cite Repository

Please use the following bibtex entry, if you consider to cite those implementations:

```latex
@misc{Stripinis2020directgl,
    title     = {{Sequential and parallel DIRECT-type algorithms for box and generally constrained global optimization problems in MATLAB}},
    author    = {Stripinis, Linas},
    year      = {2020},
    publisher = {GitHub},
    journal   = {GitHub repository},
    url       = {https://github.com/LinasStripinis/DIRECT-GL},
    version   = {1.0}
}

@phdthesis{Stripinis2021phd,
    booktitle = {Improvement, development and implementation of derivative-free global optimization algorithms},
    publisher = {Vilniaus universitetas. Prieiga per eLABa – nacionalinė Lietuvos akademinė elektroninė biblioteka},
    author    = {Stripinis, Linas},
    year      = {2021},
    school    = {Vilniaus universitetas},
    doi       = {10.15388/vu.thesis.138}, 
    language  = {eng},
    address   = {Vilnius},
    pages     = {156}
}
```

## References

[^1]: D. E. Finkel. (2004) MATLAB source code for DIRECT, http://www4.ncsu.edu/~ctk/Finkel_Direct/, online; accessed: 2017-03-22.
[^2]: J. He, L. T. Watson, N. Ramakrishnan, C. A. Shaffer, A. Verstak, J. Jiang, K. Bae, W. H. Tranter.  (2002). [Dynamic data structures for a DIRECT search algorithm](https://link.springer.com/article/10.1023/A:1019992822938), [Computational Optimization and Applications](https://link.springer.com/journal/10589). vol. 23, no 1, p. 5–25. DOI: [10.1023/A:1019992822938](https://doi.org/10.1023/A:1019992822938)
[^3]:L. Stripinis, R. Paulavičius, J. Žilinskas. (2018). [Improved scheme for selection of potentially optimal hyper-rectangles in DIRECT](http://link.springer.com/10.1007/s11590-017-1228-4). *[Optimization Letters](http://www.springer.com/mathematics/journal/11590)*, ISSN 1862-4472, vol. 12, no 7, p. 1699-1712, 1699-1712. DOI: [10.1007/s11590-017-1228-4](https://doi.org/10.1007/s11590-017-1228-4)
[^4]: L. Stripinis, R. Paulavičius, J. Žilinskas. (2019). [Penalty functions and two-step selection procedure based DIRECT-type algorithm for constrained global optimization](https://doi.org/10.1007/s00158-018-2181-2). *[ Structural and Multidisciplinary Optimization](https://www.springer.com/engineering/mechanics/journal/158)*, ISSN 1615-1488, vol. 59, no 6, p. 2155-2175. DOI: [10.1007/s00158-018-2181-2](https://doi.org/10.1007/s00158-018-2181-2)
[^5]: L. Stripinis, L. G. Casado, J. Žilinskas, R. Paulavičius. (2021). [On MATLAB experience in accelerating DIRECT-GLce algorithm for constrained global optimization through dynamic data structures and parallelization](https://www.sciencedirect.com/science/article/abs/pii/S0096300320305518?via%3Dihub). [*Applied Mathematics and Computation*](https://www.sciencedirect.com/journal/applied-mathematics-and-computation). ISSN: 0096-3003, vol. 390, no. 1, article 125596, 17 pages. DOI: [10.1016/j.amc.2020.125596](https://doi.org/10.1016/j.amc.2020.125596)
[^6]: L. Stripinis, R. Paulavičius. (2021). [A new DIRECT-GLh algorithm for global optimization with hidden constraints](https://link.springer.com/article/10.1007%2Fs11590-021-01726-z). [Optimization Letters](http://www.springer.com/mathematics/journal/11590), ISSN: 1862-4480, vol. 15, no 1, p. 1865-1884. DOI: [10.1007/s11590-021-01726-z](https://doi.org/10.1007/s11590-021-01726-z)  
[^7]: L. Stripinis. (2021). [Improvement, development and implementation of derivative-free global optimization algorithms]([Improvement, development and implementation of derivative-free global optimization algorithms](https://doi.org/10.15388/vu.thesis.138). Vilniaus universitetas. DOI: [10.15388/vu.thesis.138](https://doi.org/10.15388/vu.thesis.138)

