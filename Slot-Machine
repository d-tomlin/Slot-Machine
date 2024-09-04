import random
import time
import os
print()
print('''Welcome to the Slot Machine 
You'll start with £50. You'll be asked if you want to play.
Answer with yes/no. you can also use y/n
There is no case sensitivity, type it however you like!
To win you must get one of the following combinations:
HAMMER\tHAMMER\tHAMMER\t\tpays\t£250
DAGGER\tDAGGER\tDAGGER/HAMMER\tpays\t£20
BOW\tBOW\tBOW/HAMMER\tpays\t£14
FIREBALL\tFIREBALL\tFIREBALL/HAMMER\tpays\t£10
SKULL\tSKULL\tSKULL\t\tpays\t£7
SKULL\tSKULL\t  -\t\tpays\t£5
SKULL\t  -\t  -\t\tpays\t£2
20\t  20\t  20\t\tpays\t The Jackpot!
''')
time.sleep(10)
#Constants:
INIT_STAKE = 50
INIT_BALANCE = 1000
ITEMS = ["SKULL", "SWORD", "FIREBALL", "BOW", "DAGGER", "HAMMER", 20]

firstWheel = None
secondWheel = None
thirdWheel = None
stake = INIT_STAKE
balance = INIT_BALANCE

def play():
    global stake, firstWheel, secondWheel, thirdWheel
    playQuestion = askPlayer()
    while(stake != 0 and playQuestion == True):
        firstWheel = spinWheel()
        secondWheel = spinWheel()
        thirdWheel = spinWheel()
        printScore()
        playQuestion = askPlayer()

def askPlayer():
    '''
    Asks the player if he wants to play again.
    expecting from the user to answer with yes, y, no or n
    No case sensitivity in the answer. yes, YeS, y, y, nO . . . all works
    '''
    global stake
    global balance
    while(True):
        os.system('cls' if os.name == 'nt' else 'clear')
        if (balance <=1):
            print ("Machine balance reset.")
            balance = 1000

        print ("The Jackpot is currently: £" + str(balance) + ".")
        answer = input("Would you like to play? Or check your money? ")
        answer = answer.lower()
        if(answer == "yes" or answer == "y"):
            return True
        elif(answer == "no" or answer == "n"):
            print("You ended the game with £" + str(stake) + " in your hand. Great job!")
            time.sleep(5)
            return False
        elif(answer == "check" or answer == "CHECK"):
            print ("You currently have £" + str(stake) + ".")
        else:
            print("Whoops! Didn't get that.")

def spinWheel():
    '''
    returns a random item from the wheel
    '''
    randomNumber = random.randint(0, 5)
    return ITEMS[randomNumber]

def printScore():
    '''
    prints the current score
    '''
    global stake, firstWheel, secondWheel, thirdWheel, balance
    if((firstWheel == "SKULL") and (secondWheel != "SKULL")):
        win = 2
        balance = balance - 2
    elif((firstWheel == "SKULL") and (secondWheel == "SKULL") and (thirdWheel != "SKULL")):
        win = 5
        balance = balance - 5
    elif((firstWheel == "SKULL") and (secondWheel == "SKULL") and (thirdWheel == "SKULL")):
        win = 7
        balance = balance - 7
    elif((firstWheel == "FIREBALL") and (secondWheel == "FIREBALL") and ((thirdWheel == "FIREBALL") or (thirdWheel == "HAMMER"))):
        win = 10
        balance = balance - 10
    elif((firstWheel == "BOW") and (secondWheel == "BOW") and ((thirdWheel == "BOW") or (thirdWheel == "HAMMER"))):
        win = 14
        balance = balance - 14
    elif((firstWheel == "DAGGER") and (secondWheel == "DAGGER") and ((thirdWheel == "DAGGER") or (thirdWheel == "HAMMER"))):
        win = 20
        balance = balance - 20
    elif((firstWheel == "HAMMER") and (secondWheel == "HAMMER") and (thirdWheel == "HAMMER")):
        win = 250
        balance = balance - 250
    elif((firstWheel == 20) and (secondWheel == 20) and (thridWheel == 20)):
        win = balance
        balance = balance - win
    else:
        win = -1
        balance = balance + 1

    stake += win
    if win == balance:
        print ("You won the JACKPOT!!")
    if(win > 0):
        print(firstWheel + '\t' + secondWheel + '\t' + thirdWheel + ' -- You win £' + str(win))
        time.sleep(3)
        os.system('cls' if os.name == 'nt' else 'clear')
    else:
        print(firstWheel + '\t' + secondWheel + '\t' + thirdWheel + ' -- You lose')
        time.sleep(2)
        os.system('cls' if os.name == 'nt' else 'clear')

play()
