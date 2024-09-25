## Задача 3

Написать программу banner средствами bash для вывода текстов, как в следующем примере (размер баннера должен меняться!):

```
[root@localhost ~]# ./banner "Hello from RTU MIREA!"
+-----------------------+
| Hello from RTU MIREA! |
+-----------------------+
```

Перед отправкой решения проверьте его в ShellCheck на предупреждения.

## Решение

```
text="Hello from RTU MIREA!"; text_length=${#text}; line=$(printf "%${text_length}s" | tr ' ' '-'); echo "+ ${line} +"; echo "| ${text} |"; echo "+ ${line} +"
```
![image](https://github.com/user-attachments/assets/ab78a5ee-68a3-453a-9532-1365f60970c5)
