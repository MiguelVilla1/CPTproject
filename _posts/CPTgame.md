---
layout: default
title: Higher or Lower Number Guesser
permalink: /CPTgame
---

<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Python File Styling</title>
    <style>
        body {
            background-color: #f39c12;
            margin: 0;
            font-family: 'Impact', fantasy;
            color: #ecf0f1;
            text-align: center;
            padding: 50px; 
        }
        .textbox {
            background: rgba(0, 0, 0, 0.5);
            border: 1px solid #ecf0f1;
            padding: 20px;
            margin: 20px;
            border-radius: 10px;
            max-width: 600px;
            margin: auto;
        }
        h1 {
            font-size: 2.5em;
            margin-bottom: 20px;
        }
        p {
            font-size: 1.2em;
            line-height: 1.5;
        }
    </style>
</head>
<body>
    <div class="textbox">

import random

def main():
    secret_number = random.randint(1, 100)
    previous_guesses = []
    play_again = True
    
    while play_again:
        guess = input("Guess the number between 1 and 100: ")
        
        while not guess.isdigit() or int(guess) < 1 or int(guess) > 100:
            print("Invalid input. Please enter a number between 1 and 100.")
            guess = input("Guess the number between 1 and 100: ")
        
        guess = int(guess)
        
        if guess == secret_number:
            print("Congratulations! You guessed the correct number!")
            play_again = play_again_prompt()
        elif guess < secret_number:
            print("Higher")
        else:
            print("Lower")
        
        previous_guesses.append(guess)

def play_again_prompt():
    while True:
        play_again_input = input("Do you want to play again? (yes/no): ").lower()
        if play_again_input == "yes":
            return True
        elif play_again_input == "no":
            print("Thank you for playing!")
            return False
        else:
            print("Invalid input. Please enter 'yes' or 'no'.")

def run_tests():
    secret_number = 50
    assert guess_number(secret_number, 50) == "Congratulations! You guessed the correct number!"
    secret_number = 75
    assert guess_number(secret_number, 60) == "Lower"
    secret_number = 25
    assert guess_number(secret_number, 40) == "Higher"
    assert play_again_prompt("yes") == True
    assert play_again_prompt("no") == False
    assert guess_number(50, "abc") == "Invalid input. Please enter a number between 1 and 100."
    assert guess_number(50, 200) == "Invalid input. Please enter a number between 1 and 100."

def guess_number(secret_number, guess=None):
    if guess is None:
        guess = input("Guess the number between 1 and 100: ")
        
        while not guess.isdigit() or int(guess) < 1 or int(guess) > 100:
            print("Invalid input. Please enter a number between 1 and 100.")
            guess = input("Guess the number between 1 and 100: ")
        
        guess = int(guess)
    
    if guess == secret_number:
        return "Congratulations! You guessed the correct number!"
    elif guess < secret_number:
        return "Higher"
    else:
        return "Lower"

if __name__ == "__main__":
    run_tests()
    main()
