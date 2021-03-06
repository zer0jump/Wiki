# Справка по GDB

## Компиляция с отладочными символами
`gcc -g <filename>`

## Запуск
`gdb -q <filename>`

## Команды
- `break main` (поставить точку останова перед функцией main)
- `run` (запуск выполнения программы до точки останова или др. прерываний)
- `continue` или `cont` (продолжение выполнения программы)
- `quit` (закончить отладку)
- `list` (вывести 10 строк кода после текущего положения)
- `disassemble main` (дизассемблировать функцию main)
- `info register eip` или `i r eip` (вывести информацию о регистре EIP)
- `x/o $eip` (отобразить одно слово в восьмеричном представлении по адресу из регистра EIP)
- `x/t $eip` (тоже самое, только в двоичном представлении)
- `x/u $eip` (тоже самое, только в десятичном беззнаковом представлении)
- `x/d $eip` (тоже самое, только в десятичном представлении)
- `x/2xb $eip` (отобразить 2 байта по адресу из регистра EIP в шестнадцатиричном виде)
- `x/3xh $eip` (отобразить 3 полуслова (полуслово = 2 байта) по адресу из регистра EIP в шестнадцатиричном виде)
- `x/4xw $eip` (отобразить 4 слова (слово = 4 байта) по адресу из регистра EIP в шестнадцатиричном виде)
- `x/5xg $eip` (отобразить 5 гигантских слов (гигантское слово = 8 байтов) по адресу из регистра EIP в шестнадцатиричном виде)
При просмотре слов и полуслов порядок байтов приводится к естественному. Тогда как при последовательном выводе по одному байту байты выводятся так как расположены в памяти (то есть от младшего к старшему)
- `x/i $eip` (отобразить дизассемблированную инструкцию по адресу из EIP)
- `x/x $ebp - 4` (вывести в шестнадцатиричном виде слово, начиная с адреса, отстоящего на 4 байта вверх от адреса, на который указывает регистр EBP)
- `print $ebp - 4` (произвести вычисление адреса и записать значение по адресу в переменную)
- `x/4xb $1` (вывести в нужном формате значение, записанное в переменную $1 с помощью команды `print`)
- `nexti` (выполнить инструкцию и перейти к следующей)
- `x/2cb 0x8048484` (отобразить 2 байта в виде ASCII-кода и соответствующего ему символа по адресу 0x8048484)
- `x/s 0x8048484` (отобразить строку по адресу 0x8048484)
- `x/s pointer` (отобразить в строковом виде значение, на которое ссылается указатель 'pointer')
- `x/xw &pointer` (отобразить значение переменной указателя 'pointer', т.е. не значение по адресу, а сам адрес, который хранится в переменной указателя; '&' - оператор взятия адреса)
- `bt` (обратная трассировка вызовов функций с помощью стека)
- `bt full` (выполнить обратную трассировку стека и показать информацию о всех локальных переменных в каждом стековом кадре)
