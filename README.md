# Tic-Tac-Toe

# write your code here
symbol = input('Enter cells: ')
row_winnings = [[i for i in symbol[:3]], [i for i in symbol[3:6]], [i for i in symbol[6:]]] 
column_winnings = [[symbol[i] for i in [0, 3, 6]], [symbol[i] for i in [1, 4, 7]], [symbol[i] for i in [2, 5, 8]]]
diameter_winnings = [[symbol[i] for i in [0, 4, 8]], [symbol[i] for i in [2, 4, 6]]]
all_winnings = row_winnings + column_winnings + diameter_winnings
# print first part of the output
row0 = ' '.join(symbol[:3])
row1 = ' '.join(symbol[3:6])
row2 = ' '.join(symbol[6:])
print('---------')
print(f'| {row0} |')
print(f'| {row1} |')
print(f'| {row2} |')
print('---------')
# check if winning states of char occur
def winning(char, overall_list):
    for sublists in overall_list:
        if sublists.count(char) == 3:
            return True
# check and print current state
if abs(symbol.count('X') - symbol.count('O')) > 1 or winning('X', all_winnings) and winning('O', all_winnings):
    print('Impossible')
elif winning('X', all_winnings):
    print('X wins')
elif winning('O', all_winnings):
    print('O wins')
elif '_' in symbol or ' ' in symbol:
    print('Game not finished')
else:
    print('Draw')
