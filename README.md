Introduction:
In the era of computers and technology, we have seen many extraordinary new apps. Coding and programming have become a dominant industry, and many developers have come up with exceptional forms of entertainment which include game development. Modern games have become very spectacular and as aspiring young coders, we wanted to explore the field of game production. Snake and Ladder is a very popular game that is played by both children and adults. So, we decided to make a snake and ladder game which adds some new features to this well-known board game. Our game has many interesting new features which we will be discussing later in the report. We will also calculate the complexities and discuss the game structure.

Problem Definition:
Snake and ladder is a multiplayer game. The objective of the game is for players to keep rolling the dice until they reach the last tile to win the game. The first player to reach the last tile on the board wins. This game is buit on the luck of getting a number number. So, a random function needed for rolling the dice was needed. It is games like snake and ladder that has the concept of randomness that lead to the creation of the random library. The players dont make any decisions in the game and the payers move on the board based on the random roll that they get. It is an entertainig and thrilling family game. 

Methodology:
At the start, we tried to implement the snake and ladder game using vectors instead of weighted directed graphs. However, vectors dont make use of the advanced search algorithm like Breadth first search. Moreover, graphs would feel more natural to implement in a board game. Each tile on the board represent a vertex in the graph and the connection between two tiles on the graph is represented using edges. If a tile is normal, then the weight will be 1. If a tile is a snake, then the destination will be less than the current tile position. If a tile is a ladder, then the destination will be more than the current tile position. The edge gives us the distance between any two tiles in a graph as well as the direction of motion from each tile since it is a directed graph.

Analysis of the algoritms used:
We have the Breadth first search algorithm. This algorithm is used in order to find the shortest path to win on the board from the tile you are currently standing on. In snake and ladders, this means outputting to the user the luckiest series of moves that he needs in order to win the game in the least number of moves every time he rolls the dice. Forexample, if the user is on tile 60 and there is a tile 65 that takes him to 91, then his luckiest path would be 65->91->97->100. luckiest path would be rolling a 2 since it would make him instantly win. Another important algorithm or rather function that we used is the distribution function. Distribution function has a more random seeding than the srand function which uses time seeding. This is because, it works in union with the computer storage memory locations which are completely randomised everytime we boot up the computer. If we use srand and time seeding, we would start to get patters even though it should be a random result.

Implementation and Features:
We implemented the game using the graph data structures and algorithms. In most normal snake and ladder games, the board is generated with snakes and ladders being placed in certain fixed positions every time the game is run. In our game, the snakes and ladders are placed randomly every time the game is run. Moreover, we allow the user to define the size of the board as well as the difficulty of the game. As the difficulty level increases, the number of snakes increases. Another feature of the game is that each time a user rolls a 6, he gets to play again. However, there is only a max of 3 moves that he can do in one turn. If he rolls 6 three times in a row, then he can only move 2 times each time he moves 6 positions. If he 6 twice in a row then rolls any number other than 6, then he can move three times in a row. As for the actual implementation of the graph, we decided to use the adjacency list, which shows the adjacency of various vertices in the graph, instead of an adjacency matrix.

Data Specifications:
Although the game board is randomely generated, we still need some input from the user in order to create the board. The first input needed is the size of the board. The user enters the number and columns that he wants to play the game on. This input is taken from the user which is passed to the generate board function. It specifies the rows and columns for the board. We also take as input the difficulty that the user wants to play on. The harder the game, the more the snakes and ladders that will be placed on the board. Another input is the number of players that will play the game. This is used to know how many players we will push in the queue at the start of the game. The queue is used to see which player is going to roll the dice and move in the currect turn. 

Experimental result:
There may be ways that the user input might break the game. For instance, when we entered the size of the board to be very large like 10000 tiles, the game broke and didnt run since the board was way too large to display. Therefore, we limited the number of rows and columns to only be between 5 and 20 inclusive. when we made the board have 5 rows and 5 columns, then the game ended very fast in the minimum number of moves being       . However, if the user makes the board to have 20 rows and 20 columns, then the game would take much longer to end than the 5 by 5 board, and would needed a minimum number of moves of       based on difficulty level set to 50 in both cases. Moreover, if the difficulty is set to be 0, then the board would only be ladders and snakes, incresing the probability of the game having a cycle making it impossible to win the game. if the difficulty is set to be 100, then the board would only be normal tiles with no snake and ladders at all. So, we made 3 custom difficulties, easy, medium and hard with each having a fixed 'NormalTilePercentage'. This would ensure that the game wont break. When we ran the game on difficulty set to 0, 
 
Adjacency List vs Adjacency Matrix:

Snakes and Ladders, a game of chance and colorful squares, might seem like a simple childhood pastime. But beneath its playful facade lies a fascinating connection to the world of graphs and data structures. When representing this game as a graph, the choice between an adjacency list and an adjacency matrix becomes crucial. While both can technically work, the adjacency list shines brighter for several compelling reasons:

1. Sparse Graph:
 Unlike a typical grid-based game, Snakes and Ladders boasts a sparse graph. Many squares have no direct connections to others since each tile would only have 1 destination. An adjacency matrix, with its fixed size for all squares, becomes inefficient. It wastes space storing zeros for non-existent connections, bloating memory usage. The adjacency list, however, thrives on sparsity. It stores only the actual connections for each tile, creating a compact and memory-friendly graph representation. In the game we developed, we allow the user to generate a new board every time the game is run. This is a very expensive process since it essentially rebuilds the entire graph. Now imagine we are going to build a 10 by 10 board. This means that the game will have 100 tiles. In an adjacency matrix, we are going to store a fixed 1000, which is 100, squared new entries every time we generate a new board. However, in an adjacency list, we are going to only store 100 new values since each node will only have 1 connection to another node.

2. Graph Traversal:
 Searching the graph for possible moves is a core operation in Snakes and Ladders. An adjacency list excels here. Every tile in the game would essentially have only one destination. In an adjacency matrix, searching involves scanning the entire row, potentially wasting time on irrelevant squares, especially for sparse boards. It would be required to check the relationship between the current tile and every other tile in the game. This can hamper the performance of algorithms like finding the luckiest path to win the game. However, with an adjacency list, there will be no searching involved since each tile in the list will only point to one other tile which is its destination. So, the complexity of using an adjacency matrix would be O(n), while the complexity of using an adjacency list would be O(1). This makes the game run faster and way more efficiently.

In conclusion, while both adjacency list and matrix can represent a Snakes and Ladders graph, the list reigns supreme for its memory efficiency as well as graph traversal efficiency.

Edge Class:

This class defines the edges between any 2 nodes in the directed graph. It has 3 private variables. "u" which is the position of the current node, "v" which is the destination from the current tile which the edge points to, and "w" which is the weight of the edge. It is the distance between the 2 nodes that has edges between them. It is also of type weightType which ensures that the weight will be negative. There are also two overloaded operators which are the "<" and the "<=" operators. They allow for the comparision between the weights of the two edges.

Dice Class:

In this class, there are no class variables. We only have the constructor and the "roll" function. Both of them take no parameters. For the constructor, it seeds the random number generator with the current time using std::srand(std::time(0)). The "roll" function returns a random number between 1 and 6 inclusive which is the same as a real dice. The roll function has the complexity O(1). The dice class is resposible for rolling the dice for the players in the game. The number that gets rolled is the number of positions that the player is going to move on the board.

Players class:

This class is responsible for the players' movements. It has three private variables. Position stores the tile number of the player. Name stores the name of the player. Sixcounter stores the number of times a player rolls a 6 consequently. The overloaded constructor takes name of the player as a parameter and assigns it to the variable 'Name'. It also assigns 1 to the variable 'position' since every player would start the game at tile number 1. Now lets move on to the public functions. 

The first function is Rolldice. It takes 2 parameters, one of the type board class and another one which is passed bu reference and has the type int. Roll dice function returns a boolean variable. The function first intialises 2 varibales. One has the type Dice class and is named v, and another variable has type int named result. The then calls the roll function from the dice class, which as stated before generates a random number between 1 and 6, and stores the result in result variable. We then check if the function roll returned 6. If yes, we inctrement the 'sixcounter' private variable otherwise, we make 'sixcounter' equal 0 since sixcounter only stores the number of times 6 has been rolled consequently. Next, we check if 'sixcounter' is not equal to 3. If it is equal to 3, we make 'result' equal to 0 since the game does not allow a player to move 6 positions 3 times consequently. If it is not equal to 3, we check if the sum of 'position' and result is less than or equal to the size of the board which the function gets using the 'getsize' function stored in the board class. If the condition is true, the function updates the 'position' variable by adding the dice roll stored in 'result' variable to the current position of the player stored in the 'position' variable. If the condition is false, the function outpots a message to the user telling him that he has overshot so he cannot move this turn. It also tells the player by how much he has overshot the dice, and returns false since the player won't move this turn. If the roll was valid, the function outputs the roll number the user got and returns true indicating that the user can play his roll this turn.

We also have two getter function and one setter function. The setter function is 'updatepos' which is a void function that takes as parameter the new position of the current player and changes the current position of the current player. Next is the getter function 'getname' which returns the name of the player, and the getter function 'Getpos' which returns the current position of the current player.

The last function and certainly the most important function of the Player class is 'Play' which takes a parameter of the type board class. Play has two variables, input and rollnum. At the start, the function asks the user if he wants to roll the dice or not. It stores his input in the variable input. It then compares 'input' to 1 and if input stores the integer 1, then th function play calls another function in the 'Play' class called Rolldice. Rolldice takes two parameters and returns a boolean variable in the variable 'torf' to indicate whether or not the dice has been rolled. It also stores the number which was rolled in the rollnum variable. The function then checks whether or not 'torf' is true. If yes, it enters another if statement. This if statement calls the function 'findEdgeByU' which is in board class and takes the player's current position on the board as a parameter. 'findEdgeByU' returns an edge and the condition statment checks if the weight of this edge is 1 or not. If it is 1 then the player is on a normal tile. So, the function then checks if the 'rollnum' is equal to 0. If yes, then the function outputs to the user that he has rolled 6 3 times in a row so he can't play the last 6 he rolled. If no, then it outputs to the user the new tile that he has moved to. Going back to the original condition, if the weight of the edge not 1, then the player is not on a normal tile. So, the function checks if the player is on a ladder by checking if the destination of the tile he is currently on has a larger value than the tile he is currently on. If yes, the function changes his current position to the position stored in the destination variable of the edge. The function then outputs to the player his old position, the fact that he has moved up a ladder, and the new position he is currently on. If this condition is false, then the player must be on a snake. The function changes his current position to the position stored in the destination variable of the edge. It then outputs to the player his old position, the fact that he has moved down a snake, and the new position he is currently on. The function then checks if the player has won by comparing the size of the board retrieved using the 'getsize' function to the player's new position. If they are equal, it returns 66 indicating that the player has won the game. If the condition is false, then the function returns the number of the dice roll of the player.

Board Class:
This class is resposible for generating the board on which the players play. It has 2 contants of type integer, Vmax and Emax. Vmax sets the maximum size of the board and Emax calculates the maximum number of edges that can be in the board. We also have the struct tile. It has the three variables pos, destination and type. 'Pos' stores the number of the tile on the board. 'destination' stores the tile that can be reached from a tile. 'type' stores whether a tile is a normal tile, a snake or a ladder. There is also an overloaded constructor which assigns the values for the 3 variables. 

There are a total of 12 private variables in the class.

'V': Stores the number of edges and is of type integer.
'edges': It is a vector of type class Edge. It stores all the edges of the graph that makes up the board.
'map': It is an array of the type list and is used to store the adjacency list. It has the size of Vmax which is the maximum number of vertices in the graph.
'distance':
'via':
'processed':
'order': 
'val':
'visited':
'path':
'rows_': Stores the number of rows generated on the board.
'columns_': Stores the number of columns generated on the board.
'NORMAL_TILE_PERCENTAGE': It is an integer which is used to set the difficulty of the game. The higher the value the easier the game.
'LaddertosnakeRatio': The higher the ratio, the more likely it is to generate a ladder instead of a snake.

Now we will start discussing the functions. 
The first function is the 'generateBoard' function. It takes two parameters as input which are the number of rows and the number of columns. It then assigns them to their corresponding private variables. We then created a random device which will be used later for the generation of the tile types. We then use two for loops in order to visit each tile on the board that will be created. Then, using the random distribution function and 'gen', we generate a random number between 0 and 99 and store it in 'random percentage'. We then check if the random number we got is less than the 'NORMAL_TILE_PERCENTAGE' which is a percentage set earlier in order for the use to define the game difficulty. If yes, then we make the tile we are currently on a normal tile with no snakes or ladders. We connect it to the tile immediately after it and use the 'addedge' function to add the new edge created between them in the edge vector. The edge will have its start position as the current tile position which is stored in 'count', and the destination as the other tile that the current tile is connected to. Now, if the random number we got at the start not less than the 'NORMAL_TILE_PERCENTAGE', we compare the 'random percentage' to the sum of 'NORMAL_TILE_PERCENTAGE' and (100-'NORMAL_TILE_PERCENTAGE) times 'LaddertosnakeRatio'. This is our way of checking whether to place a snake or a ladder. The higher the 'LaddertosnakeRatio', the more probable it is to get a ladder. If the condition is false, we place a ladder on the current tile. Since ladders take you upwards or forward, we will generate a random number between the current tile number we are on and the max size of the board to ensure this ladder next destination will be forward or upwards but never downwards or backwards. If the condition is true, we place a snake on the current tile. Since snakes take you backward or downward, we will generate a random number between 1 and the current tile number we are on to ensure this snake next destination will be backward or downward but never forward or upward. In both conditions, we store the new random number in 'randint' varibale. Now, we check if we are at the last vertix. If so, we add an edge whose destination is same as its position with zero weight. Since there will be nowhere else to go. If this condition is false, we calculate the weight using an absolute function since the weights cant be negative. Then, we generate a new edge using 'addedge' function with the current position, destination and EDGE_WEIGHT as parameters. At the end of the inside loop, we increment 'count' to go to the next tile on the board. At the very end of the function, we call the 'boardfixer' function which ensures that there is no more than 6 snakes in a row. 

We also have another function which generates a random number for both the rows and columns, then calls the generate board function with the random number of rows and columns as parameters.


Conclusion.
