# ИДЗ #1
# Фролов Иван Григорьевич, БПИ-235

## Применение каналов при обработке строк символов

### Задание (Вариант 24): Разработать программу, которая ищет в ASCII–строке заданную подстроку и возвращает индекс первого символа первого вхождения подстроки в строке. Подстрока вводится как дополнительный аргумент.

В папке уже присутствуют исполняемые файлы для всех программ.  
Их можно запустить командами:  

`./4 source1.txt res.txt "No such string"`  
`.5/ source5.txt res.txt "Her hair, nor loose"`  
`./6 source1.txt res.txt "It works!"`  
`./7 source2.txt res.txt "maid full pale"`  

Программа на 8 баллов - это консольное приложение из двух файлов.  
Их можно либо запустить по отдельности в разных терминалах, либо использовать исполняемый скрипт `run8.sh`.  
Я постарался сделать, чтобы он работал как на MacOS, так и на Linux.  
Для MacOS точно работает, для Linux - не знаю)  

То же самое для программ на 9 и на 10 баллов.  

```
./8_read res.txt "The carcass of beauty spent and done:"

./8_write source3.txt

ИЛИ

run8.sh
```

```
./9_read source3.txt res.txt 

./9_write "The carcass of beauty spent and done:"

ИЛИ

run9.sh
```

```
./10_read source1.txt res.txt

./10_write "awesome"

ИЛИ

run10.sh
```

Скриншоты работы программ на разных тестовых файлах:  
![image](https://github.com/user-attachments/assets/50fa0bbd-88af-49e5-9f2b-4d1b39b7aaad)  
![image](https://github.com/user-attachments/assets/16b91122-97a9-4dd1-b820-0293c36b6cbb)
(ищем строку "It works!")

![image](https://github.com/user-attachments/assets/bfb20694-e0fc-438d-9e58-c26776a02d12)  
![image](https://github.com/user-attachments/assets/b70e9356-2240-43d5-b5de-6ef545677187)  
"No such string"  

![image](https://github.com/user-attachments/assets/7bd73dcb-55b7-402f-b5d0-d8d123d8776e)  
![image](https://github.com/user-attachments/assets/938caf65-ae84-464c-8a93-fc5c470c427a)  
"Her hair, nor loose"  

![image](https://github.com/user-attachments/assets/293948ec-57bb-429b-879a-71f3dae3beae)  
![image](https://github.com/user-attachments/assets/8e447add-fd91-42d7-8fd7-cc1c2b727c89)  
"The carcass of beauty spent and done:"  

![image](https://github.com/user-attachments/assets/5bebde18-d680-4705-b838-b7e0328392d5)  
![image](https://github.com/user-attachments/assets/1efde004-fce7-4c96-978f-d53e975d74df)  
"maid full pale"  

<img width="588" alt="image" src="https://github.com/user-attachments/assets/9c0a3d8b-f3c9-4253-a0aa-c83f680fb12e" />
<img width="272" alt="image" src="https://github.com/user-attachments/assets/8e06032d-941d-497c-9a14-2c8b168977de" />
"awesome"

==========================
==========================

### Исходные файлы с текстом: 
`source1.txt`  
`source2.txt`  
`source3.txt`  
`source4.txt`  
`source5.txt`  


## Схемы работы программ 

### Программа 4
 Схема работы:  
 * Первый процесс (Родитель): читает данные из входного файла и передаёт их второму процессу через неименованный канал pipe1 (создаем через fifo()).  
 * Второй процесс (Child 1): получает данные, ищет подстроку, отправляет результат третьему процессу через неименованный канал pipe2 (создаем через pipe()).  
 * Третий процесс (Child 2): получает результат из pipe2 и записывает его в выходной файл.

### Программа 5
 Схема работы:  
 * Первый процесс (Родитель): читает данные из входного файла и передаёт их второму процессу через именованный канал pipe1 (создаем через mkfifo).  
 * Второй процесс (Child 1): получает данные, ищет подстроку, отправляет результат третьему процессу через именованный канал pipe2 (создаем через mkfifo).  
 * Третий процесс (Child 2): получает результат из pipe2 и записывает его в выходной файл.  

### Программа 6
 Схема работы:  
 * Первый процесс (Родитель): читает данные из входного файла и передаёт их второму процессу через неименованный канал (создаем через pipe()).  
 * Второй процесс (дочерний от первого): получает данные, ищет подстроку, отправляет результат обратно родителю через неименованный канал (создаем через pipe()).  
 * Первый процесс ждет завершения дочернего процесса, получает результат из канала и записывает его в выходной файл.  

### Программа 7
Схема работы:  
 * Первый процесс (Родитель): читает данные из входного файла и передаёт их второму процессу через именованный канал pipe_name1 (создаем через mkfifo()).  
 * Второй процесс (дочерний от первого): получает данные, ищет подстроку, отправляет результат обратно родителю через именованный канал pipe_name2 (создаем через mkfifo()).  
 * Первый процесс ждет завершения дочернего процесса, получает результат из канала pipe_name2 и записывает его в выходной файл.  

### Программа 8
Схема работы:  
 * Первый процесс Read: читает данные из входного файла и передаёт их второму процессу через именованный канал PIPE_IN (создаем через mkfifo()).  
 * Второй процесс Write (независимый от первого и исполняющийся в другом терминале): получает данные из именованного канала, ищет подстроку передает индекс ее вхождения через именованный канал PIPE_OUT (создаем через mkfifo()) обратно первому процессу  
 * Первый процесс записывает результат в выходной файл  

### Программа 9
Схема работы:  
 * Первый процесс Read: читает данные из входного файла по порциям 128 байт и передаёт их второму процессу через именованный канал PIPE_IN (создаем через mkfifo()).  
 * Второй процесс Write (независимый от первого и исполняющийся в другом терминале): получает данные из именованного канала, ищет подстроку передает индекс ее вхождения через именованный канал PIPE_OUT (создаем через mkfifo()) обратно первому процессу  
 * Первый процесс записывает результат в выходной файл

### Программа 10
Схема работы:  
 * Первый процесс Read: читает данные из входного файла по порциям 128 байт и передаёт их второму процессу через именованный канал очередь сообщений.  
 * Второй процесс Write (независимый от первого и исполняющийся в другом терминале): получает данные из именованного канала, ищет подстроку передает индекс ее вхождения через очередь сообщений обратно первому процессу  
 * Первый процесс записывает результат в выходной файл




