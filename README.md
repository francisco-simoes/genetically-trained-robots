# Pathfinding with virtual robots in a grid using the genetic algorithm
(UNDER CONSTRUCTION)

## Summary

We explore the genetic algorithm in the context of a pathfinding problem: given a virtual robot (at some position (x,y)) capable of receiving instructions ('move up', 'move down',...) to move in a 2D grid, what is the set of instructions we should feed it to make it reach the goal (x', y')? (We do not care if the path is the shortest or not).   
Pathfinding problems are both interesting and useful, but there are many (better) ways to deal with them.
Here we use the problem as a way to explore the genetic algorithm, and to see it in action in a geometrical and intuitive problem. I learned the conceptual framework behind the genetic algorith in [Norvig] (where the authors discuss how to solve the 8-queens problem in chess using this algorithm).

## Main steps of the project

### Our robots and grid
  
Our robots must be at a certain position in the grid at all times, and be able to move up. down, left or right (on each step).  
I use a 10x10 grid, meaning that the maximum number of steps one could possibly need to reach one position from another is (10-1) x 2 = 18.
Accordingly, the set of orders that the a robot must obey will be written as a string of length 18, each character being either 'u', 'd', 'l' or 'r', corresponding to the four directions we want the robot to move in. 

<p align="center">
  <img src="images/grid.png" alt="hi" class="inline"/>
</p>
(Blue squares are positions where the robot has been in the past; the yellow square is the position for the current iteration).


So I started by defining a Robot class compatible with these requirements.
A robot is an instance of the Robot class.
To define a robot we need to specify an initial grid position (x,y), an ID number for the robot and a string `orders` of length 18 as described above.

But how to evolve our robots?

## The genetic algorithm mimics natural selection:

   1. Start with an *initial population* (of candidates to a solution), each individual having its own set of *genes* (descriptors of the solution proposal);
   2. Determine how *fit* (how close they are to truly providing a solution to the problem) the individuals in the population are;
   3. *Select* the individuals which are going to reproduce using their fitness levels: the fitter, the more likely to reproduce;
   4. Couple the selected individuals in pairs (of *parents*) and generate two *children* for each pair of parents by *crossing over* (mixing) the parents' genes;
   5. Introduce a slight *mutation* in the children genes, so that their genes are not just a mix of their parents' genes, and evolution can occur.
   6. These children are now the new population. Repeat 2. --> 5. until one of the robots solves the problem (has maximum fitness) or we reach our maximum number of iterations.
   
   <p align="center">
  <img src="images/scheme.png" alt="hi" class="inline"/>
</p>


## Evolution of the robots:

Implementing the algorithm with initial position (0,0) for all robots and goal=(9,9), it was necessary to use 139 generations (iterations) to find a robot that achieves the goal.
   
   Best robot of generation 20:
   <p align="center">
  <img src="images/BestRobot20.png" alt="hi" class="inline"/>
</p>

   
   Best robot of generation 40:
   
   <p align="center">
  <img src="images/BestRobot40.png" alt="hi" class="inline"/>
</p>

   
   Best robot of generation 60:
   
   <p align="center">
  <img src="images/BestRobot60.png" alt="hi" class="inline"/>
</p>

   
   Best robot of generation 139:
   
   <p align="center">
  <img src="images/BestRobot139.png" alt="hi" class="inline"/>
</p>

   <p align="center">
  <img src="images/fitness_plot.png" alt="hi" class="inline"/>
</p>

   
   ## References

- [Norvig]: Russell, Stuart J., and Peter Norvig. *Artificial intelligence: a modern approach*. Malaysia; Pearson Education Limited,, 2016.
