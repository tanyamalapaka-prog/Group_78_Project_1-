# Group_78_Project_1-
import random

# Word bank of random words
word_bank = ["rake", "snail", "barbecue", ""]

# Prints the string with a space between each letter
def output(string):
    output = ""
    for char in string:
        output += char + " "
    print(output)


# Main game functionality
def play_hangman():
    guessed = False
    print("Let's play hangman!")
    mystery_word = random.choice(word_bank)
    guessed_word = ""
    for i in range(len(mystery_word)):
       guessed_word = ["_"] * len(mystery_word)
    output(guessed_word)
    
    lives_left = 6
    guessed_letters = []
    while lives_left > 0 and guessed == False:
        print('You have ' + str(lives_left) + ' lives left!')
        # Gets a letter from user
        letter = input("Guess a letter: ").lower()
        guessed_letters.append(letter)
        # 
        if len(letter) != 1 or not letter.isalpha():
            print('invalid input! Please enter a letter.')
        else:
            if letter in mystery_word:
                new_word = ""
                for i, char in enumerate(mystery_word):
                    if char == letter:
                        new_word += letter
                    elif guessed_word[i] != "_":
                        new_word += guessed_word[i]
                    else:
                        new_word += "_"
                guessed_word = new_word
            else:
                print("Letter not found!")
                lives_left -= 1
            output(guessed_word)
            if "_" not in guessed_word:
                guessed = True
                print("You guessed the word!")
                return
    print("Out of lives, game over!")
    
    
while True:
    play_hangman()
    again = input('Do you want to play again? ')
    if again.lower() != 'yes':
        print('Thanks for playing!')
        break
