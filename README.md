# TECHDEGREE PROJECT #1

import random
import math
import sys

def good_job(playerName,attempts,playerScore):
    print("""

    You got it, {} ! It took you [{}] attempts, so your score is >>> {} <<<<.

    """.format(playerName,attempts,playerScore))

def exit_due_to_score(playerScore):
    if playerScore < -8:
        sys.exit("Sorry, Game Over!")


def rewards(playerScore):
    if playerScore == 100:
        print("""
              -------------------------------
              You are a WORLD CLASS player!!!
              -------------------------------
              """)




def help_input(playerName,attempts,playerScore):
    question = input("Do you want to play again?  'y/n'   ")
    if question.lower() == "n":

        if highscore[0] > playerScore:
            print("""
                  -----------------------------------
                  Your HIGHSCORE is {} ! ! !
                  -----------------------------------
                  """.format(highscore))
        elif highscore[0] <= playerScore:
            highscore[0] = playerScore
            print("""
                  -----------------------------------
                  Your HIGHSCORE is {} ! ! !
                  -----------------------------------
                  """.format(highscore))

        sys.exit("Bye {} !!! See you soon! ".format(playerName))
    elif question.lower() == "y":

        if highscore[0] > playerScore:
            print("""
                  -----------------------------------
                  Your HIGHSCORE is {} ! ! !
                  -----------------------------------
                  """.format(highscore))
        elif highscore[0] <= playerScore:
            highscore[0] = playerScore
            print("""
                  -----------------------------------
                  Your HIGHSCORE is {} ! ! !
                  -----------------------------------
                  """.format(highscore))
            print("Lets play again!")
        start()



highscore = [ 0 ]       #     -------->>>>>>> I NEEDED TO DEFINE HIGHSCORE HERE OUTSIDE


print("""
    --------------------------------------
    Welcome to our NUMBER GUESSING GAME!!!
    --------------------------------------
    """)

player_name = input("What is your name?   ")
player_name = player_name.capitalize()



#print("""
#     RULES OF THE GAME:
#     1.Guess an integer number from 1 to 10
#     2.Top score is 100 points.
#     3. You have 10 attempts to guess the number.
#     """)
#
#proceed = input("""
#                   ----------------------------------------------------
#                   If you want to see how we calculate points, type [t].
#                   If you like to proceed with the game, press 'ENTER'.
#                   If you don't want to proceed, type [n].
#                           >>>         """)
#if proceed.lower() == "n":
#    sys.exit("Sorry to hear that {}. See you soon!".format(player_name))
#elif proceed.lower() == "t":
#    print("""
#          * Attempt #1 = 100 points
#          * Attempt #2 = 96 points
#          * Attempt #3 = 90 points
#          * Attempt #4 = 82 points
#          * Attempt #5 = 72 points
#          * Attempt #6 = 60 points
#          * Attempt #7 = 46 points
#          * Attempt #8 = 30 points
#          * Attempt #9 = 12 points
#           """)

def start():
#    scores = [0]
    attempts = 0
    player_score = 102 # ---->>. I wanted to make game more interesting with scores , attempts are a bit simple as a result. So, the top score is 100 (102 - (1(attempt) *2) and so on with lower scores.
    random_number = random.randrange(1,10)
    print(random_number)
    player_guess = 0
    while random_number != player_guess:
        try:
            player_guess = int(input("Attempt # [{}] : {} , can you guess a number from 1 to 10?     ".format(attempts + 1,player_name)))
            if (player_guess < 1):
                raise ValueError("""
                                 Invalid input. Only integer numbers from 1 to 10 allowed --- !!!
                                 """)
            elif (player_guess > 10):
                raise ValueError("""
                                 Invalid input. Only integer numbers from 1 to 10 allowed --- !!!
                                 """)
            attempts +=1
            player_score -= attempts * 2
        except ValueError as error:
            if "invalid literal" in str(error):
                print("""
                      Invalid input. Please try again by typing an integer number. ex[2,4,7]
                      """)
            else:
                print(error)
            # I have all ok, but when i type letters, i get also invalid message from system together with my error messages???
        else:    
            #if answer in lower that random number ....
            if player_guess < random_number:
                exit_due_to_score(player_score)
                try:
                    player_guess= int(input("Attempt # [{}] : It is HIGHER!   ".format(attempts+1)   ))
                    attempts +=1
                    player_score -= attempts * 2
                except ValueError:
                    print("Invalid entry. Please type a integer number ex[4,6,9]")
                if random_number == player_guess:
                    good_job(player_name,attempts,player_score)
                    help_input(player_name,attempts,player_score)

                while random_number != player_guess:
                    if player_guess < random_number:
                        exit_due_to_score(player_score)
                        try:
                            player_guess= int(input("Attempt # [{}] : It is HIGHER!   ".format(attempts+1)   ))
                            attempts +=1
                            player_score -= attempts * 2
                        except ValueError:
                            print("Invalid entry. Please type a integer number ex[4,6,9]")
                        if random_number == player_guess:
                            good_job(player_name,attempts,player_score)
                            help_input(player_name,attempts,player_score)       
                    elif player_guess > random_number:
                        exit_due_to_score(player_score)
                        try:
                            player_guess = int(input("Attempt # [{}] : It is LOWER!   ".format(attempts+1)  ))
                            attempts +=1
                            player_score -= attempts * 2
                        except ValueError:
                            print("Invalid entry. Please type a integer number ex[4,6,9]")

                        if random_number == player_guess:
                            good_job(player_name,attempts,player_score)
                            help_input(player_name,attempts,player_score)       
            elif player_guess > random_number:
                exit_due_to_score(player_score)
                try:
                    player_guess = int(input("Attempt # [{}] : It is LOWER!   ".format(attempts + 1) ))
                    attempts +=1
                    player_score -= attempts * 2
                except ValueError:
                    print("Invalid entry. Please type a integer number ex[4,6,9]")

                if random_number == player_guess:
                    good_job(player_name,attempts,player_score)
                    help_input(player_name,attempts,player_score)
                while random_number != player_guess:
                    if player_guess < random_number:
                        exit_due_to_score(player_score)
                        try:
                            player_guess = int(input("Attempt # [{}] : It is HIGHER!   ".format(attempts+1)  ))
                            attempts +=1
                            player_score -= attempts * 2
                        except ValueError:
                            print("Invalid entry. Please type a integer number ex[4,6,9]")

                        if random_number == player_guess:
                            good_job(player_name,attempts,player_score)
                            help_input(player_name,attempts,player_score)

                    elif player_guess > random_number:
                        exit_due_to_score(player_score)
                        try:
                            player_guess = int(input("Attempt # [{}] : It is LOWER!   ".format(attempts+1)  ))
                            attempts +=1
                            player_score -= attempts * 2
                        except ValueError:
                            print("Invalid entry. Please type a integer number ex[4,6,9]")
                            if random_number == player_guess:
                                good_job(player_name,attempts,player_score)                            
                                help_input(player_name,attempts,player_score)                        
            else:
                rewards(player_score)
                good_job(player_name,attempts,player_score)
                help_input(player_name,attempts,player_score)

start()
