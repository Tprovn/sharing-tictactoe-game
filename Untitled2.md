```python
### WRITE A FUNCTION TO PRINT OUT A BOARD 3X3, WHERE EACH INDEX FROM 1-9 CORRESPONDS WITH A NUMBER ON A NUMPAD

from IPython.display import clear_output

def game_board(board):
    clear_output()  ### This works only on Jupiter

    print('   |   |')
    print(' ' + board[7] + ' | ' + board[8] + ' | ' + board[9])
    print('   |   |')
    print('-----------')
    print('   |   |')
    print(' ' + board[4] + ' | ' + board[5] + ' | ' + board[6])
    print('   |   |')
    print('-----------')
    print('   |   |')
    print(' ' + board[1] + ' | ' + board[2] + ' | ' + board[3])
    print('   |   |')
    

### WRITE A FUNCTION THAT ASSIGN A PLAYER'S INPUT AS X OR O, USING WHILE LOOPS TILL A PLAYER PUT IN EITHER X OR O

def player_input():
    marker = ''
    
    while not(marker == 'X' or marker == 'O'):
        marker = input('Player 1: Do you want to be X or O?').upper()
        
    if marker == 'X':
        return ('X','O')
    else:
        return ('O','X')
    
### WRITE A FUNCTION THAT ASSIGN X OR O TO THE BOARD AT DEESIRED POSITION

def marker_placing(board, marker, posistion):
    board[position] = marker
    
### WRITE A FUNCTION TO CHECK WIN CONDITIONS


def win_check(board,mark):
    
    return ((board[7] == mark and board[8] == mark and board[9] == mark) or # across the top
    (board[4] == mark and board[5] == mark and board[6] == mark) or # across the middle
    (board[1] == mark and board[2] == mark and board[3] == mark) or # across the bottom
    (board[7] == mark and board[4] == mark and board[1] == mark) or # down the middle
    (board[8] == mark and board[5] == mark and board[2] == mark) or # down the middle
    (board[9] == mark and board[6] == mark and board[3] == mark) or # down the right side
    (board[7] == mark and board[5] == mark and board[3] == mark) or # diagonal
    (board[9] == mark and board[5] == mark and board[1] == mark)) # diagonal


### WRITE A FUNCTION THAT RANDOMLY PICKS FIRST PLAYER

import random

def choose_first():
    if random.randint(0, 1) == 0:
        return 'Player 2'
    else:
        return 'Player 1'
    

### WRITE A FUNCTION  TO CHECK WHETHER A SPACE ON BOARD IS AVAILABLE OR UNUSED 

def space_check(board, position):
    return board[position] == ' '


### WRITE A FUNCTION TO CHECK IF BOARD IS FULL AND RETURN A BOOLEAN VALUE, TRUE IF FULL, OTHERWISE FALSE

def full_board_check(board):
    for i in range(1,10):
        if space_check(board, i):
            return False
        
    return True


### WRITE A FUNCTION ASKS FOR NEXT PLAYER'S MOVE THEN USES SPACE_CHECK FUNCTION ABOVE TO TO CHECK IF SELECTED SPOT IS FREE?

def player_choice(board):
    position = 0
    
    while position not in [1,2,3,4,5,6,7,8,9] or not space_check(board, position):
        position = int(input('Choose your next position: (1-9) '))
    
    return position


### WRITE A FUNCTION TO ASK IF PLAYERS WANT TO PLAY AGAIN

def play_again():
    return input('Do you want to play again? Enter Yes or No: ').lower().startswith('y')

       
print ("Welcome to Tic Tac Toe")

while True:
    # Reset the board
    
    the_board = [' ']*10
    player1_marker, player2_marker = player_input()
    turn = choose_first()
    print (turn + ' will go first.')
    
    game_play = input('Are you ready to play? Plesse enter Yes or No')
    
    if game_play.lower()[0] == 'y':
        game_on = True
    else:
        game_one = False
        
    while game_on:
        if turn == 'Player 1':
            # Player 1's turn
            
            game_board(the_board)
            positon = player_choice(the_board)
            marker_placing(the_board, player1_marker, position)
            
            if win_check(the_board, player1_marker):
                game_board(the_board)
                print('Congratulation! You have won the game!')
                game_on = False
            else:
                if full_board_check(the_board):
                    game_board(the_board)
                    print('The game is a draw!')
                    break
                else:
                    turn = 'Player 2'
        else:
            
        # Player 2's turn
            game_board(the_board)
            positon = player_choice(the_board)
            marker_placing(the_board, player2_marker, position)
            
            if win_check(the_board, player2_marker):
                game_board(the_board)
                print('Congratulation! You have won the game!')
                game_on = False
            else:
                if full_board_check(the_board):
                    game_board(the_board)
                    print('The game is a draw!')
                    break
                else:
                    turn = 'Player 1'
                    
    if not replay():
        break
```


```python

```
