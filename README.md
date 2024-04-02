<h1>Multiple-Objective Routing Path Optimisation - Search and Optimisation</h1>

<h1>Introduction</h1>
The project aims to address the critical challenge of optimizing data packet routing in vehicle networks along a motorway. With the increasing demand for Internet access in vehicles, the project proposes a solution where cars act as relay nodes to enhance connectivity. By strategically routing data packets through neighboring vehicles, we aim to maximize the end-to-end data transmission rate while minimizing latency.
<br />
<h2>Used Libraries</h2>
1. pandas <br/>
2. matplotlib.pyplot <br/>
3. numpy<br/>
4. networkx<br/>
5. heapq<br/>
<h2>Problem Definition</h2>
This project seeks to optimise data packet routing paths from either of two base stations to any of the 100 vehicles on the given motorway network with limited Internet access. The primary challenge is to ensure reliable and efficient Internet connectivity for vehicles by utilising neighboring cars as relay nodes, since they all do not have a direct link to the base stations. The solution requires finding routing paths that maximize end-to-end data transmission rates while minimising latency which will form the optimal routing path while taking into cognisance the constraint that the route must have a link with either base station.<br />
<h2>Key Metrics</h2>
End-to-End Data Transmission Rate: Defined as the minimum transmission rate among all links in the routing path.
End-to-End Latency: Comprises the sum of delays imposed by each link in the path. <br/>
<h2>Network Description</h2>
Two base stations (BS-1 and BS-2) are positioned at coordinates (-1, -1) and (56325, 9) respectively.
A link's transmission rate is determined by the distance between communicating cars, as specified in Table 1. A distance exceeding 6000 meters results in no connection (transmission rate = 0).
 <br/>
<h2>Optimisation Objectives</h2>
Find routing paths for each car to access either BS-1 or BS-2, maximizing end-to-end data transmission rate and minimising end-to-end latency.
 <br/>
<h2>Constraints</h2>
The chosen path must consist of feasible links based on distance limitations.
The path must link to either of the base stations
 <br/>
 <h2>Deliverables</h2>
1.Optimal routing paths for each car to reach either BS-1 or BS-2. <br/>
2.End-to-end data transmission rates and latencies for each path.
 <br/>
<h1>Methodology</h1>
<h2>Data Collection</h2>
The required data was provided which included car id and coordinates of base stations and the cars. This coordinates helps to determine the location of the cars.
<h2>Data Processing</h2>
1. <b>Car Distance:</b> Calculate the distance between all the cars in the network including their distance from the base station <br/>
2. <b>Transmission rate:</b> Based on the distance, the transmission rate between a car and other cars is determined using the following chart. 
<p align="center">
<img src="https://github.com/yasemxn/Search-and-Optimisation/blob/main/assets/table.png"/>

The transmission rate will determine whether there can be transmission between two cars.
3. <b>Network Topology: </b> This is a visual representation of transmission flows in the network constructed using the transmission rate.

<h2>Algorithm Selection</h2>

<b>Dijk's Optimisation: </b> <br/>
1. Mark the initial point (source node) as 0 while setting other points as infinity.<br/>
2. From the source node, identify the neighbours, then assign the values of their transmission rate to replace the infinity earlier set only for those neighbours.<br/>
3. The next node will be the node with the least transmission from the source, for this node, the neighbours will be identified and their values will be the cumulation of rates from the source through the parent node and from its parent node to itself. The rates are recorded. This is repeated for other neighbouring nodes from the source. If a node has been passed through before, if the value of the new route is greater than the older value, it is discarded, however, if it is less, it will be the new transmission for the route.<br/>
4. Steps 2 and 3 are repeated for other nodes until the source nodes gets to the destination node which is either of the base station. <br/>

<b>Genetic Algorithm (GA): </b> <br/>
1. <b> Individual Represantation: </b> Define a class Individual representing an individual in the population and calculate fitness i.e Minimum Transmission rate.<br/>
2. <b> Population Initialisation: </b> Each individual's path is randomly generated until it reaches one of the base stations. Discard paths that do not reach any of the target nodes.<br/>
3. <b> Genetic Algorithm Loop: </b> Execute the genetic algorithm loop for a specified number of generations.<br/>
4. <b> Crossover Operation: </b> Perform crossover by taking half of the path from the fittest individual and assigning it to other individuals in the population.<br/>
5. <b> Mutation Operation: </b> Apply mutation by randomly changing one node in the path of each individual.<br/>
6. <b> Sort Population: </b> Sort the population again based on fitness values after crossover and mutation.<br/>
7. <b> Select Best Population: </b> Identify the best path and maximum transmission rate from the fittest individual in the final population.<br/>
8. <b> Run the Genetic Algorithm </b> Execute the genetic algorithm by calling the _genetic_algorithm_ function with specified parameters for population size and number of generations.<br/>


