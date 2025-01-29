# Фролов Иван Григорьевич, БПИ-235, ДЗ-2

### Скрипт if -  проверяет четность числа

```
# IS EVEN

#!/bin/bash

echo -n "Enter a number >" # input
read number

# Check if even
if [ $[number % 2] -eq 0 ]; then
  echo "Число $number чётное!"
else
  echo "Число $number нечётное!"
fi
```
### Скриншот работы программы:  
<img width="470" alt="image" src="https://github.com/user-attachments/assets/7ded09ca-c952-438d-9c2f-9be4a449a8ee" />  

### Скрипт while - считаем от 1 до 10

```
# Count from 1 to 10

#!/bin/bash

parametr1=$1  # parametr1 = первому параметру скрипта
script_name=$0  # присваиваем script_name значение имени скрипта

# Вывод строки с подстановкой переменных
echo "Вы запустили скрипт с именем $script_name и параметром $parametr1"

# Вторая строка не будет интерпретировать переменные из-за одинарных кавычек
echo 'Вы запустили скрипт с именем $script_name и параметром $parametr1'

cnt=1

# Count while cnt is less than or equal to 10
while [ $cnt -le 10 ]; do
  echo "Значение: $cnt" # Print current value
((cnt++))  # Увеличиваем счетчик на 1
done

exit 0  # Выход с кодом 0 (удачное завершение работы скрипта)
```
### Скриншот работы программы:  
<img width="470" alt="image" src="https://github.com/user-attachments/assets/7ded09ca-c952-438d-9c2f-9be4a449a8ee" />  

### Функция НОД

```
# IS EVEN

#!/bin/bash

parametr1=$1  # parametr1 = первому параметру скрипта
script_name=$0  # присваиваем script_name значение имени скрипта

# Вывод строки с подстановкой переменных
echo "Вы запустили скрипт с именем $script_name и параметром $parametr1"

# Вторая строка не будет интерпретировать переменные из-за одинарных кавычек
echo 'Вы запустили скрипт с именем $script_name и параметром $parametr1'

# Calculate GCCD
function gcd {
  a=$1
  b=$2
  
  while ((b != 0)); do
    temp=$b
    ((b = a % b))
    a=$temp
  done
  
  echo $a # Return GCD
}

# Input two numbers
echo "Enter two integer numbers:"
read a
read b

result=$(gcd $a $b)  # Call gcd(a, b)
echo "GCD of $a and $b is $result"

exit 0  # Выход с кодом 0 (удачное завершение работы скрипта)
```

### Скриншот работы программы:  
<img width="466" alt="image" src="https://github.com/user-attachments/assets/2aee2d61-3118-4c27-b4ef-d33e9e55daf7" />  





