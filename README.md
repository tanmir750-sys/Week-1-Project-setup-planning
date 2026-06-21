import random

puzzles = [
    ("📚✏️🎓", "STUDENT"),
    ("🎬🍿🎥", "MOVIE"),
    ("🏏🏃🏆", "CRICKET"),
    ("🎮🕹️🏆", "GAMER"),
    ("🚀🌕⭐", "ROCKET"),
    ("📱💬📞", "MOBILE"),
    ("💻⌨️🖱️", "COMPUTER"),
    ("🌧️☁️💧", "WEATHER"),
    ("🔥🍳👨‍🍳", "COOKING"),
    ("🎸🎵🎤", "MUSICIAN")
]

emoji, word = random.choice(puzzles)

guessed_letters = []
lives = 6

print("================================")
print("      EMOJI HANGMAN")
print("================================")
print(f"Emoji Hint: {emoji}")

while lives > 0:

    display_word = ""

    for letter in word:
        if letter in guessed_letters:
            display_word += letter + " "
        else:
            display_word += "_ "

    print("\nWord:", display_word)
    print("Lives:", lives)

    if "_" not in display_word:
        print("\n🎉 Congratulations! You guessed the word.")
        break

    guess = input("Enter a letter: ").upper()

    if len(guess) != 1 or not guess.isalpha():
        print("Please enter one letter only.")
        continue

    if guess in guessed_letters:
        print("You already guessed that letter.")
        continue

    guessed_letters.append(guess)

    if guess not in word:
        lives -= 1
        print("Wrong guess!")

if lives == 0:
    print(f"\n💀 Game Over! The word was {word}")
