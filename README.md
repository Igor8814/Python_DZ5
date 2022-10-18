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