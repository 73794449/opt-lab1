# OPT-LAB1: "РОЗРОБКА ЛЕКСИЧНОГО АНАЛІЗАТОРА"
## Usage

    ./opt-lab1 <filename>
    -f <filename> 		Input filename
    -o <filename>		Output filename
    -v					Verbose output

## Мета лабораторної роботи
Метою лабораторної роботи «Розробка лексичного аналізатора» є засвоєння теоретичного матеріалу та набуття практичного досвіду і практичних навичок розробки лексичних аналізаторів (сканерів). 
## Постановка задачі 
Розробити програму лексичного аналізатора (ЛА) для підмножини мови програмування SIGNAL. 
Лексичний аналізатор має забезпечувати наступні дії: 
* видалення (пропускання) пробільних символів: пробіл (код ASCII 32), повернення каретки (код ASCII 13); перехід на новий рядок (код ASCII 10), горизонтальна та вертикальна табуляція (коди ASCII 9 та 11), перехід на нову сторінку (код ASCII 12); 
* згортання ключових слів; 
* згортання багато-символьних роздільників (якщо передбачаються граматикою варіанту); 
* згортання констант із занесенням до таблиці значення та типу константи (якщо передбачаються граматикою варіанту); 
* згортання ідентифікаторів; 
* видалення коментарів, заданих у вигляді (*<текст коментаря>*); 
* формування рядка лексем з інформацією про позиції лексем; 
* заповнення таблиць ідентифікаторів та констант інформацією, отриманою під час згортки лексем; 
* виведення повідомлень про помилки.

## Варіант 23
1. <signal-program> --> <program>
2. <program> --> PROGRAM <procedure-identifier> ;
<block>.
3. <block> --> <declarations> BEGIN <statements-list> END
4. <declarations> --> <constant-declarations>
5. <constant-declarations> --> CONST <constantdeclarations-list> |
<empty>
6. <constant-declarations-list> --> <constantdeclaration> <constant-declarations-list> |
<empty>
7. <constant-declaration> --> <constant-identifier> =
<constant>;
8. <statements-list> --> <statement> <statements-list> |
<empty>
9. <statement> --> CASE <expression> OF <alternativeslist> ENDCASE ;
10. <alternatives-list> --> <alternative> <alternativeslist> |
<empty>
11. <alternative> --> <expression> : /<statements-list>\
12. <expression> --> <summand> <summands-list> |
- <summand> <summands-list>
13. <summands-list> --> <add-instruction> <summand>
<summands-list> |
<empty>
14. <add-instruction> --> + |
-
15. <summand> --> <variable-identifier> |
<unsigned-integer>
16. <constant> --> <unsigned-integer>
17. <variable-identifier> --> <identifier>
18. <constant-identifier> --> <identifier>
19. <procedure-identifier> --> <identifier>
20. <identifier> --> <letter><string>
21. <string> --> <letter><string> |
<digit><string> |
<empty>
22. <unsigned-integer> --> <digit><digits-string>
23. <digits-string> --> <digit><digits-string> |
<empty>
24. <digit> --> 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9
25. <letter> --> A | B | C | D | ... | Z


## Building

    git clone https://github.com/73794449/opt-lab1.git
    cd ./opt-lab1
    gcc -g -O2 ./src/*.c -o opt-lab1

