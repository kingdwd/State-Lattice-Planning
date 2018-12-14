# State Lattice Planning
Artificial Intelligence Practicum - University of Colorado Boulder  
Mark Ivlev and Spencer Wegner  
December 2018  

## Methods
&nbsp;&nbsp;&nbsp;&nbsp;State Lattice Planning is a method of state space navigation that uses A* search to get an agent from a start state to a goal state. Similarly to Pivtoraiko, Knepper and Kelly, the goal for this project is finding a path between two states vehicle considering its heading and wheel angle and in the presence of arbitrary obstacles. The state lattice itself is “a particular discretization of robot state space” (Pivtoraiko, Knepper, Kelly 1). Discretization of the state space drastically reduces the overall computational complexity of motion plan- ning. Initially, the agent does not have any knowledge about the state space except how it is structured, so it makes an initial plan to go straight to the goal, using A*. This means that the agent “sees” its own version of the state space that initially, as far as the agent knows, is completely free of any obstacles. As the agent moves along its initial A* route, it updates its knowledge of the state space by “perceiving” the space around it. If the agent perceives that there is an obstacle obstructing its path, it will re-plan using A*. At any given point along a path, the agent has only “seen” a certain amount of the actual state lattice, and so it will plan according to what it knows. Furthermore, throughout navigation, the agent is aware of the direction of its wheels (center, left or right) and its heading (North, South, East or West). Because of these added parameters, the agent is a more realistic representation of an an actual robot. This implementation is similar to that of others such as Pivtoraiko, Knepper and Kelly in multiple published papers, as well as McNaughton, Urmson, Dolan and Lee.

&nbsp;&nbsp;&nbsp;&nbsp;The methods we implemented for this project were building a randomized state lattice, and modifying A* search to work with the additional parameters of heading and wheel angle. Both the heading and wheel angle are discrete sets of options, rather than continuous. Each time the program is run, the size of the state lattice may be changed, as well as the amount of “vision” the agent has (how far ahead it can see when updating its knowledge), the start and goal positions of the agent, and the probability distribution for the obstacles in the state lattice. Each position in the state lattice is a tuple in the form of (X, Y, Heading, Wheel Angle). X and Y are integers that form a coordinate position. Heading takes one of four options: north, south, east or west, and wheel angle takes one of three options: center, left or right. The probability distribution represents the probability that any given space in the state lattice will have an obstacle in it. For example, a probability distribution of [0.8,0.2] would give an 80% chance that any given space will be open and a 20% chance that a space will have an obstacle in it. Upon running the program, the agent will attempt to make its way through the randomized state space. If it successfully navigates to the goal state, the path that the agent took will be printed, as well as the total number of A* plans, path cost and number of nodes expanded. If the agent is unable to reach the goal state, that means that there is no possible path to the goal state in the state space. The program will still print all of the information about path, plans, cost, and expansion relevant to the point at which the agent figured out that there was no available path.

&nbsp;&nbsp;&nbsp;&nbsp;While our implementation of state lattice planning did include most of the necessary methods, there were some methods that we did not implement, or did not fully implement. Pivtoraiko, Knepper and Kelly have published several papers on state lattice planning ad- dressing the methods that were not fully implemented in our project, such as better represen- tations of wheel angle, heading, and the state lattice itself. Additionally, our implementation would need some adapting in order to be used with an actual robot, as it stands right now it is only a simulation.
