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
![граф](https://github.com/more1oleva/lab3tfiyak/assets/118746926/8af70a79-479e-49ec-a9ae-ae26358e90fc)

### Тестовые примеры
