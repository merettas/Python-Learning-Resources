## **2.Rock-Paper-Scissors Game**

## **What is Rock-Paper-Scissors Game?**

Rock paper scissors is a hand game, usually played between two people, in which each player simultaneously forms one of three shapes with an outstretched hand. These shapes are "rock" (a closed fist), "paper" (a flat hand), and "scissors" (a fist with the index finger and middle finger extended, forming a V).  It has only two possible outcomes: a draw, or a win for one player and a loss for the other. A player who decides to play rock will beat another player who has chosen scissors ("rock crushes scissors" or sometimes "blunts scissors"), but will lose to one who has played paper ("paper covers rock"); a play of paper will lose to a play of scissors ("scissors cuts paper"). If both players choose the same shape, the game is tied and is usually immediately replayed to break the tie.

## **Source Code**

### **main.py**
```py
import random
from graphic_view import *
from intro import *
from count import *

def try_again():
    decision = input("Do you want to try again? (Yes/No): ").lower()
    if decision == "y" or decision == "yes":
        print('''
__________________________________________________________________________________________________________________________
        
                                                New Game
                                        ''')
        main()
    elif decision == "n" or decision == "no":
        print("\n*************************************************************************************************************************")
        exit()
    else:
        try_again()

intro()
trial = 3
Pscore = 0
Cscore = 0
def main():
    global Pscore
    global Cscore
    global trial
    if trial >= 1 and (Pscore != 2 and Cscore !=2):
        num = random.randint(1,3)
        print('''__________________________________________________________________________________________________________________________        
Chances Left: ''',trial)
        player = int(input("Enter the number of the shape: "))
        count()
        if num == player:
            print(Tied[player])
            main()
        elif num == 1 and player == 2:
            print(PlayerWins[player])
            Pscore+=1
            trial-=1
            main()
        elif num == 1 and player == 3:
            print(ComputerWins[num])
            Cscore+=1
            trial-=1
            main()
        elif num == 2 and player == 1:
            print(ComputerWins[num])
            Cscore+=1
            trial-=1
            main()
        elif num == 2 and player == 3:
            print(PlayerWins[player])
            Pscore+=1
            trial-=1
            main()
        elif num == 3 and player == 1:
            print(PlayerWins[player])
            Pscore+=1
            trial-=1
            main()
        elif num == 3 and player == 2:
            print(ComputerWins[num])
            Cscore+=1
            trial-=1
            main()
        else:
            print('''
            You have typed wrong value
            Please enter the correct value !!!
            ''')
            main()
    else:
        print(f'''
    _________________________________
    |   Computer     |    Player    |
    |________________|______________|
    |       {Cscore}        |      {Pscore}       |
    |________________|______________|  
    ''')
        if Pscore > Cscore :
            print('''
        !!! You Win The Game !!!

''')
            trial = 3
            Pscore = 0
            Cscore = 0
            try_again()
        else:
            print('''
        !!! You lost the Game !!!

''')
            trial = 3
            Pscore = 0
            Cscore = 0
            try_again()

main()
```
