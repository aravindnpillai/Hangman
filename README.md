# Hangman
A simple hangman game using Python
# Hangman....Created by Aravind

import time

name = raw_input('What is your Name ?')

print 'Hello '+ name +' Welcome To The Hangman '

print ' '

time.sleep(1)                                      # a time delay, which prints the lines with respect to a time

print 'Start Guessing...'

time.sleep(1)

import random                               


file = open('words.txt','r')                       # 'words.txt' contains a group words.open the file
data = file.readlines()                            # reading the file.
for line in data:
    word = line.split()                            # spliting the word for random selection


def pick_a_word():                                 # picking a random word from the 'words.txt'
    word_position = random.randint(0,len(word)-1)
    return word[word_position]

word = pick_a_word()                               # assign the word


guesses = ''                                       # the letter which player enters
 
turns = 6                                          # Number of Turns

while turns > 0:
    failed = 0

    for char in word:                              # gussed letter is found in randomly picked word
        if char in guesses:
            print char,
        else:
            print '_',
            failed+=1

    if  failed == 0:                               # if you save your lives
        print ' You WON the GAME'
        break
    print

    guess = raw_input('Guess a Letter :')          # Guessing each letter
    guesses += guess

    if guess == guesses:                           # if the correct letter guessed twice,lives (turns) wont decreases 
        print'_'

    if guess not in word:                          # guessed letter not found in the randomly picked word, turns decreases

        turns -= 1
    
        print 'Wrong '
        print 'You have', + turns,  'more Guesses' # this will print the guesses remaining
        
        if turns == 0:
            print 'You are HUNG !'                 # if you run out of guesses
    if turns < 1: print '   ________'              # some animation,which can be altered with your imagination
    if turns < 1: print '   !      !'
    if turns < 1: print '   !      !'
    if turns < 6: print '   O      !'
    if turns < 5: print ' \_|_/    !'
    if turns < 4: print '   |      !'
    if turns < 3: print '  / \     !'
    if turns < 2: print ' d   b    !'
    if turns == 0:
      print 'The answer is '+ word                # this will print the randomly selected word
      


               
    
          
    
 
        

