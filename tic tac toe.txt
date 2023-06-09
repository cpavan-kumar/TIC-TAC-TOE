board = [" ", " ", " ", " ", " ", " ", " ", " ", " "]
def display_board():
    print(board[0] + " | " + board[1] + " | " + board[2])
    print(" - " + " - " + " - ")
    print(board[3] + " | " + board[4] + " | " + board[5])
    print(" - " + " - " + " - ")
    print(board[6] + " | " + board[7] + " | " + board[8])
def check_winner(player):
    if (board[0] == board[1] == board[2] == player or
        board[3] == board[4] == board[5] == player or
        board[6] == board[7] == board[8] == player or
        board[0] == board[3] == board[6] == player or
        board[1] == board[4] == board[7] == player or
        board[2] == board[5] == board[8] == player or
        board[0] == board[4] == board[8] == player or
        board[2] == board[4] == board[6] == player):
        return True
    else:
        return False

def play_game():
    player = "X"
    game_still_going = True

    while game_still_going:
        display_board()

        move = input("Player " + player + ", enter a position from 1-9: ")

        # Validate the input
        while move not in ["1", "2", "3", "4", "5", "6", "7", "8", "9"] or board[int(move)-1] != " ":
            move = input("Invalid input. Player " + player + ", enter a position from 1-9: ")

        # Update the board with the player's move
        board[int(move)-1] = player

        # Check if there is a winner or a tie
        if check_winner(player):
            display_board()
            print("Congratulations! Player " + player + " wins!")
            game_still_going = False
        elif " " not in board:
            display_board()
            print("It's a tie!")
            game_still_going = False

        # Switch to the other player
        player = "O" if player == "X" else "X"

# Start the game
play_game()