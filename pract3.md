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
