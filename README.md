# Lab 2: Traveling Salesman Problem (TSP)

(this readme is AI generated based on the contents of all the notebooks)

## Overview
Evolutionary algorithm implementation for solving symmetric and asymmetric TSP instances using (μ,λ)-ES with 2-opt mutations.



## Files

### Development Process
- **tests.ipynb** - Initial exploration: distance matrix validation, solution representations (matrix vs array)
- **tsp.ipynb** - First working implementation: dimension reduction for visualization, basic evolutionary algorithm with swap2opt
- **tsp2.ipynb** - Performance optimization: fast distance calculation for symmetric TSP, simulated annealing experiments
- **test3.ipynb** - Further testing and refinements
- **tests2.ipynb** - Asymmetric TSP exploration using graph transformation approach
- **final.ipynb** - Complete solution with all test instances

## Algorithm

### Symmetric TSP (G problems)
- **(μ,λ)-Evolutionary Strategy** with 2-opt swap mutation
- **Fast distance calculation**: O(1) distance update instead of O(n) recalculation
- **Initial solutions**: Random or ultra-greedy (best greedy from all starting cities)
- **Parameters**: λ=200-500, μ=20-50, generations=200-10000 depending on problem size

### Asymmetric TSP (R1, R2 problems)
- **Graph doubling technique**: Transform asymmetric graph into symmetric with 2n nodes
  - Nodes 0→n-1: entering cities
  - Nodes n→2n-1: leaving cities
  - Path 0→1→2 becomes 0→3→1→4→2→5→0 in doubled graph
- Convert back to simple path for final solution

## P.S.

## Results

### Test Problem
- **2823.79**

### Symmetric Problems (G)
| Instance | Best Distance |
|----------|---------------|
| G10      | 1497.66       |
| G20      | 1755.51       |
| G50      | 2629.99       |
| G100     | 4287.97       |
| G200     | 5688.67       |
| G500     | 9191.54       |
| G1000    | 13118.49      |

### Asymmetric Problems (R1)
| Instance | Best Distance |
|----------|---------------|
| R1_10    | 184.27        |
| R1_20    | 340.21        |
| R1_50    | 596.59        |
| R1_100   | 736.37        |
| R1_200   | 1103.90       |
| R1_500   | 1744.17       |
| R1_1000  | 2533.81       |

### Asymmetric Problems (R2)
*Note: All R2 problems optimally solved by ultra-greedy initial  (basically without running the algorithm)*

| Instance | Best Distance |
|----------|---------------|
| R2_10    | -411.70       |
| R2_20    | -796.86       |
| R2_50    | -2232.38      |
| R2_100   | -4667.68      |
| R2_200   | -9603.77      |
| R2_500   | -24584.05     |
| R2_1000  | -49477.87     |

## Sources

Often, algorithms and functions are present in multiple files. Only the first one I did has the sources. They are messy a little bit everywhere.

Below is what AI found:

- **2-opt algorithm**: https://en.wikipedia.org/wiki/2-opt
- **Distance matrix to coordinates conversion**: https://math.stackexchange.com/questions/156161/finding-the-coordinates-of-points-from-distance-matrix
- **MDS dimensionality reduction**: https://scikit-learn.org/stable/modules/generated/sklearn.manifold.MDS.html
- **Asymmetric TSP transformation**: https://www.comp.nus.edu.sg/~gilbert/CS4234/2015/lectures/06.ATSP.pdf Note that this is a thing that I tried but did not manage to get working. The transformation of the nxn matrix to 2nx2n is something else.
I don't know why but the ultra-greedy initial solution seems to be optimal for the R2 problems and not for the other problems.