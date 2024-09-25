## Задача 2

Вывести данные /etc/protocols в отформатированном и отсортированном порядке для 5 наибольших портов, как показано в примере ниже:

```
[root@localhost etc]# cat /etc/protocols ...
142 rohc
141 wesp
140 shim6
139 hip
138 manet
```

## Решение 

```
cat /etc/protocols | sort –nk2 -r | head -n5 | awk '{print $2, $1}'
```
![image](https://github.com/user-attachments/assets/f1203a6b-3404-4c0b-b1fd-495548556fcd)
