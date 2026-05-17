# Interactive Command Tutor 

## Project Description

Interactive Command Tutor Script is a Python command-line tool that helps students learn and practice basic Linux shell commands from Basic Command I and Basic Command II.

The program allows the user to review Linux commands by category, take multiple-choice quizzes, practice real command-line tasks, and view saved quiz/practice scores.

## Features

- Learn Mode:
  - Shows Linux commands by category.
  - Displays command meaning and example usage.

- Quiz Mode:
  - Provides Easy, Medium, Hard, and Mixed quiz options.
  - Uses multiple-choice questions.
  - Randomizes the question order.
  - Shows the correct answer when the user answers incorrectly.

- Practice Mode:
  - Provides Easy and Hard practical command tasks.
  - The user must type the correct Linux command.
  - The program checks the answer and shows the correct command if the answer is wrong.

- Score System:
  - Shows final score.
  - Shows correct and wrong answers.
  - Calculates percentage.
  - Gives feedback based on performance.

- Score History:
  - Saves quiz and practice results into `scores.txt`.
  - Allows the user to view previous saved scores.

## Requirements

- Kali Linux or any Linux terminal
- Python 3
- Git

To check if Python 3 is installed, run:

    python3 --version

To check if Git is installed, run:

    git --version

## Installation

1. Open the GitHub repository.

2. Click the green **Code** button.

3. Make sure **HTTPS** is selected.

4. Copy the repository link.

5. Open the terminal in Kali Linux and run:

    git clone <paste-the-repository-link-here>

Example:

    git clone https://github.com/YOUR_USERNAME/ITAP-3411.git

6. Go to the project folder:

    cd ITAP-3411/Eta

If Git is not installed, install it using:

    sudo apt update
    sudo apt install git -y

## Configuration

No special configuration is required.

The program runs directly in the terminal using Python 3.

Optional: if you want to run the program as an executable script using `./command_tutor.py`, give the file execute permission:

    chmod +x command_tutor.py

## How to Run

Run the program using Python 3:

    python3 command_tutor.py

Or, if you gave the file execute permission, run:

    ./command_tutor.py

## Short Usage Example

After running the program, the main menu appears:

    1. Learn Mode
       -Review Linux commands by category.

    2. Quiz Mode
       -Answer multiple-choice questions about Linux commands.

    3. Practice Mode
       -Type the correct command for practical tasks.

    4. View Previous Scores
       -Show saved quiz and practice results.

    5. Exit
       -Close the program.

Example usage:

    Choose option 1 to open Learn Mode.
    Choose a command category, such as Navigation or File and Directory.
    Review the commands, meanings, and examples.

    Choose option 2 to open Quiz Mode.
    Select Easy, Medium, Hard, or Mixed Quiz.
    Answer the multiple-choice questions.

    Choose option 3 to open Practice Mode.
    Select Easy or Hard Practice.
    Type the correct Linux command for each task.

    Choose option 4 to view saved scores.

## File Structure

    ITAP-3411/
    └── Eta/
        ├── command_tutor.py
        └── README.md

When the program saves scores, it automatically creates:

    scores.txt
