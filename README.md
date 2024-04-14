# Лабораторная работа №3. Разработка синтаксического анализатора (парсера).
## Объявление структуры на языке С#
Цель работы: изучить назначение синтаксического анализатора, спроектировать алгоритм и выполнить программную реализацию парсера. \
**В соответствии с вариантом задания необходимо:**
1. Разработать автоматную грамматику.
2. Спроектировать граф конечного автомата (перейти от автоматной грамматики к конечному автомату).
3. Выполнить программную реализацию алгоритма работы конечного автомата.
4. Встроить разработанную программу в интерфейс текстового редактора, созданного на первой лабораторной работе.
### Примеры допустимых строк
![309557916-fc6f1710-46ab-4f0e-970f-2c3ce1689ff6](https://github.com/more1oleva/lab3tfiyak/assets/118746926/e8c59611-3ea1-4764-9bf1-0ee1f1c37ea4)

### Грамматика:
G[<ЦК> = <целочисленная константа>]: \
VT = { ‘public’, ‘private’, ‘protected’, ‘struct’, ‘int’, ‘double’, ‘bool’, ‘string’, ‘{’, ‘}’, ‘;’, ‘a’…’z’, ‘A’…’Z’, ‘0’…’9’, ‘_’ } \
VN = { DEF, STRUCT, NAMESTRUCT, NAMESTRUCTREM, FIELD, TYPE, STRUCTEND, FIELDNAME, FIELDNAMEREM } \
P = { 
1. DEF -> (public | private | protected) STRUCT
2. STRUCT -> struct NAMESTRUCT
3. NAMESTRUCT -> letter NAMESTRUCTREM
4. NAMESTRUCTREM -> (letter | digit | _) NAMESTRUCTREM | { FIELD
5. FIELD -> (public | private | protected) TYPE | } STRUCTEND
6. TYPE -> (int | double | bool | string) FIELDNAME
7. FIELDNAME -> letter FIELDNAMEREM
8. FIELDNAMEREM -> (letter | digit | _) FIELDNAMEREM | ; FIELD
9. STRUCTEND -> ; \
}
### Классификация грамматики
Согласно классификации Хомского, грамматика G[Z] является полностью автоматной.
### Граф конечного автомата
![граф](https://github.com/more1oleva/lab3tfiyak/assets/118746926/192cb7aa-0e21-443f-96c0-a337ec5fb5e1)


### Тестовые примеры
**Тест №1** Ошибок нет
![Снимок](https://github.com/more1oleva/lab3tfiyak/assets/118746926/39fc2cc1-938f-4d46-af6f-9c0286dd16cb) \
**Тест №2** Ошибки в ключевых словах \
![Снимок](https://github.com/more1oleva/lab3tfiyak/assets/118746926/fd8d4893-1103-4789-8ebe-f74b052286fd) \
**Тест №3** Неподходящие символы \
![Снимок](https://github.com/more1oleva/lab3tfiyak/assets/118746926/9484ec2d-6aa5-4ab0-a1db-c30d26cbfdc3) \
**Тест №4** Отсутствие ключевых слов \
![Снимок](https://github.com/more1oleva/lab3tfiyak/assets/118746926/066972c1-d36f-4d7c-b6d2-c929fb2cb9bf)



