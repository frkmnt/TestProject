# TestProject

This is an overview of the decisions made when working on this challenge.

I decided to use Unreal Engine 5.1.1, since I've yet to use 5. Therefore, I faced this challenge as a more of a learning exercise and as a way to show adaptability.

After considering the requirements, I believe this exercise can be broken down into 4 smaller problems:

* 1 Creating a grid composed of hexes and its respective tile outlines;
* 2 Binding said grid to a backend data structure that allows pathfinding;
* 3 Simulating a server-side seed generator that deterministically outputs a match result;
* 4 Representing the combat through non-UI methods.

In order of execution, I handled the problems as follows:

* Problem 1:
I created an 11x11 hexagonal grid system using meshes that weave together. Each second column must be offset
vertically so as to meld into the previous row's shape. 
The meshes used for the hexes have a 120 unit radius if placed inside of a circle.
The outline can be achieved by simply placing a gap between tiles, as a simple solution.

* Problem 2:
During the hexagon's spawning process, they are bound to a map of Vector2D -> Tile.
This can be used in conjunction with the Astar algorithm to enable seamless pathfindind.
I chose to use Astar since it is a scalable algorithm, and I wanted the challenge. But since all tiles have a traversal weight of 1,
a much simpler algorithm could have been used. This system allows many simultaneous agents to move around and interact with each other
in an efficient manner.

* Problem 3:
I created the GameOverseer as a way to "black box" any server interactions that may take place. It is responsible for
spawning and managing entities, and it also simulates the 100ms ticks by pinging each relevant agent whenever needed.
I didn't implement a seed management system to provide a deterministic outcome. Each agent's logic is handled here.

* Problem 4:
I represented damage dealt by simply scaling down the agents in regards to their maximum HP whenever they were dealt damage.

The end result allows many simultaneous agents to pathfind and interact with each other, each with slightly randomized stats.





