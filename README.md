# Python
# Hangman game python code with User Menu
import random

word_list = ['python', 'java', 'kotlin', 'javascript']
random_word = random.choice(word_list)
guess_word = ""
chances = 0
repeated_letters = ""
for i in range(0, len(random_word)):
    guess_word = guess_word + "-"
print("H A N G M A N")
option = input('Type "play" to play the game, "exit" to quit:')
while True:
    if option == "play":
        print("")
        print(guess_word)
        while chances < 8 and "-" in guess_word:
            input_letter = input("Input a letter: ")
            if len(input_letter) != 1:
                print("You should print a single letter")
                if chances != 8:
                    print("")
                    print(guess_word)
                continue
            elif not input_letter.islower():
                print("It is not an ASCII lowercase letter")
                if chances != 8:
                    print("")
                    print(guess_word)
                continue
            elif input_letter in guess_word or input_letter in repeated_letters:
                print("You already typed this letter")
                if chances != 8:
                    print("")
                    print(guess_word)
            elif input_letter.islower() and len(input_letter) == 1:
                if input_letter in random_word and input_letter not in guess_word:
                    for i in range(0, len(random_word)):
                        if random_word[i] == input_letter:
                            guess_word = guess_word[:i] + input_letter + guess_word[i + 1:]
                    if chances != 8:
                        print("")
                        print(guess_word)
                    continue
                else:
                    print("No such letter in the word")
                    chances += 1
                    repeated_letters = repeated_letters + input_letter
                    if chances != 8:
                        print("")
                        print(guess_word)
                    continue
        if random_word == guess_word:
            print("You survived!")
            break
        elif chances == 8:
            print("You are hanged!")
            break
    elif option == "exit":
        break
