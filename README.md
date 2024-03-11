#tictactoe
#using python
# Function to print the board
def print_board(board):
    for i in range(0, 9, 3):
        print(" | ".join(board[i:i+3]))
        if i < 6:
            print("-" * 9)

# Function to check if the board is full
def is_board_full(board):
    return ' ' not in board

# Function to check if someone has won
def check_winner(board, player):
    winning_combinations = [[0, 1, 2], [3, 4, 5], [6, 7, 8],s
                            [0, 3, 6], [1, 4, 7], [2, 5, 8],
                            [0, 4, 8], [2, 4, 6]]

    for combo in winning_combinations:
        if all(board[i] == player for i in combo):
            return True
    return False

# Main game function
def play_game():
    board = [' ' for _ in range(9)]
    current_player = 'X'

    while True:
        print_board(board)
        print(f"\nPlayer {current_player}'s turn. Move to which place? (1-9): ")
        move = int(input()) - 1

        if board[move] == ' ':
            board[move] = current_player
        else:
            print("That place is already filled. Choose another.")
            continue

        if check_winner(board, current_player):
            print_board(board)
            print(f"Player {current_player} wins!")
            break

        if is_board_full(board):
            print_board(board)
            print("It's a tie!")
            break

        # Switch player
        current_player = 'O' if current_player == 'X' else 'X'

# Run the game
play_game()
