## Задача 1

Вывести служебную информацию о пакете matplotlib (Python). Разобрать основные элементы содержимого файла со служебной информацией из пакета. Как получить пакет без менеджера пакетов, прямо из репозитория?

## Решение

```
npm info matplotlib
```

![image](https://github.com/user-attachments/assets/33f75bec-8254-4f33-86e2-368d1aea172a)

## Задача 2

Вывести служебную информацию о пакете express (JavaScript). Разобрать основные элементы содержимого файла со служебной информацией из пакета. Как получить пакет без менеджера пакетов, прямо из репозитория?

## Решение

```
npm info express
```

![image](https://github.com/user-attachments/assets/3bbd8a19-a1df-4450-a7b7-42793d54e536)

## Задача 3

Сформировать graphviz-код и получить изображения зависимостей matplotlib и express.

## Решение

```

```

## Задача 4

**Следующие задачи можно решать с помощью инструментов на выбор:**

* Решатель задачи удовлетворения ограничениям (MiniZinc).
* SAT-решатель (MiniSAT).
* SMT-решатель (Z3).

Изучить основы программирования в ограничениях. Установить MiniZinc, разобраться с основами его синтаксиса и работы в IDE.

Решить на MiniZinc задачу о счастливых билетах. Добавить ограничение на то, что все цифры билета должны быть различными (подсказка: используйте all_different). Найти минимальное решение для суммы 3 цифр.

## Решение

```
include "globals.mzn";

array[1..6] of var 0..9: digits;
constraint all_different(digits);

var int: sum_first = sum(digits[1..3]);
var int: sum_last = sum(digits[4..6]);

constraint sum_first = sum_last;
solve minimize sum_first;
```

![image](https://github.com/user-attachments/assets/76fd72b5-d90c-4715-a59d-29679d4bb222)

## Задача 5

Решить на MiniZinc задачу о зависимостях пакетов для рисунка, приведенного ниже.

![image](https://github.com/user-attachments/assets/01860fbd-3c59-4ee8-97e7-7c3fdbc56339)

## Решение

```
set of int: Menu = {100, 110, 120, 130, 150};
set of int: Dropdown = {230, 220, 210, 200, 180};
set of int: Icons = {100, 200};

var Menu: menu;
var Dropdown: dropdown;
var Icons: icons;

constraint if menu >= 110 then dropdown >= 200 else dropdown = 180 endif;

constraint if dropdown <= 200 /\ dropdown > 180 then icons = 200 else icons = 100 endif;

solve satisfy;
```

![image](https://github.com/user-attachments/assets/2b08afb5-b074-47eb-8315-ccbed608161a)

## Задача 6

Решить на MiniZinc задачу о зависимостях пакетов для следующих данных:

```
root 1.0.0 зависит от foo ^1.0.0 и target ^2.0.0.
foo 1.1.0 зависит от left ^1.0.0 и right ^1.0.0.
foo 1.0.0 не имеет зависимостей.
left 1.0.0 зависит от shared >=1.0.0.
right 1.0.0 зависит от shared <2.0.0.
shared 2.0.0 не имеет зависимостей.
shared 1.0.0 зависит от target ^1.0.0.
target 2.0.0 и 1.0.0 не имеют зависимостей.
```

## Решение

```
set of int: Foo = {100, 110};
set of int: Target = {100, 200};
set of int: Left = {100};
set of int: Right = {100};
set of int: Shared = {100, 200};

var Foo: foo;
var Target: target;
var Left: left;
var Right: right;
var Shared: shared;

constraint if left < 100 then shared = 100 else target = 200 endif;

constraint if right >= 100 then shared = 200 else shared = 100 endif;

solve satisfy;
```

![image](https://github.com/user-attachments/assets/a17ad2a8-1e5c-497e-92b6-13096a2d1f25)

## Задача 7

Представить задачу о зависимостях пакетов в общей форме. Здесь необходимо действовать аналогично реальному менеджеру пакетов. То есть получить описание пакета, а также его зависимости в виде структуры данных. Например, в виде словаря. В предыдущих задачах зависимости были явно заданы в системе ограничений. Теперь же систему ограничений надо построить автоматически, по метаданным.

## Решение

```

```
