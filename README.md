# python_final_project

import time
import sys
from random import randrange
#Defining a function to delay the printing
def slowPrinting(s):
    for c in s:
        sys.stdout.write(c)
        time.sleep(0.05) 

# Class definition
class soldier ():
    def __init__(self,name, types, goldCoins, health, attackPower):
        self.name = name
        self.types= types
        self.goldCoins = goldCoins
        self.health = health
        self.attackPower = attackPower
 
 # Defintion of the function that handles the entire adventure
    def fight(self, enemy0, enemy1, enemy2):
        slowPrinting("Hello World! Meet your wonderful adventurer. His name is Josh. He is ready to conquer the all his enemies\n")
        slowPrinting("to save his princess Mia. \nJosh can be randomly attacked by unpredictable ennemies\n")
        slowPrinting("Let me also present you all the enemies that Josh the Hero may face during his risky journey toward his ultimate goal\n")
        slowPrinting("Meet enemy0 who is the most dangerous one. His damages are heavy.\nWe are also presenting enemy1 who can cause serious damages too.\nFinally, there is enemy2 who is not very dangerous\n")
        print(" ")
        time.sleep(2)
        
        slowPrinting("The following lines will show the data for the adventurer and the enemies\n")
        print("                           ")
        time.sleep(2)
        
        print("NAME      : ",self.name)
        print("TYPE      : ",self.types)
        print("GOLD COINS: ",self.goldCoins)
        print("HEALTH    : ",self.health)
        print("ATTACK    : ",self.attackPower)
        print("                          ")
        time.sleep(2)
        
        slowPrinting("will compete AGAINST--\n")
        print("  ")
        time.sleep(2)
        print("NAME      : ",enemy0.name)
        print("TYPE      : ",enemy0.types)
        print("GOLD COINS: ",enemy0.goldCoins)
        print("HEALTH    : ",enemy0.health)
        print("ATTACK    : ",enemy0.attackPower)
        print("                        ")
        time.sleep(2)
        print("NAME      : ",enemy1.name)
        print("TYPE      : ",enemy1.types)
        print("GOLD COINS: ",enemy1.goldCoins)
        print("HEALTH    : ",enemy1.health)
        print("ATTACK    : ",enemy1.attackPower)
        print("                         ")
        time.sleep(2)
        print("NAME      : ",enemy2.name)
        print("TYPE      : ",enemy2.types)
        print("GOLD COINS: ",enemy2.goldCoins)
        print("HEALTH    : ",enemy2.health)
        print("ATTACK    : ",enemy2.attackPower) 
        time.sleep(2)
        print(" ")
        slowPrinting("Let the adventure begin\n")
 # This loops takes care of the actual fight
        numOfSteps = 0
        while numOfSteps < 10:
            input("Type the letter y from the keyboard to continue making steps toward your target: ") 
            index = randrange(1,6) 
 # Enemy0 is attacking Josh
            if index == 1:
                message = "Josh you have been attacked by the most furious enemy which is enemy0 \n"
                slowPrinting(message)
                # Damage computation
                self.health = self.health - 5
                self.goldCoins = self.goldCoins - enemy0.attackPower
                print("enemy0 destroyed 5 of your health points and",enemy0.attackPower,"gold coins Josh.") 
                time.sleep(1)    
 # Your adventurer is being attacked by enemy1
            elif index == 2:
                message = "Josh you have been attacked by enemy1, some trinkets and health point got lost\n"
                slowPrinting(message)
                self.health = self.health - 3
                self.goldCoins = self.goldCoins - enemy1.attackPower
                print("You just lost 3 health points Josh and",enemy1.attackPower,"gold coins.")
                time.sleep(1)
           
           # Josh is being attacked by enemy2   
            elif index == 3:
                message = "Josh you have been attacked by enemy2, some gold coins and health points got lost\n"
                slowPrinting(message)
                self.health = self.health - 1
                self.goldCoins = self.goldCoins - enemy2.attackPower
                print("You lost 1 health point and",enemy2.attackPower,"gold coins.")
                time.sleep(1)
                  
            # No attack at all, Josh is earning gold coins and health points          
            else:
                message = "You are earning some power Josh,you are getting stronger\n"
                slowPrinting("No enemy is attacking now, your safe Josh!\n")
                slowPrinting(message)
                self.health = self.health + 5
                self.goldCoins = self.goldCoins + 10
                time.sleep(1)
                
            print("NEW HEALTH LEVEL    : ",self.health)
            print("NEW GOLD COINS LEVEL: ",self.goldCoins)   
           
           # for every 20 gold coins, one health point is added to the adventurer's health and 20 points are subsracted from the current gold coins amount    
            if self.goldCoins > 50:
                self.health = self.health + 1
                self.goldCoins = self.goldCoins - 20
             # This conditon verifies if the adventurer is still alive   
            if self.health > 0 and self.health <= 5:
                slowPrinting("Your health level is low Josh, be careful\n")
                time.sleep(1)
            elif self.health > 5:
                # This block is made to switch the sentences so that the program does not print the same sentence to encourage the adventurer
                sentIndicator = randrange(1,3)
                if sentIndicator == 1:
                    slowPrinting("Keep pushing Josh, you still have a good chance to rescue your princess\n")
                    time.sleep(1)
                else:
                    slowPrinting("Go Josh, you are on the right path\n")
                time.sleep(1)
            else: # if he is not alive, no more steps should be taken
                break
            numOfSteps = numOfSteps + 1   
        # meaning the adventurer died along the process
        if numOfSteps < 10:
            print("You failed to rescue your princess Mia.\nYou were only able to complete",numOfSteps,"steps out of the 10\n    GAME OVER")
            time.sleep(2)
        # meaning he was able to fully make all 10 steps    
        elif numOfSteps == 10:
            print("Your final gold coins amount is {0} and your final health level is {1}".format(self.goldCoins, self.health))
            time.sleep(2)
            print("CONGRATULATIONS JOSH!!! Your adventure had been a complete success.\nYou have rescued your hostage: princess Mia")
            
def main ():
 # Objects definitions   
    Josh = soldier("Josh", "adventurer", 30, 10, 0)
    enemy0 = soldier("enemy0","enemy", 0, 0, 10)
    enemy1 = soldier("enemy1","enemy", 0, 0, 5)          
    enemy2 = soldier("enemy2","enemy", 0, 0, 3)
 # the soldier.fight function is called to make the adventure take place   
    soldier.fight(Josh, enemy0, enemy1, enemy2)
              
main()              
  
