This example is in the m-file ```
examples/lamg_example.m``` in the distribution. See other examples in this directory for SDD systems.

# Basic Example #
<a>
<pre><code>%=========================================================================<br>
% lamg_example.m<br>
%<br>
% LAMG Example usage: solve a graph Laplacian system with a random<br>
% compatible right-hand side.<br>
%=========================================================================<br>
<br>
fprintf('Setting up problem\n');<br>
g = Graphs.grid('fd', [40 40], 'normalized', true);<br>
A = g.laplacian;                % Zero row-sum (Neumann B.C.)<br>
b = rand(size(A,1), 1);<br>
b = b - mean(b);                % Make RHS compatible with A's null space<br>
inputType = 'laplacian';        % The input matrix A is a graph Laplacian<br>
solver = 'lamg';                % Or 'cmg', or 'direct'<br>
<br>
%---------------------------------------------------------------------<br>
% Setup phase: construct a LAMG multi-level hierarchy<br>
%---------------------------------------------------------------------<br>
fprintf('Setting up solver %s\n', solver);<br>
lamg    = Solvers.newSolver(solver, 'randomSeed', 1);<br>
tStart  = tic;<br>
setup   = lamg.setup(inputType, A);<br>
tSetup  = toc(tStart);<br>
<br>
%---------------------------------------------------------------------<br>
% Solve phase: set up a random compatible RHS b and solve A*x=b. You can<br>
% repeat this phase for multiple b's without rerunning the setup phase.<br>
%---------------------------------------------------------------------<br>
setRandomSeed(now);<br>
% Turn on debugging printouts during the run<br>
core.logging.Logger.setLevel('lin.api.AcfComputer', core.logging.LogLevel.DEBUG);<br>
fprintf('Solving A*x=b\n');<br>
tStart = tic;<br>
[x, ~, ~, details] = lamg.solve(setup, b, 'errorReductionTol', 1e-8);<br>
tSolve = toc(tStart);<br>
% Turn printouts off<br>
core.logging.Logger.setLevel('lin.api.AcfComputer', core.logging.LogLevel.INFO);<br>
fprintf('------------------------------------------------------------------------\n');<br>
<br>
%---------------------------------------------------------------------<br>
% Display statistics<br>
%---------------------------------------------------------------------<br>
disp(setup);<br>
tMvm    = mvmTime(A, 5);<br>
nnz     = numel(nonzeros(A));<br>
<br>
fprintf('\n');<br>
fprintf('MVM time [sec]       elapsed %.3f, per nonzero %.2e\n', ...<br>
    tMvm, tMvm / nnz);<br>
fprintf('Setup time [sec]     elapsed %.3f, per nonzero %.2e, in MVM %.2f\n', ...<br>
    tSetup, tSetup / nnz, tSetup / tMvm);<br>
fprintf('Solve time [sec]     elapsed %.3f, per nonzero %.2e, in MVM %.2f\n', ...<br>
    tSolve, normalizedSolveTime(tSolve, details.errorNormHistory) / nnz, tSolve / tMvm);<br>
fprintf('|A*x-b|/|b|          %.2e\n', norm(A*x-b)/norm(b));<br>
if (isfield(details, 'acf'))<br>
    fprintf('Convergence factor   %.3f\n', details.acf);<br>
end<br>
</code></pre>

Output (when debugging is turned on):<br>
<pre><code>Setting up problem<br>
Setting up solver lamg<br>
Solving A*x=b<br>
------------------------------------------------------------------------<br>
Multi-level setup<br>
	#levels          = 5<br>
	Design gamma     = 1.5<br>
	Edge  complexity = 2.866<br>
	Cycle complexity = 5.405<br>
l  Type     Nodes    Edges    NodeR  EdgeR   DegL1   Nu  Gam  Work  TV <br>
=======================================================================<br>
1  FINEST   1600     3120     1.000  1.000  3.90    0   1.0  0.00  0  <br>
2  ELIM     798      3038     0.499  0.974  7.61    3   1.5  3.42  4  <br>
3  AGG      358      1201     0.449  0.395  6.71    0   1.0  0.19  0  <br>
4  ELIM     327      1141     0.913  0.950  6.98    3   1.5  1.67  5  <br>
5  AGG      146      442      0.446  0.387  6.05    0   0.0  0.12  0  <br>
<br>
MVM time [sec]       elapsed 0.000, per nonzero 4.23e-009<br>
Setup time [sec]     elapsed 0.095, per nonzero 1.22e-005, in MVM 2878.14<br>
Solve time [sec]     elapsed 0.071, per nonzero 1.08e-006, in MVM 2136.91<br>
|A*x-b|/|b|          1.03e-008<br>
Convergence factor   0.158<br>
</code></pre>

<h1>Customizing the Algorithm</h1>
LAMG is supposed to be a black-box solver, so in most cases you don't need to tweak any options!<br>
<br>
If you do need to, all options are attributes of the class <code>amg.api.Options</code> and described therein. You can pass key-value pairs at the end of the <code>newSolver('lamg')</code>, <code>setup()</code> and solve()` calls. Examples:% Measure convergence in the residual L2 norm.<br>
% Options passed to the constructor are used by both the setup and solve phases.<br>
lamg    = Solvers.newSolver('lamg', 'errorNorm', @errorNormResidual);<br>
<br>
% Stop coarsening when the graph has less than 200 edges<br>
setup = lamg.setup(A, 'maxDirectSolverSize', 200);<br>
<br>
% Solve A*x=b to 8 significant figures<br>
[x, details] = lamg.linearSolve(setup, b, 'errorReductionTol', 1e-8);</code></pre>