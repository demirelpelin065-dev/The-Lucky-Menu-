The-Lucky-Menu-🎮🕹️👾

import random 


def thePowerOfTwo(x):
    if x > 21:  # if-condition that checks if input is greater than 21
        print("You have bypassed the maximum input value (21) allowed for this function!")
        # restrict output to 2^21 if condition is true
        for i in range(21):
            print(f"2^{i} = {2**i}")
    else:
        for i in range(x):
            print(f"2^{i} = {2**i}")
    print("\n")  # empty line for nicer structure
    

def diceGame(rounds):
    points_player = 0
    points_computer = 0
    my_rolls = []   # List to store player's rolls
    comp_rolls = [] # List to store computer's rolls

    for i in range(rounds):
        print(f"Round {i + 1} begins..\n")
        input("Press Enter to roll the dice!")
        roll_1 = random.randint(1, 6)
        my_rolls.append(roll_1)
        print(f"You rolled {roll_1}\n")
        input("Opponent's turn, press Enter to continue!")
        roll_2 = random.randint(1, 6)
        comp_rolls.append(roll_2)
        print(f"Opponent rolled {roll_2}\n")

        if roll_1 > roll_2:
            print("You won this round!")
            points_player += 1
            print(f"Score after this round: {points_player}-{points_computer} (You vs Opponent)")
        elif roll_1 < roll_2:
            print("You lost this round!")
            points_computer += 1
            print(f"Score after this round: {points_player}-{points_computer} (You vs Opponent)")
        else:
            print("This round is a draw!")
            print(f"Score after this round: {points_player}-{points_computer} (You vs Opponent)")

        print("\n")
    print(f"Final score: {points_player}-{points_computer} (You vs Opponent)")
    if points_player > points_computer:
        print("Congratulations! You won the game!")
    elif points_player < points_computer:
        print("Unfortunately, you lost. The opponent wins!")
    else:
        print("The game ended in a draw!")

    # Calculate and print statistics
    avg_roll_player = round(sum(my_rolls) / len(my_rolls), 1)
    avg_roll_comp = round(sum(comp_rolls) / len(comp_rolls), 1)
    min_roll_player = min(my_rolls)
    min_roll_comp = min(comp_rolls)
    max_roll_player = max(my_rolls)
    max_roll_comp = max(comp_rolls)
    print(f"\nYour average roll: {avg_roll_player}")
    print(f"Opponent's average roll: {avg_roll_comp} \n")
    print(f"Your lowest roll: {min_roll_player}")
    print(f"Opponent's lowest roll: {min_roll_comp} \n")
    print(f"Your highest roll: {max_roll_player}")
    print(f"Opponent's highest roll: {max_roll_comp}\n")



def guessRandomNumber():
    under_seven = 0  # boolean-like variable to show if it took <=7 attempts
    attempts = 0
    random_number = random.randint(1, 100)
    
    while True:
        user_guess = int(input("Guess a number between 1 and 100: "))
        attempts += 1
        
        if user_guess == random_number:
            print(f"You guessed correctly in {attempts} attempts.")
            if attempts <= 7:
                print("Well done!")
                under_seven = 1
            else:    
                print("That took too many attempts, try again.")
            return under_seven
        elif user_guess < random_number:
            print("Too low! Try again.")
        else:
            print("Too high! Try again.")
        



consecutive_wins = 0  # Variable to keep track of consecutive successful guesses
while True:
    print("1. thePowerOfTwo()")
    print("2. diceGame()")
    print("3. guessRandomNumber()")
    print("4. Close the menu")
    inp = int(input("Choose one of the four options (1 -> 4): "))

   
    if inp == 1:
        inp1 = int(input("Enter an input for the function to start: "))
        print("\n")
        thePowerOfTwo(inp1)
    
    if inp == 2:
        inp2 = int(input("How many rounds do you want to play? Enter a number: "))
        print("\n")
        diceGame(inp2)
     
    if inp == 3:
        print("\n")
        play = guessRandomNumber()  # =1 if it took <=7 guesses, otherwise =0
        if play:
            consecutive_wins += 1
        else:
            consecutive_wins = 0

        if consecutive_wins >= 3:
            print("You clearly have a good guessing strategy!")    
          
    if inp == 4:
        break
