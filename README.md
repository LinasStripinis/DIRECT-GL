# Sequential and Parallel DIRECT-type Implementations

This repository contains MATLAB-based implementations of both sequential and parallel algorithms designed for box-constrained, generally constrained, and hidden constrained global optimization problems. The code provided here builds upon the foundational works referenced in [1] through [7].

**Sequential Implementations Based on Static Data Structures [3]:**

- For box-constrained global optimization; `sDirect_GL`, `sDirect_G`, and `sDirect_L`;
- For generally constrained global optimization: `sDirect_GLce`, `sDirect_GLc`, and `sDirect_GLce_min`;
- For problems with hidden constraints: `sDirect_GLh`.

**Sequential Implementations Based on Dynamic Data Structures [3]:**

- For box-constrained global optimization; `dDirect_GL`, `dDirect_G`, and `dDirect_L`;
- For generally constrained global optimization: `dDirect_GLce`, `dDirect_GLc`, and `dDirect_GLce_min`;
- For problems with hidden constraints: `dDirect_GLh`.

**Parallel Implementations Based on Dynamic Data Structures [3] and MATLAB SPMD [x]:**

- For box-constrained global optimization; `parallel_dDirect_GL`, `parallel_dDirect_G`, and `parallel_dDirect_L`;
- For generally constrained global optimization: `parallel_dDirect_GLce`, `parallel_dDirect_GLc`, and `parallel_dDirect_GLce_min`;

## Syntax

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

## Example

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

[fval, x] = dDirect_GLc(problem, bounds, options)
Minima was found with Tolerance: 1.000000e-02
fval =

   -2.9999

x =

   -1.0027
   -0.9950
   -1.0023
```



## References

[1] C. A. Baker, L. T. Watson, B. Grossman, W. H. Mason, R. T. Haftka, [Parallel global aircraft configuration design space exploration, in: A. Tentner (Ed.)](https://www.semanticscholar.org/paper/Parallel-Global-Aircraft-Configuration-Design-Space-Baker-Watson/2ca51b579b927476a21a4a751ef2ca8792f8944a), High Performance Computing Symposium 2000, Soc. for Computer Simulation Internat, 2000, pp. 54–66. <a name="1">
</a>

[2] D. E. Finkel, MATLAB source code for DIRECT, http://www4.ncsu.edu/~ctk/Finkel_Direct/, online; accessed: 2017-03-22 (2004).

[3] J. He, L. T. Watson, N. Ramakrishnan, C. A. Shaffer, A. Verstak, J. Jiang, K. Bae, W. H. Tranter, [Dynamic data structures for a DIRECT search algorithm](https://link.springer.com/article/10.1023/A:1019992822938), Computational Optimization and Applications 23 (1) (2002) 5–25. 

[4] L. Stripinis, R. Paulavičius, J. Žilinskas, [Improved scheme for selection of potentially optimal hyper-rectangles in DIRECT](https://link.springer.com/article/10.1007/s11590-017-1228-4), Optimization Letters 12 (7) (2018) 1699–1712. doi:10.1007/ s11590-017-1228-4. <a name="2">
</a>

[5] L. Stripinis, R. Paulavičius, and J. Žilinskas, [Penalty functions and two-step selection procedure based DIRECT-type algorithm for constrained global optimization](http://link.springer.com/10.1007/s00158-018-2181-2), Struct. Multidiscip. Optim., vol. 59, no. 6, pp. 2155–2175, 2019. <a name="3">
</a>

[6] L. Stripinis, J. Žilinskas, L. G. Casado, and R. Paulavičius, *On MATLAB experience in accelerating DIRECT-GLce algorithm for constrained global optimization through dynamic data structures and parallelization*, Applied Mathematics and Computation. ISSN: 0096-3003. 2021, vol. 390, p. 1-17. DOI: 10.1016/j.amc.2020.125596. <a name="4">
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
