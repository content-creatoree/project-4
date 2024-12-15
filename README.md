# project-4
import random

def display_word(word, guessed_letters):
    return ' '.join([letter if letter in guessed_letters else '_' for letter in word])

def get_guess(guessed_letters):
    while True:
        guess = input("Enter a letter: ").lower()
        if len(guess) != 1 or not guess.isalpha():
            print("Please enter a single letter.")
        elif guess in guessed_letters:
            print("You already guessed that letter. Try again.")
        else:
            return guess

def hangman():
    words = ['python', 'hangman', 'programming', 'challenge', 'computer']
    word_to_guess = random.choice(words)
    guessed_letters = set()
    attempts_remaining = 6
    word_guessed = False

    print("Welcome to Hangman!")
    print(display_word(word_to_guess, guessed_letters))

    while attempts_remaining > 0 and not word_guessed:
        print(f"\nAttempts remaining: {attempts_remaining}")
        guess = get_guess(guessed_letters)
        guessed_letters.add(guess)

        if guess in word_to_guess:
            print(f"Good guess! '{guess}' is in the word.")
        else:
            print(f"Sorry, '{guess}' is not in the word.")
            attempts_remaining -= 1

        current_display = display_word(word_to_guess, guessed_letters)
        print(current_display)

        if '_' not in current_display:
            word_guessed = True

    if word_guessed:
        print("\nCongratulations! You guessed the word!")
    else:
        print(f"\nGame over! The word was '{word_to_guess}'. Better luck next time!")

if __name__ == "__main__":
    hangman()
Welcome to Hangman!
_ _ _ _ _ _ _ _

Attempts remaining: 6
Enter a letter: animal
Please enter a single letter.
Enter a letter: food
Please enter a single letter.
Enter a letter: a
Sorry, 'a' is not in the word.
_ _ _ _ _ _ _ _

Attempts remaining: 5
Enter a letter: p
Good guess! 'p' is in the word.
_ _ _ p _ _ _ _

 
