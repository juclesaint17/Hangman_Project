# Hangman_Project

Milestone 1:

- The hangman project is a computer game, and in the game the program choose randomnly a name in the list of given names and the user is prompt to guess letters containing in the secret word.If the user find the correct match of the word,the user wins otherwise the user loose.At each iteration when the user select an incorrect letter ,the user number of lives is reduced by one and the visual display of Hangman is displayed.

- This project "HANGMAN" is build using Python3 programming language and developped using Visual Studio Code IDE. Jupyter notebook was used as well to test some blocks of codes functionality.
- In Milestone 1,one fuction was built:
- - 'ask_letter(self)': This function ask the user or player to guess a letter using a pyhton3 INPUT() function;and the letter must meet some requirements built inside the function. For example the letter must be a single letter only, not a number.Another programming complexity with this fuction is that it will check the user input to check if the the chosen letter was already tried and ask the user to choose another letter.
- the code below illustrate the ask_letter function:
- ------------------------------------------------------------------------------------------------------------------------


        def ask_letter(self):
        
        # ask the user to enter a letter 
        while True:

            print("Guess a letter !")
            letter = input()
            letter =letter.lower()
            len(letter)==1
            try:

                if len(letter) >1:
                    print("Please just enter a single letter")
        
                    print("You enter an incorrect format")

                elif letter in self.list_letters:

                    print("The letter: {}, was already tried".format(letter.upper()))
                elif letter not in 'abcdefghejklmnopqrstuvwxyz':
                    
                    print('Please do not use numbers.Try again...')
            
                else:
                
                    break
            except:
                print("Please try again")

        self.list_letters.append(letter)
        print("List of gueussed letters:", self.list_letters)
        self.check_letter(letter) 
        -----------------------------------------------------------------------
        
- Milestone 2:


      ----------------------------------------------------------------------------------------------------
      In this Milestone we defined and initialize the attributes.
      
       def __init__(self, word_list, num_lives=5):
        
        #list containing words to be picked randomly
       
        self.word_list =[]

        #generate the word randomnly from the wordlist 
        self.word = random.choice(word_list)

        # the list containing the number of letters the word choosed randomnly has
        self.word_guessed = ['_'] * len(self.word)
         #
        self.num_letter = len(set(self.word))

        #the number of lives the user will have during the game
        self.num_lives = num_lives

        #empty list to check if the letter exists
        self.list_letters =[]

        #initializing a variable that pick randomly the position of the word  in the list.

        #retrieving the word picked randomly from the list and assign it to a string variable for processing.

        #print out the number of charactes that the word picked randomly from the world_list has.
        print("The mystery word has",len(self.word),"characters")
        print()


        #print(' '.join(self.word_guessed))
        print(self.word_guessed)
        #self.num_letters = len(self.word)
-----------------------------------------------------------------------------------------------------------
      This block of code above shows how the attributes were initialized. Let us look at 'self.list_letters' attribute. The attribute is connected with Mileston1. When the user input the letter, the letter is stored inside it, and when the second input is submitted by the user,the program check that input againt the 'self.list_letter' to see if the letter was already tried.If it was tried, the user is asked to choose another letter and it is a continious loop till the user meet the condition of the function defined.

- Milestone 3:

In this Milestone, the Check_letter() function is defined. In this function, the system checked if the letter selected by ther user exist inside the selected word,and if the letter exist,the letter is saved to the 'word_guessed attribute that was initialized in 'milestone 2'. We used 'enumerate()' function to check and append the letter at the same index and display the number of correct letters in the word not guessed yet.If the letter is not in the word, the attribute'num_lives'the number of lives the user is given is reduice by 1,and the Hangman graphic is displayed on the screen.
the code below illustrate the check_letter function and the second is the output of the running code.

-------------Function Check_letter()-------------.

def check_letter(self, letter) -> None:

      
    

        # if the letter is in the word, the word is placed at a specific corresponding index in the word

        if letter in self.word:
            for index, letters in enumerate(self.word):
                
                if letters == letter:
                
                    self.word_guessed[index] = letter  

            self.num_letter-=1   
            print("Correct guess, the guessed letter  {} is in the word".format(letter)) 
            print()
            print("Total number of unique letters not gueussed is: ", self.num_letter)
            print()
            #print(' '.join(self.word_guessed))
            print(self.word_guessed)
        else:
           # if guess not in word the number of the lives is reduice by 1 and the Hangman graphic is displayed
           print("Ops...Wrong guess!!!...")
           print()
           self.num_lives-=1 
           # call the diplay method to display the hangman pics
           self.display(self.num_lives)   
           print()
           print("You have {} lives remaining".format(self.num_lives)) 

        ---------------------------------------------------------------------------------
        --------------------------Code 2:Check_letter() output-----------------------------
        
               HANGMAN
The mystery word has 6 characters.

['_', '_', '_', '_', '_', '_']
Guess a letter !.
x
List of gueussed letters: ['x']
Ops...Wrong guess!!!...


                    
                ------   
                |    |
                |    o
                |    |
                |     

                    

Pending lives 0.
Pending lives 1.
Pending lives 2.
Pending lives 3.

You have 4 lives remaining
Guess a letter !
b
List of gueussed letters: ['x', 'b']
Ops...Wrong guess!!!...


                    
                ------   
                |    |
                |    o
                |   -|
                |     

                    

Pending lives 0
Pending lives 1
Pending lives 2

You have 3 lives remaining
Guess a letter !
r
List of gueussed letters: ['x', 'b', 'r']
Correct guess, the guessed letter  r is in the word

Total number of unique letters not gueussed is:  5

['_', 'r', '_', '_', '_', '_']
Guess a letter !

----------------------------------------------------------------------------

- Milestone 4:
- In this last part of the Hangman game another function was added. A function to display the HAngman picture when the guessed letter is not in the secret word, for this, we created a constant attribute called HANGMAN_PICS  and defined the function called 'Display()'. The Display() will print out on the screen the hangman pics.For example if the user enter a wrong guess the Hangman_pics will display an hanging man with one hand and so forth..
- the code bellow illustrate the Display function.
- ------------------------------- Display()---------------------------------.
- 
 def display(self,num_lives):

        # display the hangman part if guess letter not i the word by reducing the number of lives by 1.
        print(HANGMAN_PIC[self.num_lives])
        print()

        for i in range(self.num_lives):
            print("Pending lives",i, end='')
            print()
  -------------------------------------------------------------------------------------------------------------------

     


