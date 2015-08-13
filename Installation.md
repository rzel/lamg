# LAMG Code Installation #
  * **Step 1:** [Download](http://code.google.com/p/lamg/downloads/list) the latest release of the code and unzip it, say into `C:\lamg`.
  * **Step 2:** In MATLAB, run the comand
```
     cd lamg; make('compile');
```
  * **Step 4**: verify the successful installation of LAMG by typing at the MATLAB prompt:
```
>> lamg_example
```
> The output should be similar to:
```
Setting up problem
Setting up solver
Updated state to FINEST
======= Constructing Level   1, strategy FINEST =======
Updated state to ELIM
Level size: nodes=160000, edges=319200
======= Constructing Level   2, strategy ELIM =======
Elimination stage  1: total=   80000  f=   80000  c=   80000  edges=  318401
stopping elimination: total=   80000  f=       4  c=   79996
Updated state to AGG
Level size: nodes=80000, edges=318401
======= Constructing Level   3, strategy AGG =======
Computing relaxation speed
Relaxation ACF = 0.904, acceptable ACF = 0.300
### Aggregation: gamma = 1.5 ###
   #suns = 0, marked as seeds
   #delta-affiliate edges = 318401 / 318401 total edges
Stage  1     nc = 33003 alpha = 0.41   beta = 0.59   delta = 0.00e+000  d/(1+d)=0.00
Optimal: 1   nc = 33003 alpha = 0.41   beta = 0.59
Updated state to ELIM
#edges = 318401  finest edges = 319200
Setting cycle index to 1.5 (fine level)
Level size: nodes=33003, edges=117828
======= Constructing Level   4, strategy ELIM =======
Elimination stage  1: total=   32344  f=     659  c=   32344  edges=  116372
stopping elimination: total=   32344  f=      48  c=   32296
Updated state to AGG
Level size: nodes=32344, edges=116372
======= Constructing Level   5, strategy AGG =======
Computing relaxation speed
Relaxation ACF = 0.930, acceptable ACF = 0.300
### Aggregation: gamma = 1.5 ###
   #suns = 0, marked as seeds
   #delta-affiliate edges = 115951 / 115951 total edges
Stage  1     nc = 14055 alpha = 0.43   beta = 0.57   delta = 0.00e+000  d/(1+d)=0.00
Optimal: 1   nc = 14055 alpha = 0.43   beta = 0.57
Updated state to ELIM
#edges = 116372  finest edges = 319200
Setting cycle index to 1.5 (fine level)
Level size: nodes=14055, edges=46314
======= Constructing Level   6, strategy ELIM =======
Elimination stage  1: total=   12944  f=    1111  c=   12944  edges=   43709
stopping elimination: total=   12944  f=     103  c=   12841
Updated state to AGG
Level size: nodes=12944, edges=43709
======= Constructing Level   7, strategy AGG =======
Computing relaxation speed
Relaxation ACF = 0.938, acceptable ACF = 0.300
### Aggregation: gamma = 1.5 ###
   #suns = 0, marked as seeds
   #delta-affiliate edges = 40370 / 40370 total edges
Stage  1     nc = 5750  alpha = 0.44   beta = 0.56   delta = 0.00e+000  d/(1+d)=0.00
Optimal: 1   nc = 5750  alpha = 0.44   beta = 0.56
Updated state to ELIM
#edges = 43709  finest edges = 319200
Setting cycle index to 1.5 (fine level)
Level size: nodes=5750, edges=18275
======= Constructing Level   8, strategy ELIM =======
Elimination stage  1: total=    5126  f=     624  c=    5126  edges=   16833
Elimination stage  2: total=    5053  f=      73  c=    5053  edges=   16654
stopping elimination: total=    5053  f=       5  c=    5048
Updated state to AGG
Level size: nodes=5053, edges=16654
======= Constructing Level   9, strategy AGG =======
Computing relaxation speed
Relaxation ACF = 0.941, acceptable ACF = 0.300
### Aggregation: gamma = 1.5 ###
   #suns = 0, marked as seeds
   #delta-affiliate edges = 14630 / 14630 total edges
Stage  1     nc = 2277  alpha = 0.45   beta = 0.55   delta = 0.00e+000  d/(1+d)=0.00
Optimal: 1   nc = 2277  alpha = 0.45   beta = 0.55
Updated state to ELIM
#edges = 16654  finest edges = 319200
Setting cycle index to 1.5 (guard)
Level size: nodes=2277, edges=7119
======= Constructing Level  10, strategy ELIM =======
Elimination stage  1: total=    2006  f=     271  c=    2006  edges=    6516
Elimination stage  2: total=    1968  f=      38  c=    1968  edges=    6416
stopping elimination: total=    1968  f=       5  c=    1963
Updated state to AGG
Level size: nodes=1968, edges=6416
======= Constructing Level  11, strategy AGG =======
Computing relaxation speed
Relaxation ACF = 0.938, acceptable ACF = 0.300
### Aggregation: gamma = 1.5 ###
   #suns = 0, marked as seeds
   #delta-affiliate edges = 5666 / 5666 total edges
Stage  1     nc = 907   alpha = 0.46   beta = 0.54   delta = 0.00e+000  d/(1+d)=0.00
Optimal: 1   nc = 907   alpha = 0.46   beta = 0.54
Updated state to ELIM
#edges = 6416  finest edges = 319200
Setting cycle index to 1.5 (guard)
Level size: nodes=907, edges=2814
======= Constructing Level  12, strategy ELIM =======
Elimination stage  1: total=     807  f=     100  c=     807  edges=    2585
Elimination stage  2: total=     787  f=      20  c=     787  edges=    2538
stopping elimination: total=     787  f=       4  c=     783
Updated state to AGG
Level size: nodes=787, edges=2538
======= Constructing Level  13, strategy AGG =======
Computing relaxation speed
Relaxation ACF = 0.962, acceptable ACF = 0.300
### Aggregation: gamma = 1.5 ###
   #suns = 0, marked as seeds
   #delta-affiliate edges = 2245 / 2245 total edges
Stage  1     nc = 366   alpha = 0.47   beta = 0.53   delta = 0.00e+000  d/(1+d)=0.00
Optimal: 1   nc = 366   alpha = 0.47   beta = 0.53
Updated state to ELIM
#edges = 2538  finest edges = 319200
Setting cycle index to 1.5 (guard)
Level size: nodes=366, edges=1106
======= Constructing Level  14, strategy ELIM =======
Elimination stage  1: total=     303  f=      63  c=     303  edges=     969
Elimination stage  2: total=     295  f=       8  c=     295  edges=     948
stopping elimination: total=     295  f=       2  c=     293
Updated state to AGG
Level size: nodes=295, edges=948
======= Constructing Level  15, strategy AGG =======
Computing relaxation speed
Relaxation ACF = 0.935, acceptable ACF = 0.300
### Aggregation: gamma = 1.5 ###
   #suns = 0, marked as seeds
   #delta-affiliate edges = 827 / 827 total edges
Stage  1     nc = 133   alpha = 0.45   beta = 0.55   delta = 0.00e+000  d/(1+d)=0.00
Optimal: 1   nc = 133   alpha = 0.45   beta = 0.55
Updated state to ELIM
Reached a small enough graph (< 200)
Updated state to DONE_COARSENING
#edges = 948  finest edges = 319200
Setting cycle index to 1.5 (guard)
Level size: nodes=133, edges=395
Solving A*x=b
Initial     e=2.843e+002
Iter    1   e=1.089e+001  conv=0.038   time=0.16 [sec]
Iter    2   e=3.150e+000  conv=0.289   time=0.17 [sec]
Iter    3   e=8.223e-001  conv=0.261   time=0.17 [sec]
Iter    4   e=2.022e-001  conv=0.246   time=0.16 [sec]
Iter    5   e=5.446e-002  conv=0.269   time=0.16 [sec]
Iter    6   e=1.486e-002  conv=0.273   time=0.18 [sec]
Iter    7   e=3.845e-003  conv=0.259   time=0.15 [sec]
Iter    8   e=9.798e-004  conv=0.255   time=0.15 [sec]
Iter    9   e=2.486e-004  conv=0.254   time=0.15 [sec]
Iter   10   e=6.333e-005  conv=0.255   time=0.17 [sec]
Total time: 1.6 [sec]
------------------------------------------------------------------------
Multi-level setup
	#levels          = 15
	Design gamma     = 1.5
	Edge  complexity = 3.190
	Cycle complexity = 7.684
l  Type     Nodes    Edges    NodeR  EdgeR   DegL1   Nu  Gam  Work  TV 
=======================================================================
1  FINEST   160000   319200   1.000  1.000  3.99    0   1.0  0.00  0  
2  ELIM     80000    318401   0.500  0.997  7.96    3   1.5  3.49  4  
3  AGG      33003    117828   0.413  0.370  7.14    0   1.0  0.19  0  
4  ELIM     32344    116372   0.980  0.988  7.20    3   1.5  1.65  5  
5  AGG      14055    46314    0.435  0.398  6.59    0   1.0  0.11  0  
6  ELIM     12944    43709    0.921  0.944  6.75    3   1.5  0.94  6  
7  AGG      5750     18275    0.444  0.418  6.36    0   1.0  0.07  0  
8  ELIM     5053     16654    0.879  0.911  6.59    3   1.5  0.54  7  
9  AGG      2277     7119     0.451  0.427  6.25    0   1.0  0.04  0  
10 ELIM     1968     6416     0.864  0.901  6.52    3   1.5  0.31  8  
11 AGG      907      2814     0.461  0.439  6.21    0   1.0  0.02  0  
12 ELIM     787      2538     0.868  0.902  6.45    3   1.5  0.19  9  
13 AGG      366      1106     0.465  0.436  6.04    0   1.0  0.01  0  
14 ELIM     295      948      0.806  0.857  6.43    3   1.5  0.11  10 
15 AGG      133      395      0.451  0.417  5.94    0   0.0  0.01  0  

MVM time [sec]       elapsed 0.003, per edge 9.10e-009
Setup time [sec]     elapsed 1.106, per edge 3.46e-006, in MVM 380.66
Solve time [sec]     elapsed 1.701, per edge 8.01e-007, in MVM 585.51
|A*x-b|/|b|          5.49e-007
Convergence factor   0.256
```

# Configuring Logging Levels #
Edit 'logging\_config.m'. Logging level conventions are the same as in [Log4J](http://logging.apache.org/log4j/1.2/): `ERROR,WARN,INFO,DEBUG,TRACE`. Levels are per package and inherited from the parent package if not specified. For instance, to suppress all logging messages, you need only one line at the bottom of the file:
```
logger('amg') = 'WARN';
```

# LAMG Code Uninstallation #
In MATLAB, run the comand
```
     cd lamg; rmpathsub('C:\lamg');
```
The LAMG directories should now be removed from your MATLAB path.