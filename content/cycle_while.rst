**Работа с циклом while в оболочке bash**
=========================================
:date: 2020-05-22
:summary: Работа с циклом while
:status: published
:author: Тин П.А.

.. default-role:: code
.. contents:: Содержание

Теоретическая часть
-------------------
Определение цикла и общий вид
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
**Цикл** – последовательность, которая позволяет выполнить определенный участок кода необходимое количество раз. Оболочкой bash поддерживаются несколько типов циклов: for, while, until. Здесь будет рассмотрен цикл while.

Суть цикла while заключается в том, что он будет повторяться до тех пор, **пока будет выполняться условие**, указанное в объявлении цикла. Bash цикл while имеет такой синтаксис:

.. code-block:: bash
 
 While[условие] do
     команда1
     команда2
     …
     командаN
 done

Сначала выполняется проверка на правильность условия. Если true, то выполняется набор команд, затем снова выполняется проверка, и так, пока условие не вернет отрицательный результат.

Использование
~~~~~~~~~~~~~~~~~~~~~~~~~
Примеры кода
""""""""""""

.. code-block:: bash

 # !/bin/bash
 x = 1
 while [ $x –lt 5]         # -lt – знак «меньше»
     do 
     echo “Значение счётчика: $x”		# echo - вывод
     x = $(($x + 1))
 done

Здесь мы выставляем значение счетчика в 1, затем сравниваем его с 5. Если верно, выводим значение счетчика и увеличиваем его на 1.

С помощью while можно **прочитать несколько строк** из стандартного ввода:

.. code-block:: bash

 # !/bin/bash
 while read line
     do
     echo $line
 done

Программа будет запрашивать новые строки, пока не будет получен **символ конца файла** с помощью сочетания клавиш **CTRL + D**. 

Выход из цикла
"""""""""""""""
**Выход из цикла** – с помощью команды **break:**

.. code-block:: bash

 #! /bin/bash
 number = 1
 while [$number –lt 10] do
     if [$number –eq 9] then
        * break
     fi
     echo “Номер равен: $number”
     number = $(($number + 1))
 done

Здесь выход из цикла осуществляется командой break в теле if, когда счетчик достигнет 9.

Бесконечный цикл
""""""""""""""""""
Можно так же создать **бесконечный цикл**:

.. code-block:: bash

 # !/bin/bash
 count = 0
 while [1=1]
 do
     ((count++))
     echo $count
 done

**Выйти** можно, использовав сочетание клавиш **CTRL + C**.

Создание файлов в цикле
"""""""""""""""""""""""
.. code-block:: bash

 #! /bin/bash
 A = 123
 B = 456
 C = 789
 while [$ C -gt 779 ] do
     touch /home/$A.$B.$C
     C = $(($C - 1))
 done
 echo

Здесь с помощью команды touch создаём в папке home файлы с именами 123.456.789, 123.456.788, 123.456.787 и т.д. до 123.456.780, т.е. пока выполняется условие цикла, что C>779.

Практическая часть
------------------
**Задача**

Написать программу, которая создает в текущей папке файлы с именами от 1 до 10.

