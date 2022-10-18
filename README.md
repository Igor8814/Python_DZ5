Создайте программу для игры с конфетами
человек против человека.
Условие задачи: На столе лежит 2021 конфета.
Играют два игрока делая ход друг после друга.
Первый ход определяется жеребьёвкой. За один ход
можно забрать не более чем 28 конфет. Все конфеты
оппонента достаются сделавшему последний ход. Сколько
конфет нужно взять первому игроку, чтобы забрать 
все конфеты у своего конкурента?
a) Добавьте игру против бота
b) Подумайте как наделить бота ""интеллектом""
~~~
from itertools import count
from random import randint


def humah_vs_human():
    human1 = input('Введите ваше имя: ')
    human2 = input('Введите ваше имя: ')
    sweets_total = 2021
    max_one_move = 28
    count = 0
    x = randint(1,2)
    if x == 1:
        first_move1 = human1
        first_move2 = human2
    else:
        first_move1 = human2
        first_move2 = human1
    while sweets_total > 0 :
        if count == 0:
            step = int(input(f'Твой ход {first_move1}: '))
            if step > max_one_move:
                step = int(input(f'Число должно быть не больше 28 : '))
            sweets_total = sweets_total - step
        if sweets_total > 0:
            print(f'Осталось {sweets_total}')
            count = 1
        else:
            print('Осталось 0')  
        if count == 1:
            step = int(input(f'Твой ход {first_move2}: '))      
            if step > max_one_move:
                step = int(input(f'Число должно быть не больше 28 : '))
            sweets_total = sweets_total - step
        if sweets_total > 0:
            print(f'Осталось {sweets_total}')  
            count = 0
        else:
            print('ничего не осталось')          
    if count == 1:
        print(f'победил {first_move1}')        
    if count == 0:
        print(f'победил {first_move2}')                    
               
humah_vs_human()
~~~ 
Напишите программу, 
удаляющую из текста все слова,
содержащие ""абв"".
~~~
text = 'авиифбвабв sdfffgc аалллауддыд абвкуувабв какабвкааап аьвабвабв'


def del_words(text):
    text = list(filter(lambda x: 'абв' not in x, text.split()))
    return " ".join(text)


text = del_words(text)
print(text)
~~~
Создайте программу для игры в ""Крестики-нолики"".
~~~
from ast import While


playing_field = list(range(1, 10))
coard_win = [(1, 2, 3), (4, 5, 6), (7, 8, 9), (1, 4, 7), (2, 5, 8), (3, 6, 9), (1, 5, 9), (3, 5, 7)]

def print_fild():
    print('-------------')
    for i in range(3):
        print('|', playing_field[0 + i * 3], '|', playing_field[1 + i * 3], '|', playing_field[2 + i * 3], '|')
    print('------------')
    
def game_progress(player_token):
    while True:
        value = input(f'Куда поставить? {player_token} ')    
        if not (value in '123456789'):
            print('Неправильный ввод')
            continue
        value = int(value)
        if str(playing_field[value - 1]) in 'XO':
            print('Тут занято')
            continue
        playing_field[value - 1] = player_token
        break

def outcome_game():
        for g in coard_win:
            if (playing_field[g[0] - 1] == playing_field[g[1] - 1] == playing_field[g[2] - 1]):
                return playing_field[g[1] - 1]
        else:
            return False
def main():
    count = 0
    while True:
        print_fild()
        if count % 2 == 0:
            game_progress('X')
        else:
            game_progress('O')
        if count > 3:
            winner = outcome_game()
            if winner:
                print_fild()
                print(f'{winner} Ты выиграл!')
                break  
        count += 1
        if count > 8:
            print_fild()
            print('Ничья!')      
            break    
main()
~~~
Реализуйте RLE алгоритм: реализуйте модуль
сжатия и восстановления данных.
Входные и выходные данные хранятся 
в отдельных текстовых файлах.
~~~
from unittest import result


s = 'aaaddddffffttt'

def encode(s):
    encoding = ""
    i = 0
    while i < len(s):
        count = 1
        while i + 1 < len(s) and s[i] == s[i + 1]:
            count = count + 1
            i = i + 1
        encoding += str(count) + s[i]
        i = i + 1
    return encoding
print(encode(s))

def decoding(text):
    number = ''
    result = ''
    for i in range(len(text)):
        if not text[i].isalpha():
            number += text[i]
        else:
            result = result + text[i] * int(number)
            number = ''
           
    return result
print(decoding(encode(s)))
~~~                           