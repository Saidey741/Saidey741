- 👋 Hi, I’m @Saidey741
- 👀 I’m interested in ...paython
- 🌱 I’m currently learning ...html
- 💞️ I’m looking to collaborate on ...my project
- 📫 How to reach me ... every time
- 😄 Pronouns: ...
- ⚡ Fun fact: ..

<!---
Saidey741/Saidey741 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
    """Prints the current state of the Tic-Tac-Toe board."""
    print("-------")
    for i in range(3):
        print("|", board[i][0], "|", board[i][1], "|", board[i][2], "|")
        print("-------")
def check_win(board, player):
    """Checks if the given player has won the game."""
    # Check rows
    for row in board:
        if all(cell == player for cell in row):
            return True
    # Check columns
    for col in range(3):
        if all(board[row][col] == player for row in range(3)):
            return True
    # Check diagonals
    if all(board[i][i] == player for i in range(3)):
        return True
    if all(board[i][2 - i] == player for i in range(3)):
        return True
    return False
def is_full(board):
    """Checks if the board is full."""
    return all(cell != " " for row in board for cell in row)
def play_game():
    """Main function to run the Tic-Tac-Toe game."""
    board = [[" " for _ in range(3)] for _ in range(3)]
    current_player = "X"
    while True:
        print_board(board)
        print(f"Player {current_player}'s turn.")
        while True:
            try:
                row = int(input("Enter row (0-2): "))
                col = int(input("Enter column (0-2): "))
                if 0 <= row <= 2 and 0 <= col <= 2 and board[row][col] == " ":
                    break
                else:
                    print("Invalid move. Please enter valid row and column for an empty cell.")
            except ValueError:
                print("Invalid input. Please enter numbers between 0 and 2.")
        board[row][col] = current_player
        if check_win(board, current_player):
            print_board(board)
            print(f"Player {current_player} wins!")
            break
        elif is_full(board):
            print_board(board)
            print("It's a tie!")
            break
        current_player = "O" if current_player == "X" else "X"
if __name__ == "__main__":
    play_game()
This code defines a simple text-based Tic-Tac-Toe game. Here's a breakdown of how it works:
 * print_board(board): This function takes the current state of the game board (a 3x3 list of lists) and prints it in a user-friendly format.
 * check_win(board, player): This function checks if the given player ("X" or "O") has won the game by examining all rows, columns, and diagonals for three consecutive marks of that player.
 * is_full(board): This function checks if all the cells on the board have been filled, indicating a potential tie.
 * play_game(): This is the main function that orchestrates the game:
   * It initializes an empty 3x3 board.
   * It sets the current_player to "X".
   * It enters a while True loop that continues until the game ends (win or tie).
   * Inside the loop:
     * It prints the current board using print_board().
     * It prompts the current player to enter the row and column for their move.
     * It includes error handling to ensure the input is valid (within the board boundaries and the chosen cell is empty).
     * It updates the board with the current player's mark.
     * It checks if the current player has won using check_win(). If so, it prints the final board and a win message, then breaks the loop.
     * It checks if the board is full using is_full(). If so, it prints the final board and a tie message, then breaks the loop.
     * It switches the current_player to the other player.
 * if __name__ == "__main__":: This ensures that the play_game() function is called only when the script is executed directly (not when it's imported as a module).
To play the game, simply run this Python code. It will prompt you to enter the row and column numbers (0-2) for your moves.

