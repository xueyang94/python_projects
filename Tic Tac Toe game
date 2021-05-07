import colorama
from colorama import Fore, Back, Style
colorama.init(autoreset=True)

class color:
   PURPLE = '\033[95m'
   CYAN = '\033[96m'
   DARKCYAN = '\033[36m'
   BLUE = '\033[94m'
   GREEN = '\033[92m'
   YELLOW = '\033[93m'
   RED = '\033[91m'
   BOLD = '\033[1m'
   UNDERLINE = '\033[4m'
   END = '\033[0m'

avnums = [1,2,3,4,5,6,7,8,9]
config = [' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ']
def print_board(board_nums):
    board = ['  | ', '  |  ', '\n', board_nums[0], ' | ', board_nums[1], ' | ', board_nums[2], '\n', '  | ', '  |  ', '\n',
             ' —', ' —', ' —', ' — ', '\n',
             '  | ', '  |  ', '\n', board_nums[3], ' | ', board_nums[4], ' | ', board_nums[5], '\n', '  | ', '  |  ', '\n',
             ' — ', ' — ', ' — ', '\n',
             '  | ', '  |  ', '\n', board_nums[6], ' | ', board_nums[7], ' | ', board_nums[8],'\n',  '  | ', '  |  ', '\n']
    for item in board:
        if item == 'X':
            print(color.BOLD + Fore.YELLOW + Style.BRIGHT + Back.CYAN + 'X', end="" + color.END)
        elif item == 'O':
            print(color.BOLD + Fore.RED + Style.BRIGHT + Back.CYAN + 'O', end="" + color.END)
        else:
            print(color.BOLD + Style.BRIGHT + Back.CYAN + item, end="" + color.END)


def check_position(available_position):
    choice = input("Choose your next position: ")
    while choice.isdigit()==False or int(choice) not in available_position:
        print("Input is invalid!")
        choice = input("Choose your next position: ")
    return int(choice)


def player_input():
    player1 = input("Player 1: Do you want to be X or O? ")
    while player1 not in ['X','O']:
        print("Invalid answer!")
        player1 = input("Player 1: Do you want to be X or O? ")
    if player1 == 'X':
        player2 = 'O'
    else:
        player2 = 'X'
    print("Player1 will go first.")
    return [player1, player2]


def place_marker1(player_set, available_nums, v_config):
    player1 = player_set[0]
    player1_position = check_position(available_nums) - 1
    v_config[player1_position] = player1
    print_board(v_config)
    available_nums.remove(player1_position + 1)
    return [available_nums, v_config]

def place_marker2(player_set, available_nums, v_config):
    player2 = player_set[1]
    player2_position = check_position(available_nums) - 1
    v_config[player2_position] = player2
    print_board(v_config)
    available_nums.remove(player2_position + 1)
    return [available_nums, v_config]


def check_win(player_marks, v_config):
    win_inside = False
    breaker = 1
    while breaker == 1:
        for p in player_marks:
            for item in [0, 3, 6]:
                if p == v_config[0+item] and p == v_config[1+item] and p == v_config[2+item]:
                    print(Fore.RED + Style.BRIGHT + f"Congratulations! {p} win!")
                    win_inside = True
                    breaker = 2
                    break
            for item in [0, 1, 2]:
                if p == v_config[0+item] and p == v_config[3+item] and p == v_config[6+item]:
                    print(Fore.RED + Style.BRIGHT + f"Congratulations! {p} win!")
                    win_inside = True
                    breaker = 2
                    break
            if (p == v_config[0] and p == v_config[4] and p == v_config[8]) or (p == v_config[2] and p == v_config[4] and p == v_config[6]):
                print(Fore.RED + Style.BRIGHT + "Congratulations! {} win!".format(v_config[4]))
                win_inside = True
                breaker = 2
                break
            breaker = 2
    return win_inside


def game():
    print("Welcome to this Tic Tac Toe game, created by XW")
    ready = input("Are you ready to play? Enter Yes or No: ")
    print("The numbered positions are like this: ")
    IC = [1, ' | ', 2, ' | ', 3, '\n', '\n', 4, ' | ', 5, ' | ', 6, '\n', '\n', 7, ' | ', 8, ' | ', 9, '\n']
    for item in IC:
        print(item, end="")
    print("Here is the initial empty board: ")
    config = [' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ']
    print_board(config)

    while ready == 'Yes':
        avnums = [1,2,3,4,5,6,7,8,9]
        config = [' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ', ' ']
        counter = 0
        win = False
        test = 1
        #print_board(config)
        player_symbols = player_input()
        while counter < 4:
            marker_result1 = place_marker1(player_symbols, avnums, config)
            available1 = marker_result1[0]
            config = marker_result1[1]
            print(f"Available positions include: {available1}")
            counter += 1

            marker_result2 = place_marker2(player_symbols, avnums, config)
            available2 = marker_result2[0]
            config = marker_result2[1]
            print(f"Available positions include: {available2}")
            counter += 1
        while win == False:
            marker_result1 = place_marker1(player_symbols, avnums, config)
            available1 = marker_result1[0]
            config = marker_result1[1]
            print(f"Available positions include: {available1}")
            win = check_win(player_symbols, config)
            if win == True:
                break
            if not available1:
                print(Fore.RED + Style.BRIGHT + "This is a tie!")
                break

            marker_result2 = place_marker2(player_symbols, avnums, config)
            available2 = marker_result2[0]
            config = marker_result2[1]
            print(f"Available positions include: {available2}")
            win = check_win(player_symbols, config)
            if win == True:
                break
            if not available2:
                print(Fore.RED + Style.BRIGHT + "This is a tie!")
                break

        ready = input("Are you ready to play? Enter Yes or No: ")

    print("Thanks for trying out this game, hope you've had fun:)")

game()
