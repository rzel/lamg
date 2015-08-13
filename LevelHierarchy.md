# Creating a Hierarchy #
A LAMG multi-level hierarchy can be created for a symmetric adjacency sparse matrix `A`. There is no need to solve a linear system `Ax=b`. For instance, the 5-point Laplacian on a 20x20 grid can be constructed manually, or via the provided functions
```
g = Graphs.grid('fd', [20 20]);
A = g.symAdjacency;
```
To create the hierarchy, run
<a>
<pre><code>% Construct a solver<br>
lamg = Lamg();<br>
% Construct the LAMG multi-level hierarchy<br>
setup = lamg.setup(A);<br>
</code></pre>
<h1>Printing Hierarchy Statistics</h1>
Displaying the <code>setup</code> object prints summative statistics:<br>
<pre><code>&gt;&gt; setup<br>
<br>
setup = <br>
<br>
Multi-level setup<br>
	#levels      = 3<br>
	Design gamma = 1.5<br>
	# components = 1<br>
	Node  complexity = 1.715<br>
	Edge  complexity = 2.314<br>
	Cycle complexity = 3.505<br>
Level Type     Nodes   Edges    #Comp alpha    AvgDeg nu  gam  Work  #TV     <br>
===========================================================================<br>
1     FINEST   400     760      0     1.000    3.80   0   1.0  0.00  0  <br>
2     ELIM     194     709      0     0.485    7.31   3   1.5  3.31  8  <br>
3     AGG      92      290      1     0.474    6.30   0   0.0  0.19  0  <br>
</code></pre>

<h1>Getting Individual Level Information</h1>
The hierarchy is stored in the cell array <code>setup.level</code>. Levels are sorted finest to coarsest, i.e., <code>setup.level{1</code>} is the finest level, <code>setup.level{2</code>} is the first coarse level, and so on.<br>
<pre><code>&gt;&gt; setup.level<br>
<br>
ans = <br>
<br>
    [1x1 amg.level.LevelFinest     ]<br>
    [1x1 amg.level.LevelElimination]<br>
    [1x1 amg.level.LevelAgg        ]<br>
<br>
&gt;&gt; setup.level{1}<br>
<br>
ans = <br>
<br>
  amg.level.LevelFinest handle<br>
  Package: amg.level<br>
<br>
  Properties:<br>
                   coord: []<br>
              zeroMatrix: 0<br>
       disconnectedNodes: [1x0 double]<br>
    hasDisconnectedNodes: 0<br>
           numComponents: 1<br>
          componentIndex: {[400x1 double]}<br>
                   rhsMu: []<br>
                       x: []<br>
                   index: 1<br>
                   state: [1x1 amg.setup.CoarseningState]<br>
                    type: [1x1 amg.level.LevelType]<br>
                    name: 'graph'<br>
                    size: 400<br>
               fineLevel: []<br>
                       g: [1x1 graph.api.Graph]<br>
                 relaxer: [1x1 amg.relax.RelaxElimination]<br>
                       K: 8<br>
                       r: []<br>
                       A: [400x400 double]<br>
<br>
  Methods, Events, Superclasses<br>
<br>
&gt;&gt; setup.level{2}<br>
<br>
ans = <br>
<br>
  amg.level.LevelElimination handle<br>
  Package: amg.level<br>
<br>
  Properties:<br>
                   coord: []<br>
               numStages: 3<br>
                   stage: {[1x1 struct]  [1x1 struct]  [1x1 struct]}<br>
                       c: [194x1 double]<br>
              components: []<br>
              zeroMatrix: 0<br>
       disconnectedNodes: [1x0 double]<br>
    hasDisconnectedNodes: 0<br>
           numComponents: 1<br>
          componentIndex: {[194x1 double]}<br>
                   rhsMu: []<br>
                       x: [194x8 double]<br>
                   index: 2<br>
                   state: [1x1 amg.setup.CoarseningState]<br>
                    type: [1x1 amg.level.LevelType]<br>
                    name: 'graph'<br>
                    size: 194<br>
               fineLevel: [1x1 amg.level.LevelFinest]<br>
                       g: [1x1 graph.api.Graph]<br>
                 relaxer: [1x1 amg.relax.RelaxGaussSeidel]<br>
                       K: 8<br>
                       r: []<br>
                       A: [194x194 double]<br>
<br>
  Methods, Events, Superclasses<br>
</code></pre>
Each level holds the following fields (and many other useful fields):<br>
<ul><li><code>type</code> - level type: <code>FINEST</code> = finest level, <code>ELIMINATION</code> = obtained using exact elimination from next-finer level, <code>AGG</code> = aggregation of next-finer level nodes.<br>
</li><li><code>g</code> - graph corresponding to this level's Laplacian matrix. Has no nodes.<br>
</li><li><code>K</code> - number of test vectors.<br>
</li><li><code>x</code> - nxK test vector matrix. <code>x(:,k)</code> is the <code>k</code><i>th</i> test vector.<br>
vector.<br>
</li><li><code>P</code> - interpolation operator (may be available except in finest level in LAMG 1.1.0 and later versions).<br>
</li><li><code>R</code> - restriction operator (may be available except in finest level in LAMG 1.1.0 and later versions).<br>
</li><li><code>T</code> - coarse-variable type operator (available in <code>AGG</code> levels only).</li></ul>

<h1>Plotting a Level</h1>
<i>(This documentation will change and be made simpler in LAMG 1.1.0)</i>

Use the <code>plotLevel</code> function. In LAMG 1.0.x, this function relies on the <code>graphViz</code> MATLAB package, and you will need to provide the path to the {{sfdp}}} executable on your system in the file <code>config.txt</code> under the LAMG distribution.<br>
<pre><code>&gt;&gt; plotLevel(setup, 3, 'nodeSize', 0.04);<br>
neato - graphviz version 2.28.0 (20110507.0327) <br>
dot - graphviz version 2.28.0 (20110507.0327) <br>
twopi - graphviz version 2.28.0 (20110507.0327) <br>
neato - graphviz version 2.28.0 (20110507.0327) <br>
fdp - graphviz version 2.28.0 (20110507.0327) <br>
&gt;&gt;<br>
</code></pre>
<p align='center'>
<img src='http://lamg.googlecode.com/files/level3_plot.png' align='middle' alt='Logo' width='45%' />
</p>