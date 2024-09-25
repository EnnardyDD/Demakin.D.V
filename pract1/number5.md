Задача 5

Написать программу для регистрации пользовательской команды (правильные права доступа и копирование в /usr/local/bin).

Например, пусть программа называется reg:

```
./reg banner
```

В результате для banner задаются правильные права доступа и сам banner копируется в /usr/local/bin.

## Решение 

```
chmod +x reg.py
sudo cp reg.py /usr/local/bin/reg
reg
```

![image](https://github.com/user-attachments/assets/ac7502dc-2369-482f-986c-9dcc3c731d56)
