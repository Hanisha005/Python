# Python
# Hangman game 
# Write your code here
import random

word_list = ['python', 'java', 'kotlin', 'javascript']
x = random.choice(word_list)
y = ""
z = 0
b = ""
for i in range(0, len(x)):
    y = y + "-"
print("H A N G M A N")
option = input('Type "play" to play the game, "exit" to quit:')
while True:
    if option == "play":
        print("")
        print(y)
        while z < 8 and "-" in y:
            word = input("Input a letter: ")
            if len(word) != 1:
                print("You should print a single letter")
                if z != 8:
                    print("")
                    print(y)
                continue
            elif not word.islower():
                print("It is not an ASCII lowercase letter")
                if z != 8:
                    print("")
                    print(y)
                continue
            elif word in y or word in b:
                print("You already typed this letter")
                if z != 8:
                    print("")
                    print(y)
            elif word.islower() and len(word) == 1:
                if word in x and word not in y:
                    for i in range(0, len(x)):
                        if x[i] == word:
                            y = y[:i] + word + y[i + 1:]
                    if z != 8:
                        print("")
                        print(y)
                    continue
                else:
                    print("No such letter in the word")
                    z = z + 1
                    b = b + word
                    if z != 8:
                        print("")
                        print(y)
                    continue
        if x == y:
            print("You survived!")
            break
        elif z == 8:
            print("You are hanged!")
            break
    elif option == "exit":
        break

