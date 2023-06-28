import random

word_list = ["python", "programming", "computer", "science", "coding"]

def play_hangman():
    word = random.choice(word_list)
    word = word.lower()
    word_letters = set(word)
    alphabet = set("abcdefghijklmnopqrstuvwxyz")
    used_letters = set()
    used_words = []
    word_guessed = set()
    used_letter = set()
    tries = 6
    print("Welcome to Hangman!\n")
    while len(word_letters) != 0 and tries > 0:
        print("You have", tries, "tries left.")
        sub = input("\nPlease enter a letter or a word: ").lower()
        if sub in used_letter:
            print("You already used that letter. Try again.")
            continue
        if len(sub) == 1 and sub in alphabet:
            used_letter.add(sub)
            if sub in word_letters:
                word_guessed.add(sub)
                word_letters.discard(sub)
            else:
                tries -= 1
                print("Incorrect. The letter is not in the word.")
        elif len(sub) == len(word) and sub not in used_words:
            used_words.append(sub)
            if sub == word:
                print("\nCongratulations! The word was", word + ".")
                break
            else:
                tries -= 1
                print("Incorrect. The word does not match.")
        else:
            print("Invalid input. Please enter a single letter or the word.")
        print("Word:", " ".join(letter if letter in word_guessed else "_" for letter in word))
    if tries == 0:
        print("You lost! The word was", word + ". Better luck next time!")
    else:
        print("\nGreat Job! You Guessed the word!")

play_hangman()

 
