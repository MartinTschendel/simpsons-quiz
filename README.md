# simpsons-quiz
small fill in the blanks quiz, written in python

these are my first steps on GitHub, let's see how dar I can go:)

--------
## How to start the code

This code should be started with a command line, like Git Bash.<br>
You can save this code in a python file (`py`) on your computer.<br>
Then you move to the folder where you stored this file.<br><br>

These commands might be helpful, this [webpage](https://www.digitalcitizen.life/command-prompt-how-use-basic-commands) contains further infor:<br>
* see the current directory, in which you are located (print working directory): `pwd`
* change the directory (eg from c to d): `cd /d`
* move back up to a higher-level folder: `cd ..`
* open a folder: `cd + folder-name`
* get all files listed, what are stored within a folder: `ls` or `dir` 
* start the `py` file: `winpty python + filename`
* create new directory: `mkdir + directory-name`

--------
## Main parts of the code
The code consists of four main parts:
### Request to choose a level
```
#This function prompts the user choose a level (easy, medium or hard).
#The output of the function is the defined variable 'sublist', what selects
#the respective part of the lists defined above, according to the chosen level.
#In addition, the respective test ('easy_test', 'medium_test', 'hard_test') will be printed out.
#If the user input is not equal to the strings 'easy', 'medium' or 'hard',
#the user will be asked again to choose a level.
def determination_level():
    level = raw_input("Please choose a game difficulty: easy, medium, hard -->")
    if level == "easy":
        print "You have chosen the level 'easy'.\n\n" + easy_test
        sublist = 0
        play_game(list_answers_test, sublist)
    elif level == "medium":
        print "You have chosen the level 'medium'.\n\n" + medium_test
        sublist = 1
        play_game(list_answers_test, sublist)
    elif level == "hard":
        print "You have chosen the level 'hard'.\n\n" + hard_test
        sublist = 2
        play_game(list_answers_test, sublist)
    else:
        print "Wrong input!"
        determination_level()
determination_level()
```

### Playing the game
```
#This function loops through right or wrong answers of a given question
#and prints if it was correct or not. The first input of this function is the argument 'list_answers_test',
#what is required to check whether the user input is correct. The second input of the function is the argument
#'sublist', what is related to the respective level chosen by the user. This argument 'sublist' helps to
#take the correct sublists in the lists defined above. The output of this function depends on the user input:
#If the input corresponds to the content of list_answers_test, then the output will be the information
#that the answer is correct and the loop function will ask the user to answer the next question in the test
#until all questions are answered correctly. Before the user starts to answer the questions,
#he/she is also asked to define the number (integer) of tries needed (variable 'credit'). In this loop function,
#this number will be substracted by one with every wrong answer. As soon as the variable 'credit' becomes zero, the string
#'Game over!' will be printed out and the program finishes.
def play_game(list_answers_test, sublist):
    blank = 0
    credit = int(raw_input("How many tries do you need? Type in a number! -->"))
    while blank < len(list_answers_test[sublist]) and credit > 0:
        user_input = raw_input("Your answer to ___"+str(blank+1)+"___? -->")
        if user_input == list_answers_test[sublist][blank]:
            print "Your answer is correct!"
            fill_test(sublist, blank)
            blank += 1
            if blank == len(list_answers_test[sublist]) and credit > 0:
                print "You won!:-)"
        else:
            credit = credit - 1
            print "Wrong answer!"
            if credit == 0:
                print "Game over!"
            else:
                print "You still have "+str(credit)+" tries left. Try again!"
```


### Filling the blanks of the text
```
#This function fills the blanks of the test, depending on the level the user chooses. It takes as input the argument
#'sublist', what is related to the respective level chosen by the user. This argument 'sublist' helps to
#take the correct sublists in the lists defined above. This function uses a second argument as input: 'blank'.
#This argument relates to required elements in the lists defined above.
#The output of this function is a new string with the content of the easy, medium or hard test,
#where the current blanks have been substituted with the correct answers.
def fill_test(sublist, blank):
    if sublist == 0:
        list_of_easy_test[positions_test[sublist][blank]] = list_answers_test[sublist][blank]
        easy_test = ' '.join(list_of_easy_test)
        print easy_test
    elif sublist == 1:
        list_of_medium_test[positions_test[sublist][blank]] = list_answers_test[sublist][blank]
        medium_test = ' '.join(list_of_medium_test)
        print medium_test
    elif sublist == 2:
        list_of_hard_test[positions_test[sublist][blank]] = list_answers_test[sublist][blank]
        hard_test = ' '.join(list_of_hard_test)
        print hard_test
 ```

### Different strings and lists of the quiz
```
#This is the content of the easy test. It will be displayed if the user chooses the easy level:
easy_test = '''The Simpsons is an animated sitcom created by ___1___ .
The father of the family is called ___2___ and the mother's name is ___3___ .
Both have a naughty son who is called ___4___ .\n'''
#This inbuilt function splits the string easy_test into a list of separated elements:
list_of_easy_test = easy_test.split()

#This is the content of the medium test. It will be displayed if the user chooses the medium level:
medium_test = '''The Simpsons live in a city called ___1___ .
Homer works in a ___2___ and Marge cares for her family as a ___3___ .
The boss of Homer is Mr. ___4___ , a very rich person .\n'''
#This inbuilt function splits the string medium_test into a list of separated elements:
list_of_medium_test = medium_test.split()

#This is the content of the hard test. It will be displayed if the user chooses the hard level:
hard_test = '''Let us talk a bit more about other characters in The Simpsons .
The Kwik-E-Mart is definitely the most popular convenient store in Springfield .
The proprietor's family name is really difficult, but everybody only uses his
given name ___1___ . If somebody wants to rob his store, he might call Chief
___2___ for help. The Chief has a son called ___3___ , who is a classmate
of Bart's sister ___4___ .\n'''
#This inbuilt function splits the string hard_test into a list of separated elements:
list_of_hard_test = hard_test.split()

#This list contains the correct answers in the three different tests, divided into three respective sublists:
list_answers_test = [['Matt Groening', 'Homer', 'Marge', 'Bart'],
                    ['Springfield', 'nuclear power plant', 'housewife', 'Burns'],
                    ['Apu', 'Wiggum', 'Ralph', 'Lisa']]
```
