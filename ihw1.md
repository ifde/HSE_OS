# ИДЗ #1
# Фролов Иван Григорьевич, БПИ-235

## Применение каналов при обработке строк символов

### Задание (Вариант 38): Разработать программу, которая ищет в ASCII–строке заданную подстроку и возвращает индекс первого символа первого вхождения подстроки в строке. Подстрока вводится как дополнительный аргумент.

В папке уже присутствуют исполняемые файлы для всех программ.  
Их можно запустить командами:  

`./4 source1.txt res.txt "No such string"`  
`.5/ source5.txt res.txt "Her hair, nor loose"`  
`./6 source1.txt res.txt "It works!"`  
`./7 source2.txt res.txt "maid full pale"`  

Программа на 8-баллов - это консольное приложение из двух файлов.  
Их можно либо запустить по отдельности в разных терминалах, либо использовать исполняемый скрипт `run8.sh`.  
Я постарался сделать, чтобы он работал как на MacOS, так и на Linux.  
Для MacOS точно работает, для Linux - не знаю)  

```
./8_read res.txt "The carcass of beauty spent and done:"

./8_write source3.txt

ИЛИ

run8.sh
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


Исходные файлы с текстом: 
`source1.txt`  
`source2.txt`  
`source3.txt`  
`source4.txt`  
`source5.txt`  
