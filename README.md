# Mastermind

In this assignment, you are required to programm a multi-threaded Mastermind game. Mastermind  
game has a lot of variations, in our variation we will use 4 digit numbers.  
Aim of the game is to guess a hidden number with the least number of trials. The player (which is your  
application) will start guessing number with an initial try. When the try is made, depending on the  
number of write or wrong placed digits, the result of the guess is displayed. The result is in the form of  
x W y C where x represents the number of digits in the hidden number where the location of the digits  
are wrong, and y represents the number of digits in the hidden number where the location of the digits  
are correct. For example if the hidden number is 4019 and the guess is 1054 the result will be 2 W 1 C  
since 0 is located right and 4 and 1 are located wrong. The player then asseses this result and makes  
another guess until the result is 4 C.  
In your application the computer will be a player and try to guess the number. Your application will  
follow an algorithm to find the number. While doing this, the application will use at least two worker  
threads. The threads will work in parallel to find a good guess. Let's first discuss the algorithm:  
1. Start with a random number 0123 might be an example. Note the outcome.  
2. Depending on the number of right and wrong guessed digits, try another random number. For  
example 4567 might be the second guess.  
3. After these two steps you can either do another guess like 89XX or start running the guess routine.  
4. The guess routine works like this:  
• A new candidate is selected (you can use a simple loop to select numbers)  
• If the candidate gives the same outcomes as the previous guesses, it becomes the next guess.  
Otherwise a new candidate is selected.  
  
 Example:  
Suppose the hidden number 7085.  
The algorithm will make the first guess as 0123. The outcome will be 1 W.  
The algorithm than make another guess as 4567. The outcome will be 2 W.  
Now, the algorithm will try to find another number that gives the same outcome as the first and second  
guess.  
For example if we pick 8901 as our candidate, applying 0123 to 8901 will give 2 W. So we cannot  
consider 8901 as our next guess.  
If we pick 3789 as our candidate, applying 0123 to 3789 will give 1 W. So it satisfies the first check. In  
the second check, applying 4567 to 3789 will give 1 W. However we are looking for 2W as outcome.  
So we cannot pick that as our next guess either.  
If our candidate is 5916, it gives 1W and 2W when we apply it into 0123 and 4567. So 5916 can be our  
next guess.  
Here we what you can modify in the algorithm (optional):  
1. You can increase or decrease the initial random guesses. In the algorithm above, it suggests two  
guesses, you may make it 1, 3 or 4. It is up to you.  
2. You can have extra elimination techniques. In order to decrease your search space, you can use extra  
data structures to eliminate some numbers, or ranges. This might decrease the number of trials when  
making a guess. However, the memory operations may increase the computation time, if the threads  
need to wait for each other, during the data structure lookups and updates.  
Besides modifying the algorithm, you can also modify the number of threads. Experiment with the  
number of threads to see, which number gives you the best performance. When you create threads you  
should give different candidate ranges so that they can work in parallel. You should have a global  
counter that counts the number of trials for each candidate. Your aim should be minimize this number  
as well. When a thread finds a guess, it should immediately stop the other threads and make the guess.  
Your program will accept the hidden number from the user. Then start generating the guess numbers  
until the hidden number is found. Here is a sample output:  
Enter the hidden number: 4903  
Guess 1: 0123  
Guess 2: 4567  
Guess 3: 8935  
Guess 4: 4031  
Guess 5: 4903  
Found in 5 guess in 3494 tries.  
  
