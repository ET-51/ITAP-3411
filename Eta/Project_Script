#!/usr/bin/python3
import os
import random

"""
Interactive Command Tutor Script

This program helps students learn and practice Linux shell commands
from Basic Command I and Basic Command II.


Main features:

1. Learn Mode:
   Allows the user to choose a command category and review Linux commands
   with their meanings and example usage.

2. Quiz Mode:
   Allows the user to choose Easy, Medium, Hard, or Mixed quiz mode.
   The quiz uses multiple-choice questions and randomizes the question order.

3. Practice Mode:
   Allows the user to practice real command-line situations.
   The user must type the correct Linux command.
   Practice Mode includes Easy and Hard task levels.

4. Score System:
   Counts correct and wrong answers, shows the final score,
   calculates the percentage, and gives feedback based on performance.

5. Score History:
   Saves quiz and practice results into scores.txt and allows
   the user to view previous saved scores.

6. Exit:
   Allows the user to safely close the program from the main menu.
"""

# =========================
# DATA SECTION
# =========================
# This section stores the main data used by the program.



# format of commands is [category, command name, meaning, example]
commands = [
    ["Navigation", "pwd", "Shows the current working directory", "pwd"],
    ["Navigation", "cd", "Changes the current directory", "cd Desktop"],
    ["Navigation", "ls", "Lists files and directories", "ls -la"],
    ["Navigation", "clear", "Clears the terminal screen", "clear"],

    ["File and Directory", "cat", "Displays the content of a file", "cat file.txt"],
    ["File and Directory", "touch", "Creates an empty file", "touch notes.txt"],
    ["File and Directory", "mkdir", "Creates a new directory", "mkdir project"],
    ["File and Directory", "cp", "Copies files or directories", "cp file.txt backup.txt"],
    ["File and Directory", "mv", "Moves or renames files and directories", "mv old.txt new.txt"],
    ["File and Directory", "rm", "Removes files or directories", "rm old.txt"],

    ["Help and Search", "man", "Opens the manual page for a command", "man ls"],
    ["Help and Search", "whereis", "Shows the location of a command", "whereis python3"],
    ["Help and Search", "find", "Searches for files and directories", "find /home/kali -name '*.txt'"],

    ["Users and Permissions", "whoami", "Shows the current logged-in user", "whoami"],
    ["Users and Permissions", "sudo", "Runs a command with administrator privileges", "sudo apt update"],
    ["Users and Permissions", "chmod", "Changes file permissions", "chmod +x script.py"],
    ["Users and Permissions", "su", "Switches to another user", "su username"],

    ["Text Processing", "grep", "Searches for text inside a file", "grep 'hello' file.txt"],
    ["Text Processing", "sort", "Sorts lines of text", "sort names.txt"],
    ["Text Processing", "uniq", "Removes repeated adjacent duplicate lines", "sort names.txt | uniq"],
    ["Text Processing", "wc", "Counts lines, words, and characters", "wc -l file.txt"],
    ["Text Processing", "nl", "Displays a file with line numbers", "nl file.txt"],
    ["Text Processing", "cut", "Extracts sections from text", "cut -d ':' -f 1 /etc/passwd"],

    ["Processes and Network", "ps", "Shows running processes", "ps aux"],
    ["Processes and Network", "top", "Shows real-time process and resource usage", "top"],
    ["Processes and Network", "ping", "Tests network connectivity", "ping 8.8.8.8"],
    ["Processes and Network", "ifconfig", "Shows network interface information", "ifconfig"],
    ["Processes and Network", "ip route", "Shows routing table information", "ip route"],

    ["System Tools", "history", "Shows previously used commands", "history"],
    ["System Tools", "apt", "Installs, updates, and removes packages", "sudo apt install git -y"],
    ["System Tools", "tar", "Creates or extracts archive files", "tar -czvf backup.tar.gz folder"],
    ["System Tools", "sleep", "Pauses execution for a period of time", "sleep 5"]
]


# format of the quiz questions is [question, option A, option B, option C, option D, correct option]
# Easy quiz questions focus on basic command meanings.
easy_quiz_questions = [
    ["Which command shows the current directory?", "ls", "pwd", "cd", "cat", "B"],
    ["Which command lists files and directories?", "pwd", "ls", "mkdir", "chmod", "B"],
    ["Which command changes the current directory?", "cd", "cat", "grep", "touch", "A"],
    ["Which command creates an empty file?", "mkdir", "touch", "rm", "ps", "B"],
    ["Which command creates a new directory?", "cat", "mkdir", "mv", "wc", "B"]
]

# Medium quiz questions use options and slightly more practical commands.
medium_quiz_questions = [
    ["Which command lists hidden files?", "ls -a", "ls -l", "ls -h", "ls -x", "A"],
    ["Which command lists files with detailed information?", "ls -a", "ls -l", "ls -r", "ls -p", "B"],
    ["Which command gives execute permission to script.py?", "chmod +x script.py", "sudo script.py", "cat script.py", "run script.py", "A"],
    ["Which command searches for hello inside file.txt?", "find hello file.txt", "grep hello file.txt", "sort hello file.txt", "cat hello file.txt", "B"],
    ["Which command counts lines in file.txt?", "wc -l file.txt", "nl file.txt", "cat -n file.txt", "sort file.txt", "A"]
]

# Hard quiz questions focus on commands from Basic Command II and system usage.
hard_quiz_questions = [
    ["Which command sorts lines alphabetically?", "grep", "sort", "uniq", "rev", "B"],
    ["Which command removes repeated adjacent duplicate lines?", "uniq", "sort", "grep", "cut", "A"],
    ["Which command extracts fields from text using a delimiter?", "cut", "top", "ping", "touch", "A"],
    ["Which command tests network connectivity?", "ifconfig", "ping", "apt", "su", "B"],
    ["Which command creates or extracts archive files?", "tar", "mount", "cron", "sleep", "A"]
]

# format of the tasks is [task, answer]
# Easy practice tasks use simple beginner commands.
easy_practice_tasks = [
    ["Show the current directory", "pwd"],
    ["Create a folder called test", "mkdir test"],
    ["Create an empty file called notes.txt", "touch notes.txt"],
    ["Show the content of file.txt", "cat file.txt"],
    ["List files with detailed information", "ls -l"],
    ["Show the current logged-in user", "whoami"],
    ["List all files including hidden files", "ls -a"],
]

# Hard practice tasks use commands with options, permissions, searching, or networking.
hard_practice_tasks = [
    ["Give execute permission to script.py", "chmod +x script.py"],
    ["Search for the word hello inside file.txt", "grep hello file.txt"],
    ["Count the number of lines in file.txt", "wc -l file.txt"],
    ["Sort the contents of names.txt alphabetically", "sort names.txt"],
    ["Show the command history", "history"],
    ["Test connection to 8.8.8.8", "ping 8.8.8.8"]
]

# =========================
# HELPER FUNCTIONS
# =========================
#small functions used by different parts of the program. They help avoid repeating the same code many times.


# Pauses the program so the user can read the output before returning to the menu.
def pause():
    input("\nPress 'Enter' to return to the main menu...")

# Clears the terminal screen to make the interface cleaner.
def clear_screen():
    os.system("clear")

#prints a formatted title for each screen or mode.
def print_header(title):
    print("==============================")
    print("--- ", title)
    print("==============================\n")
    
# =========================
# LEARN MODE
# =========================
# This function displays Linux commands with their meanings and examples.


def learn_mode():
    # This loop keeps Learn Mode open until the user chooses Back to Main Menu.
    while True:
        clear_screen()
        print_header("Learn Mode")
        
        # Display the available command categories.
        print("What do you want to learn?\n")
        print("1. Navigation")
        print("2. File and Directory")
        print("3. Help and Search")
        print("4. Users and Permissions")
        print("5. Text Processing")
        print("6. Processes and Network")
        print("7. System Tools")
        print("8. Show All Commands")
        print("9. Back to Main Menu")

        choice = input("\nChoose an option: ")
        
        
        # Call the correct function depending on the user's category choice.
        if choice == "1":
            show_commands_by_category("Navigation")
        elif choice == "2":
            show_commands_by_category("File and Directory")
        elif choice == "3":
            show_commands_by_category("Help and Search")
        elif choice == "4":
            show_commands_by_category("Users and Permissions")
        elif choice == "5":
            show_commands_by_category("Text Processing")
        elif choice == "6":
            show_commands_by_category("Processes and Network")
        elif choice == "7":
            show_commands_by_category("System Tools")
        elif choice == "8":
            show_all_commands()
        elif choice == "9":
            break
        else:
            print("Invalid choice. Try again.")
            pause()
            
def show_commands_by_category(category):
    clear_screen()
    print_header(category)
    
    # Go through the commands list and print only commands that match the selected category.
    for command in commands:
        if command[0] == category:
            print("\nCommand:", command[1])
            print("Meaning:", command[2])
            print("Example:", command[3])

    pause()


def show_all_commands():
    clear_screen()
    print_header("All Commands")
    
    # Print every command from the commands list, including its category.
    for command in commands:
        print("\nCategory:", command[0])
        print("Command:", command[1])
        print("Meaning:", command[2])
        print("Example:", command[3])

    pause()

# =========================
# QUIZ MODE
# =========================
# The user chooses a quiz difficulty, then answers multiple-choice questions.
# The program checks the answers, counts the score, and saves the result.

def quiz_mode():
    clear_screen()
    print_header("Quiz Mode")
    # Display quiz difficulty options.
    print("1. Easy Quiz")
    print("2. Medium Quiz")
    print("3. Hard Quiz")
    print("4. Mixed Quiz")
    print("5. Back to Main Menu")

    start_choice = input("\nChoose an option: ")
    
    # Select the question list based on the user's choice.
    if start_choice == "1":
        selected_questions = easy_quiz_questions
        mode_name = "Easy Quiz Mode"
    elif start_choice == "2":
        selected_questions = medium_quiz_questions
        mode_name = "Medium Quiz Mode"
    elif start_choice == "3":
        selected_questions = hard_quiz_questions
        mode_name = "Hard Quiz Mode"
    elif start_choice == "4":
        selected_questions = easy_quiz_questions + medium_quiz_questions + hard_quiz_questions
        mode_name = "Mixed Quiz Mode"
    elif start_choice == "5":
        return
    else:
        print("Invalid choice.")
        pause()
        return

    clear_screen()
    print_header(mode_name)
    score = 0
    
    # Copy and shuffle the selected questions so the original list is not changed.
    random_questions = selected_questions.copy()
    random.shuffle(random_questions)
    
    question_number = 1
    
    # Go through each question and display its answer choices.
    for question in random_questions:
        print("\n  Question", question_number, "of", len(random_questions))
        print(" ", question[0])
        print("      A.", question[1])
        print("      B.", question[2])
        print("      C.", question[3])
        print("      D.", question[4])

        answer = input("\n   Choose A, B, C, or D: ")
        answer = answer.upper().strip()
        
        # Check if the user's answer matches the correct option.
        if answer == question[5]:
            print("  " , "Correct!")
            score = score + 1
        else:
            # Find the correct answer text based on the correct option letter
            if question[5] == "A":
                correct_answer = question[1]
            elif question[5] == "B":
                correct_answer = question[2]
            elif question[5] == "C":
                correct_answer = question[3]
            elif question[5] == "D":
                correct_answer = question[4]

            print("  ", "Wrong! Correct answer is:", question[5] + " =", correct_answer)
        
        # Move to the next question number.    
        question_number = question_number + 1
            
    clear_screen()
    print_header("Quiz Result")
    
     # Show and save the final quiz result.
    show_score(score, len(random_questions))
    save_score(mode_name, score, len(random_questions))

    retry = input("\nDo you want to try another quiz? (y/n): ")
    retry = retry.lower().strip()

    if retry == "y":
        quiz_mode()
    else:
        return
    
# =========================
# PRACTICE MODE
# =========================
# This function gives the user a real command-line task.
# The user must type the correct Linux command.


def practice_mode():
    clear_screen()
    print_header("Practice Mode")
    
    # Display practice difficulty options.
    print("1. Easy Practice")
    print("2. Hard Practice")
    print("3. Back to Main Menu")

    start_choice = input("\nChoose an option: ")
    
    # Select the task list based on the user's choice.
    if start_choice == "1":
        selected_tasks = easy_practice_tasks
        mode_name = "Easy Practice Mode"
    elif start_choice == "2":
        selected_tasks = hard_practice_tasks
        mode_name = "Hard Practice Mode"
    elif start_choice == "3":
        return
    else:
        print("Invalid choice.")
        pause()
        return

    clear_screen()
    print_header(mode_name)

    score = 0
    
    task_number = 1
    
    # Go through each practical task and ask the user to type the command.
    for task in selected_tasks:
        print("\n   Task", task_number, "of", len(selected_tasks))
        print("  ", task[0])
        answer = input("   Type the command: ")

        # Make answer checking less strict:
        # lower() ignores capital letters.
        # split() removes extra spaces.
        # join() puts the words back with one space between them.
        answer = " ".join(answer.lower().split())
        
        # Apply the same formatting to the correct answer before comparing.
        correct_answer = " ".join(task[1].lower().split())

        if answer == correct_answer:
            print("  " , "Correct!")
            score = score + 1
        else:
            print("  " ,"Wrong! Correct answer is:", task[1])
        
        # Move to the next task number.    
        task_number = task_number + 1
        
    clear_screen()
    print_header("Practice Result")
    show_score(score, len(selected_tasks))
    save_score(mode_name, score, len(selected_tasks))
    pause()
    
# =========================
# SCORE SYSTEM
# =========================
# This section handles quiz and practice results.
# It displays the score, calculates the percentage,
# gives feedback, saves scores to a text file, and shows previous score

def show_score(score, total):
     # Calculate wrong answers and percentage based on the final score.
    wrong = total - score
    percentage = (score / total) * 100

    print("\nFinal score:", score, "/", total)
    print("Correct answers:", score)
    print("Wrong answers:", wrong)
    print("Percentage:", round(percentage, 1), "%")
    
    # Give feedback depending on the user's percentage.
    if percentage >= 90:
        print("Excellent! You understood the commands very well.")
    elif percentage >= 70:
        print("Good job, but you can still improve.")
    elif percentage >= 50:
        print("Not bad, but you should review Learn Mode again.")
    else:
        print("You need more practice. Try Learn Mode again.")
        
def save_score(mode, score, total):
    # Save the result in append mode so old scores are not deleted.
    percentage = (score / total) * 100

    file = open("scores.txt", "a")
    file.write(mode + " | Score: " + str(score) + "/" + str(total) + " | Percentage: " + str(round(percentage, 1)) + "%\n")
    file.close()
    
def view_scores():
    clear_screen()
    print_header("Previous Scores")
    
     # Try to open scores.txt. If it does not exist yet, show a message instead of crashing.
    try:
        file = open("scores.txt", "r")
        content = file.read()
        file.close()

        if content == "":
            print("No scores saved yet.")
        else:
            print(content)

    except FileNotFoundError:
        print("No scores saved yet.")

    pause()  
    
# =========================
# MAIN MENU
# =========================
# This section controls the main flow of the program.
# Based on the user's choice, it calls the correct program function.

def main():
    # Keep the program running until the user chooses option 5.
    while True:
        clear_screen()
        print_header("Interactive Command Tutor")
        print("1. Learn Mode")
        print("   -Review Linux commands by category.\n")
        
        print("2. Quiz Mode")
        print("   -Answer multiple-choice questions about Linux commands.\n")
        
        print("3. Practice Mode")
        print("   -Type the correct command for practical tasks.\n")
        
        print("4. View Previous Scores")
        print("   -Show saved quiz and practice results.\n")
        
        print("5. Exit")
        print("   -Close the program.\n")
    
        choice = input("\nChoose an option: ")
        
        # Call the selected feature based on the user's menu choice.
        if choice == "1":
          learn_mode()
        elif choice == "2":
          quiz_mode()
        elif choice == "3":
          practice_mode()
        elif choice == "4":
          view_scores()
        elif choice == "5":
          print("Goodbye")
          break
        else:
          print("invalid choice, try again.")
          pause()

# =========================
# PROGRAM START
# =========================
# The program starts here by calling the main menu function.
main()
