# Pathfinding with robots in a grid using the genetic algorithm

## Summary

We explore the genetic algorithm in a pathfinding problem: given a virtual robot (at some position $(x,y)$) capable of receiving instructions ('move up', 'move down',...) to move in a 2D grid, what is the set of instructions we should feed it to make it reach the goal $(x', y')$? (We do not care if the path is the shortest or not).   
Pathfinding problems are both interesting and useful, but there are many (better) ways to deal with them.
Here we use the problem as a way to explore the genetic algorithm, and to see it in action in a geometrical and intuitive problem.  

The genetic algorithm mimics natural selection: [Norvig]

    1) Start with an *initial population* (of candidates to a solution), each individual having its own set of *genes* (descriptors of the solution proposal);
    2) Determine how *fit* (how close they are to truly providing a solution to the problem) the individuals in the population are;
    3) *Select* the individuals which are going to reproduce using their fitness levels: the fitter, the more likely to reproduce;
    4) Couple the selected individuals in pairs (of *parents*) and generate two *children* for each pair of parents by *crossing over* (mixing) the parents' genes;
    5) Introduce a slight *mutation* in the children genes, so that their genes are not just a mix of their parents' genes, and evolution can occur.
    6) These children are now the new population. Repeat 2) $\rightarrow$ 5) until one of the individuals solves the problem (has maximum fitness) or we reach our maximum number of iterations.
