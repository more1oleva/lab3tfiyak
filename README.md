# Лабораторная работа №3. Разработка синтаксического анализатора (парсера).
## Объявление структуры на языке С#
Цель работы: изучить назначение синтаксического анализатора, спроектировать алгоритм и выполнить программную реализацию парсера. \
**В соответствии с вариантом задания необходимо:**
1. Разработать автоматную грамматику.
2. Спроектировать граф конечного автомата (перейти от автоматной грамматики к конечному автомату).
3. Выполнить программную реализацию алгоритма работы конечного автомата.
4. Встроить разработанную программу в интерфейс текстового редактора, созданного на первой лабораторной работе.
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
