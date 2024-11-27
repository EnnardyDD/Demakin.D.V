# Практическое задание №4. Системы контроля версий

П.Н. Советов, РТУ МИРЭА

Работа с Git.

## Задача 1

На сайте https://onlywei.github.io/explain-git-with-d3 или http://git-school.github.io/visualizing-git/ (цвета могут отличаться, есть команды undo/redo) с помощью команд эмулятора git получить следующее состояние проекта (сливаем master с first, перебазируем second на master): см. картинку ниже. Прислать свою картинку.

![image](https://github.com/user-attachments/assets/ac761f73-7ad9-4d9b-8895-ac1471097d66)

## Решение

```
git commit
git branch first
git commit
git commit
git checkout first
git tag in
git commit
git commit
git checkout master
git merge first
git checkout in
git branch second
git checkout second
git commit
git commit
git rebase master
git checkout master
git merge second
git checkout in
```

![image](https://github.com/user-attachments/assets/951f1bde-210b-4608-9449-05e57d7325ac)

## Задача 2

Создать локальный git-репозиторий. Задать свои имя и почту (далее – coder1). Разместить файл prog.py с какими-нибудь данными. Прислать в текстовом виде диалог с git.

## Решение

```
git init --bare server.git
git remote add server ../server.git/
git remote -v
git push server master
git clone server.git coder2
echo "Test" >> readme.md
git add readme.md
git commit -m "test info"
git push server master
echo "Test2" >> readme.md
git add readme.md
git config user.name "coder2"
git config user.email "coder2@gmail.com"
git commit -m "test2 info"
git pull --no-rebase origin master
git add readme.md
git commit -m "Final"
git push origin master
git log --graph --all
```


## Задача 3

Создать рядом с локальным репозиторием bare-репозиторий с именем server. Загрузить туда содержимое локального репозитория. Команда git remote -v должна выдать информацию о server! Синхронизировать coder1 с server.

Клонировать репозиторий server в отдельной папке. Задать для работы с ним произвольные данные пользователя и почты (далее – coder2). Добавить файл readme.md с описанием программы. Обновить сервер.

Coder1 получает актуальные данные с сервера. Добавляет в readme в раздел об авторах свою информацию и обновляет сервер.

Coder2 добавляет в readme в раздел об авторах свою информацию и решает вопрос с конфликтами.

Прислать список набранных команд и содержимое git log.

Пример лога коммитов:

```
*   commit a457d748f0dab75b4c642e964172887de3ef4e3e
|\  Merge: 48ce283 d731ba8
| | Author: Coder 2 <coder2@corp.com>
| | Date:   Sun Oct 11 11:27:09 2020 +0300
| | 
| |     readme fix
| | 
| * commit d731ba84014d603384cc3287a8ea9062dbb92303
| | Author: Coder 1 <coder1@corp.com>
| | Date:   Sun Oct 11 11:22:52 2020 +0300
| | 
| |     coder 1 info
| | 
* | commit 48ce28336e6b3b983cbd6323500af8ec598626f1
|/  Author: Coder 2 <coder2@corp.com>
|   Date:   Sun Oct 11 11:24:00 2020 +0300
|   
|       coder 2 info
| 
* commit ba9dfe9cb24316694808a347e8c36f8383d81bbe
| Author: Coder 2 <coder2@corp.com>
| Date:   Sun Oct 11 11:21:26 2020 +0300
| 
|     docs
| 
* commit 227d84c89e60e09eebbce6c0b94b41004a4541a4
  Author: Coder 1 <coder1@corp.com>
  Date:   Sun Oct 11 11:11:46 2020 +0300
  
      first commit
```

## Решение

```
git init --bare server.git
git remote add server ../server.git/
git remote -v
git push server master
git clone server.git coder2
echo "Test" >> readme.md
git add readme.md
git commit -m "test info"
git push server master
echo "Test2" >> readme.md
git add readme.md
git config user.name "coder2"
git config user.email "coder2@gmail.com"
git commit -m "test2 info"
git pull --no-rebase origin master
git add readme.md
git commit -m "Final"
git push origin master
git log --graph --all
```

```
(base) mary@iMac-Mary mirea_config % cd server
(base) mary@iMac-Mary server % git init --bare
Initialized empty Git repository in /Users/mary/Desktop/mirea_config/server/
(base) mary@iMac-Mary server % cd ..
(base) mary@iMac-Mary mirea_config % cd condig
cd: no such file or directory: condig
(base) mary@iMac-Mary mirea_config % cd config
(base) mary@iMac-Mary config % git remote add server ../server
(base) mary@iMac-Mary config % git remote -v
server	../server.git (fetch)
server	../server.git (push)
(base) mary@iMac-Mary config % git push server main
Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Writing objects: 100% (3/3), 213 bytes | 213.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
To ../server
 * [new branch]      main -> main
(base) mary@iMac-Mary mirea_config % git clone server "config 2"
Cloning into 'config 2'...
done.
(base) mary@iMac-Mary mirea_config %  cd "config 2"
(base) mary@iMac-Mary config 2 % git config user.name coder2
(base) mary@iMac-Mary config 2 % git config user.email coder2@mail.ru
(base) mary@iMac-Mary config 2 % touch readme.md
(base) mary@iMac-Mary config 2 % nano readme.md
(base) mary@iMac-Mary config 2 % git add readme.md
(base) mary@iMac-Mary config 2 % git commit -m "readme.md"
[main 02c3040] readme.md
 1 file changed, 3 insertions(+)
 create mode 100644 readme.md
(base) mary@iMac-Mary config 2 % git push ../server main
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 8 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 288 bytes | 288.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
To ../server
   9851e46..02c3040  main -> main
(base) mary@iMac-Mary config 2 % cd ../config
(base) mary@iMac-Mary config % git pull server main
]remote: Enumerating objects: 4, done.
remote: Counting objects: 100% (4/4), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), 268 bytes | 268.00 KiB/s, done.
From ../server
 * branch            main       -> FETCH_HEAD
   9851e46..02c3040  main       -> server/main
Updating 9851e46..02c3040
Fast-forward
 readme.md | 3 +++
 1 file changed, 3 insertions(+)
 create mode 100644 readme.md
(base) mary@iMac-Mary config % nano readme.md
(base) mary@iMac-Mary config % git add readme.md
(base) mary@iMac-Mary config % git commit -m "readme.md"
[main 1dba8eb] readme.md
 1 file changed, 1 insertion(+), 1 deletion(-)
(base) mary@iMac-Mary config % git push ../server main
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 8 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 292 bytes | 292.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
To ../server
   02c3040..1dba8eb  main -> main
(base) mary@iMac-Mary config % git log
commit 1dba8ebf385cfa9cbe58e9b8b72e62340cb4afb2 (HEAD -> main)
Author: coder1 <coder1@mail.ru>
Date:   Sun Oct 6 20:06:32 2024 +0300

    readme.md

commit 02c3040547a4945066d7cc9326936358a6bb8d67 (server/main)
Author: coder2 <coder2@mail.ru>
Date:   Sun Oct 6 20:03:32 2024 +0300

    readme.md

commit 9851e466c8dd5e8e023e5910502adb151a559803
Author: coder1 <coder1@mail.ru>
Date:   Sun Oct 6 19:40:21 2024 +0300

    file1.py
```

## Задача 4

Написать программу на Питоне (или другом ЯП), которая выводит список содержимого всех объектов репозитория. Воспользоваться командой "git cat-file -p". Идеальное решение – не использовать иных сторонних команд и библиотек для работы с git.

## Решение

```
import os
import subprocess

def get_git_objects():
    try:
        result = subprocess.run(
            ['git', 'rev-list', '--all'],
            stdout=subprocess.PIPE,
            stderr=subprocess.PIPE,
            text=True,
            check=True
        )
        objects = result.stdout.splitlines()

        for obj in objects:
            print(f"Git Commit: {obj}")
            try:
                content = subprocess.run(
                    ['git', 'cat-file', '-p', obj],
                    stdout=subprocess.PIPE,
                    stderr=subprocess.PIPE,
                    text=True,
                    check=True
                )
                print(content.stdout)
            except subprocess.CalledProcessError as e:
                print(f"Error {obj}: {e.stderr}")

    except subprocess.CalledProcessError as e:
        print(f"Error: {e.stderr}")

if __name__ == "__main__":
    if not os.path.exists('.git'):
        print("Git not found")
    else:
        get_git_objects()
```
