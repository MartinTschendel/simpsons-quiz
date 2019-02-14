# simpsons-quiz
small fill in the blanks quiz, written in python

these are my first steps on GitHub, let's see how dar I can go:)

--------
## How to start the code

This code should be started with a command line, like Git Bash.<br>
You can save this code in a python file (`py`) on your computer.<br>
Then you move to the folder where you stored this file.<br><br>

These commands might be helpful:<br>
* see the current directory, in which you are located (print working directory): `pwd`
* change the directory (eg from c to d): `cd /d`
* move back up to a higher-level folder: `cd ..`
* open a folder: `cd + folder-name`
* get all files listed, what are stored within a folder: `ls`
* start the `py` file: `winpty python + filename`

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



