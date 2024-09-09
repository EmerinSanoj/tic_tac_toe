# tic_tac_toe
import random

board=[" "]*10
computer="x"
human="o"


def board_display(board):
    print(f"{board[1]}  | {board[2]}  | {board[3]}")
    print(f"{board[4]}  | {board[5]}  | {board[6]}")
    print(f"{board[7]}  | {board[8]}  | {board[9]}")
    print("-"*10)

def check_win():
    if board[1]==board[2]==board[3] and board[1]!=" ":
        return True
    elif board[4]==board[5]==board[6] and board[4]!=" ":
        return True
    elif board[7]==board[8]==board[9] and board[7]!=" ":
        return True
    elif board[1]==board[4]==board[7] and board[1]!=" ":
        return True
    elif board[2]==board[5]==board[8] and board[2]!=" ":
        return True
    elif board[3]==board[6]==board[9] and board[3]!=" ":
        return True
    elif board[1]==board[5]==board[9] and board[1]!=" ":
        return True
    elif board[3]==board[5]==board[7] and board[3]!=" ":
        return True
    else:
        return False
def check_draw():
    if board.count(" ")<2:
        return True
    else:
        return False
def is_available(p):
    return True if board[p] == " " else False
def insert(letter,p):
    if is_available(p):
        board[p]=letter
        board_display(board)
        if check_win():
            if letter=="x":
                print("Computer wins")
                exit()
            else:
                print("User wins")
                exit()
        if check_draw():
            print("Draw")

  else:
        if (letter=="o"):
            p=int(input("Not Free! please re-enter a position"))
        else:
            p=random.randint(1,9)
        insert(letter,p)

def human_move(letter):
    p=int(input("Enter the position to insert:"))
    insert(letter,p)

def computer_move(letter):
    p=random.randint(1,9)
    insert(letter,p)

while not check_win():
    board_display(board)
    computer_move(computer)
    human_move(human)
