def main_menu():
    print("Flashcard App")
    print("1. Create Flashcard")
    print("2. Take Quiz")
    print("3. View Scores")
    print("4. Exit")
    choice = input("Enter your choice: ")
    return choice

def create_flashcard():
    question = input("Enter the question: ")
    answer = input("Enter the answer: ")
    flashcards[question] = answer
    print("Flashcard added successfully!\n")

def take_quiz():
    score = 0
    for question, answer in flashcards.items():
        user_answer = input(f"Question: {question}\nYour Answer: ")
        if user_answer.lower() == answer.lower():
            print("Correct!\n")
            score += 1
        else:
            print(f"Wrong! The correct answer is: {answer}\n")
    scores.append(score)
    print(f"Your score: {score}/{len(flashcards)}\n")

def view_scores():
    print("Scores:")
    for i, score in enumerate(scores, 1):
        print(f"Quiz {i}: {score}/{len(flashcards)}")

flashcards = {}
scores = []

while True:
    choice = main_menu()
    if choice == '1':
        create_flashcard()
    elif choice == '2':
        take_quiz()
    elif choice == '3':
        view_scores()
    elif choice == '4':
        break
    else:
        print("Invalid choice. Please try again.\n")
