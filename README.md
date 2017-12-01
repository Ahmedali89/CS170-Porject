# CS170-Porject
CS170 Project Part II 

We used the SAT4J library in this project. It is “the boolean satisfaction and optimisation library in Java.” There is a jar file in the folder and it should work fine if the folder is important into IntelliJ. We decided to use this library because our approach was to create 3sat clauses using the list of wizards as well as the constraints, this allowed us to then use SAT4J  to solve them.

How to use SAT4J(Download & Installation):
•	First download SAT4j from http://www.sat4j.org/ ,and it will come as a zip file.
•	Create a project in IntelliJ.
•	Unzip the SAT4j and place the resultant folder inside the intelliJ project you just created.
•	In intelliJ add the SAT4j folder as part of your library. You can do that by open file then go to project structure. Then add libraries and hit (+) sign to add the SAT4j.
•	Now import the solver.java file into the project.
•	To run a file, you need to have the file inside src folder in the intelliJ project.
•	Every time you want to process folder just do the pervious step and change the name of the folder in the main function manually.  

The high level idea of our approach is as follows: 
•	Each time we read an input file, we use the readingFile method which convert all the constraints in the input file into an Arraylist of String[ ] of constraints.

•	Next, we use the randomOrdering routine to generate a random ordering of the wizards and also assigns each wizard to a unique integer ID. 

•	We then use the bigMap method to force a particular ordering for the wizards by building inequality statements such as (wizard A < wizard B). 

•	We then map these statements to a unique integers which the Sat4j uses to solve the problem. The reason we do this is because the Sat4j library takes in statements of integers such as “[2 9 3] [3 4]” where each integer within one of these clauses maps to a condition such as “wizard 3 < wizard 6”. 

•	We use generateClausesofTwo to generate SAT clauses of two numbers such as “[7 2]”, and we use generateClausesofThree to generate SAT clauses of three numbers such as “[7 9 4]”. The reason we do this is because the SAT4j Solver. 

•	If the given clauses is deemed solvable by the solver, we can then process the output by first calling the processing method on the model, which essentially just does the post processing after the Sat4j solver solves all the statements(sat clauses) and gives the orderings. This is done by building a graph of all the wizards in the form of an adjacency list that we built with a hashmap. Each key in the hashmap is a wizard, and the list attached to that key is all the wizards that are older than itself. In other words, processing generates an adjacency list graph that denotes the dependencies, or “smaller than” relationships between all the wizards. For example, the key that has an empty list as the item would be they key that denotes the oldest wizard, and the key that does not appear in the adjacency lists of any other key is the youngest wizard. 

•	This map/graph is then fed into the figuringOrdering method which uses the dependencies from the graph to generate the appropriate ordering out by sorting each key from the graph/map by the size of its adjacency list. 
Note:
Our code could solve up to 180 optimally, but not 200 as a result we made a random ordering for the file from 200-400 and that why we use WriteRandomOrdering to the write those file. 








