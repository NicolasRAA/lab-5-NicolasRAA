# Лабораторная работа № 5: Git advanced workshop

## Оглавление
1. [Цели работы](#цели-работы)
2. [Ведение](#ведение)
3. [Работа с ветками](#работа-с-ветками)
4. [Работа с удаленным репозиторием](#работа-с-удаленным-репозиторием)
5. [Моделирование конфликта](#моделирование-конфликта)
6. [Разрешение конфликта](#разрешение-конфликта)
7. [Автоматизация проверки формата файлов при коммите](#автоматизация-проверки-формата-файлов-при-коммите)
8. [Использование Git Flow в проекте](#использование-git-flow-в-проекте)
9. [Создание репозитория для лабораторной работы № 5](#создание-репозитория-для-лабораторной-работы-5)
10. [Заключение](#заключение)  

---

## Цели работы  

Цель данной лабораторной работы заключается в освоении продвинутых возможностей системы контроля версий `Git`, а также в практическом применении полученных знаний для управления проектами. В ходе выполнения работы я научился:
  1. Создавать и управлять репозиториями на GitHub.
  2. Клонировать репозитории и работать с локальными копиями.
  3. Создавать и управлять ветками, а также сливать изменения между ними.
  4. Разрешать конфликты, возникающие при слиянии веток.
  5. Автоматизировать проверку формата файлов с помощью `Git Hooks`.
  6. Интегрировать `Git Flow` в процесс разработки для управления функциональностью, релизами и исправлениями ошибок.

---

## Ведение

### 1. Создание и клонирование репозитория
  - Репозиторий был создан из терминала Ubuntu с использованием команды:
    ```
    gh repo create git-practice --public
    ```
    ![gh repo create git-practice](https://github.com/user-attachments/assets/9edc8277-2c5e-411b-904a-75d087fe7806)
  - Клонировал репозиторий на локальную машину с помощью команды `git clone`:
    ![git clone git-practice](https://github.com/user-attachments/assets/62b2ec60-1097-4c7f-9f13-b0da8b015d11)  
  - Зашёл в директорию репозитория:
    ```
    cd git-practice
    ```
   - После клонирования я проверил, что репозиторий успешно создан и доступен на GitHub.
    ![git-practice en github](https://github.com/user-attachments/assets/4ba3fe5d-db1b-42fe-a4b6-98c114c30dfb)  

### 2. Добавление файла и работа с веткой main
  - Я создал новый текстовый файл `example.txt` с помощью редактора `nano`:
    ![nano example txt](https://github.com/user-attachments/assets/dc3c4c0b-ee39-4fe3-84a9-921bdb3fd564)  
  - Внутри файла я добавил текст структуры книги (главы, параграфы и т.д.):
    ![text inside example txt](https://github.com/user-attachments/assets/f4d73647-ddaa-48fa-ba7f-adc7c4862354)  
  - Для загрузкм изменений в репозиторий я исползовал команды:
    ![git add commit and push](https://github.com/user-attachments/assets/8469f0e0-f803-41e7-8ac4-b93f2648dcf3)  
    - Добавил файл в индекс:
      ```
      git add example.txt
      ```
    - Зафиксировал изменения:
      ```
      git commit -m ""
      ```
    - Отправил изменения в удалённый репозиторий:
      ```
      git push origin main
      ```
    ![example txt in github](https://github.com/user-attachments/assets/63b704ec-c813-40f5-9b93-277288293f1a)  
    - Убедился, что файл `example.txt` и его содержимое успешно загружены в ветку main на GitHub.

### 3. Работа с новой веткой
  - Я создал новую ветку с помощью команды `git checkout -b feature-branch`:
    ![git cheackout -b feature-branch (use 1 comando en vez de 2, agregar al informe eso)](https://github.com/user-attachments/assets/af3a02a2-b35e-4d81-9495-d3a56e1d2409)
> [!TIP]
> Я решил использовать команду `git checkout -b`, которая позволяет создать и сразу переключиться на новую ветку в одном шаге, вместо использования двух отдельных команд (`git branch` и `git checkout`) как указано в инструкции. Это упрощает процесс и экономит время.
  - В новой ветке я открыл файл `example.txt` с помощью `nano` и добавил новый текст:
    ![new text on example txt](https://github.com/user-attachments/assets/f05cf41a-d0ba-4c7f-8494-aa8b94d7cf32)  
  - Затем я выполнил команды для загрузки изменений в новую ветку:
    ![git add commit and push feature branch](https://github.com/user-attachments/assets/ceea1a26-f30b-4b55-83ef-b964d9c091f2)  
  - Я проверил на GitHub, что в ветке `feature-branch` файл `example.txt` содержит изменения, которые я сделал.
    ![example txt in github on feature branch](https://github.com/user-attachments/assets/ddcd3d42-bece-42ec-8533-fd681de62d99)  

### 4. Слияние изменений
  - Я вернулся на основную ветку с помощью команды `git checkout main`:
    ![git checkout main](https://github.com/user-attachments/assets/7d913f82-2793-4902-a6d4-754e537811d1)  
  - Я выполнил команду для слияния изменений из ветки `feature-branch` в основную ветку `main` и отправил объединённые изменения в удалённый репозиторий:
    ![git merge y git push](https://github.com/user-attachments/assets/fdcc0b34-5289-4d4b-9f9f-af10ff1a1a42)
> [!NOTE]
> Команда силияния `git merge` используется для объединения изменений из одной ветки в другую. Это позволяет работать параллельно с несколькими версиями проекта, а затем интегрировать изменения. Наличие веток помогает изолировать новые функции или исправления, чтобы основная ветка оставалась стабильной.  
  - Убедился, что изменения из ветки `feature-branch` успешно интегрированы в ветку `main`. Теперь файл `example.txt` в основной ветке содержит все изменения.
    ![example txt from feature branch merged on main](https://github.com/user-attachments/assets/6db724f7-016e-4ffa-bd03-400146674d25)  

---

## Работа с ветками

### 1. Создание нового файла
  - Создал новый текстовый файл `book.txt` с помощью редактора `nano`:
    ![nano book txt](https://github.com/user-attachments/assets/2447a79d-67f6-42bd-adf3-a09fdf397048)  
  - Внутри файла добавил базовую структуру книги:
    ![text inside book txt](https://github.com/user-attachments/assets/bd701d4d-0fcd-4dfb-9c29-a86589fadac6)

### 2. Создание новой ветки и добавление изменений
  - Создал и одновременно переключился на новую ветку `feature-login` с помощью команды:
    ![git checkout -b feature-login](https://github.com/user-attachments/assets/8c6e43b3-ed71-4f96-89b6-30d06f8545ec)
  - В новой ветке открыл файл `book.txt` и добавил новый раздел "Глава 3: Вход в систему":
    ![new text on book txt](https://github.com/user-attachments/assets/7220d8d1-6933-4a7b-bb34-4fc675a2d10b)

### 3. Загрузка изменений в ветку `feature-login`
  - Сохранил изменения и загрузил их в ветку `feature-login` на GitHub с помощью следующих команд:
    ![git add commit and push feature login](https://github.com/user-attachments/assets/93775b0b-6cb8-47a9-bc1c-9c451e0c517b)
  - Перешёл на GitHub и убедился, что файл `book.txt` с добавленной третьей главой находится в ветке `feature-login`:
    ![book txt in github on feature login branch](https://github.com/user-attachments/assets/0fb1555f-3ee7-47b6-b98c-f7a9486aeccf)

---

## Работа с удаленным репозиторием

### 1. Внесение изменений в основной ветке
  - Переключился на ветку `main` с помощью команды:
    ![git checkout main after feature login](https://github.com/user-attachments/assets/fc8c3da3-2132-42e2-9c4c-bc4f9fe7558c)  
  - Открыл файл `book.txt` в редакторе `nano` и добавил описание книги и текст для первых двух глав:
    ![nano book en main](https://github.com/user-attachments/assets/bc3b6ae6-5009-4f4b-af06-396a9fd6fc68)  
    ![text in book txt on main](https://github.com/user-attachments/assets/75b3dba3-6f53-4ff9-9d04-8059b3e83646)  
  - Сохранил изменения и загрузил их в удалённый репозиторий с помощью следующих команд:  
    ![git add commit and push book on main](https://github.com/user-attachments/assets/40ea316d-1f81-40b8-b653-3f99d1a9db99)  

---

## Моделирование конфликта

### 1. Внесение изменений в ветке `feature-login`
  - Переключился на ветку `feature-login` с помощью команды:  
    ![git checkout feature login](https://github.com/user-attachments/assets/4aa66bd0-6ac2-4155-81ac-cc33854673b4)  
  - Открыл файл `book.txt` и изменил текст для второй главы:  
    ![new text on book txt again on feature login](https://github.com/user-attachments/assets/6a0e3f97-276a-4408-9ce7-d0d916351e07)  
  - Сохранил изменения и загрузил их в ветку `feature-login` на GitHub:
    ![git add commit and push book again on feature login](https://github.com/user-attachments/assets/ce484af0-982e-4387-8bbf-c6a24f7b8622)  

---

## Разрешение конфликта

### 1. Попытка слияния изменений
  - Переключился на основную ветку `main` с помощью команды:
    ```
    git checkout main
    ```
  - Выполнил команду для получения последних изменений из удалённого репозитория `git pull origin main`:
    ![git checkout main pull and push with conflict](https://github.com/user-attachments/assets/2246ecad-32df-4f3d-90e4-9763971abc42)  
> [!NOTE]
> Команда `git pull` позволяет загрузить и интегрировать изменения из удалённого репозитория в текущую ветку. Она объединяет команды `git fetch` и `git merge` в одном шаге.
  - Попробовал слить изменения из ветки `feature-login` с помощью команды:  
    ```
    git merge feature-login
    ```
  - И как показано на фото, я получил сообщение о конфликте:
    ```
    Auto-merging book.txt
    CONFLICT (add/add): Merge conflict in book.txt
    Automatic merge failed; fix conflicts and then commit the result.
    ```
> [!NOTE]
> Конфликты возникают, когда изменения в разных ветках затрагивают один и тот же участок кода. Git не может автоматически объединить такие изменения, и требуется ручное разрешение конфликта. :skull_and_crossbones:

---

## Разрешение конфликта

### 1. Разрешение конфликта вручную  
  - Открыл файл `book.txt` и увидел следующее содержимое:
    ![text in book txt with conflict](https://github.com/user-attachments/assets/453df020-130d-41e5-8aa0-bc47ee864082)  
  - Удалил конфликтующие метки (`<<<<<<<`, `=======`, `>>>>>>>`) и оставил текст из ветки `feature-login`:
    ![book txt with the conflic solved](https://github.com/user-attachments/assets/e928253c-78ea-4076-971a-783080d87558)  
  - Сохранил файл и зафиксировал разрешение конфликта:
    ![git add commit and push book resolved conflict](https://github.com/user-attachments/assets/b7b8c5c9-7c3e-44bd-bd27-6b0be6e132f2)
      - При использовании команды `git commit`, как показано на картинке, я получил сообщение "Resolved conflict in chapter 2", что свидетельствует об успешном разрешении конфликта.

---

## Автоматизация проверки формата файлов при коммите

> Перед каждым коммитом необходимо автоматически проверять, чтобы все .txt файлы в репозитории соответствовали определенному формату.

### 1. Создание файла и кода
  - Я создал файл с помощью команды:
    ![nano check format sh](https://github.com/user-attachments/assets/654c879b-5ebe-4ee8-9602-6c75b5f9e559)  
> [!NOTE]  
> Файлы с расширением `.sh` — это скрипты, которые могут быть выполнены в оболочке Unix. Они позволяют автоматизировать задачи и упрощают выполнение последовательностей команд. Файлы `.sh` и `.bash` в основном взаимозаменяемы, но `.sh` чаще используется для обозначения скриптов, которые могут быть выполнены в любой оболочке, тогда как `.bash` указывает на использование Bash-оболочки. :nerd_face:  

  - Внутри файла я добавил следующий код:
    ![codigo nano check format sh](https://github.com/user-attachments/assets/35dab293-2cc0-4c39-8c66-10924f1cad3e)  

    - **Объяснение кода:**
      - `#!/bin/bash` — указывает, что скрипт должен выполняться с помощью Bash.
      - `echo "Проверка формата .txt файлов..."` — выводит сообщение о начале проверки.
      - `files=$(git diff --cached --name-only --diff-filter=ACM | grep '\.txt$')` — получает список всех измененных файлов с расширением `.txt`, которые находятся в индексе (готовы к коммиту).
      - `for file in $files; do` — начинает цикл по всем найденным файлам.
      - `if grep '.\{81\}' "$file"; then` — проверяет, есть ли в файле строки длиннее 80 символов.
      - `echo "Ошибка: Файл '$file' содержит строки длиннее 80 символов."` — выводит сообщение об ошибке, если такая строка найдена.
      - `exit 1` — завершает выполнение скрипта с кодом ошибки.
      - `echo "Все .txt файлы прошли проверку формата."` — выводит сообщение об успешной проверке.
      - `exit 0` — завершает выполнение скрипта без ошибок.

### 2. Настройка прав и добавление скрипта в Git Hooks
  - Я использовал команды:
    ![chmod cp chmod commands](https://github.com/user-attachments/assets/5fb8226a-851c-4200-a092-387ebde0b2bd)  
  - Первая команда:
    ```
    chmod +x check_format.sh
    ```
    > Эта команда делает файл исполняемым, что позволяет запускать его как программу.
  - И потом использованы команды:
    ```
    cp check_format.sh .git/hooks/pre-commit
    chmod +x .git/hooks/pre-commit
    ```
    > Первая команда копирует скрипт в папку `.git/hooks` и переименовывает его в `pre-commit`, что позволяет Git автоматически запускать его перед каждым коммитом. Вторая команда делает этот скрипт исполняемым.
    
### 3. Создание и тестирование файла
  - Я создал текстовый файл:
    ![nano test txt](https://github.com/user-attachments/assets/8c76d716-1c40-4c77-a45a-9d4d4813c545)  
    - Внутри файла я добавил следующее:
      ![text in test txt](https://github.com/user-attachments/assets/6385f181-7e01-400c-9990-43a2e07a30ee)  
  - Затем использовал команду:
    ```
    git add .
    ```
> [!IMPORTANT]
> Точка (`.`) указывает на добавление всех изменений в текущей директории и поддиректориях в индекс Git.
  - После этого, использовал команду:
    ```
    git commit
    ```
    - При этом появились следующие сообщения, показаные на картинке:
    ![git add and commit with error because of the format](https://github.com/user-attachments/assets/8dbbc77b-c85f-41cb-9e22-4d802715c283)

### 4. Исправление файла
  - Я снова открыл файл `test.txt` и изменил его содержимое на:
    ![changes on test txt](https://github.com/user-attachments/assets/74a6407f-6786-44d5-8a80-300913b1f418)  
  - Я снова использовал команды:
    ```
    git add .
    git commit -m "Исправлены ошибки формата"
    ```
    - Теперь при выполнении коммита я увидел следующие сообщения:
      ![git add commit and push with valid test](https://github.com/user-attachments/assets/aa4e3ddd-4221-4822-a1aa-e0be36793d94)  
        - Поскольку файл теперь соответствует всем требованиям, он без проблем прошел проверку.

---

## Использование Git Flow в проекте

> Задача: интегрировать Git Flow в проект для управления циклом разработки, создания релизов и управления hotfixes.

### 1. Установка и инициализация Git Flow
  - Я установил Git Flow с помощью команды:
    ![sudo install git-flow](https://github.com/user-attachments/assets/9d506ebb-8ddd-4799-a87a-bd515ab2ff5a)  
  - Затем я создал и переключился на ветку `develop` с помощью команды:
    ![create branch develop](https://github.com/user-attachments/assets/16af8eb6-f812-4773-8096-de88c845c895)  
  - Я использовал команду:
    ![git push -u develop](https://github.com/user-attachments/assets/f553399d-3ebd-4d07-b682-336ab30d33fa)  
> [!NOTE]
> Эта команда создает новую ветку `develop` на удаленном репозитории и устанавливает ее как отслеживаемую, что позволяет в дальнейшем использовать просто `git push` и `git pull` без указания удаленного репозитория и ветки.
  - Я инициализировал Git Flow с помощью команды:
    ![git flow init](https://github.com/user-attachments/assets/cbde7b96-d43c-41db-88b4-fac92b894c58)  
    > Эта команда настраивает Git Flow для текущего репозитория, создавая необходимые ветки и конфигурации. В процессе инициализации я оставил значения по умолчанию, нажав Enter.

### 2. Создание новой функциональности
  - Я создал ветку для новой функциональности с помощью команды:
    ![git flow feature start task-management](https://github.com/user-attachments/assets/2ff3c73d-f52d-444a-9f4a-4e850f4a0e9d)  
  - Я создал файл `task_manager.py`:
    ![nano task_manager py](https://github.com/user-attachments/assets/af98280f-8113-4d82-a4bd-5a92da41275c)
      - В нем добавил следующий код:
        ![code on task_manager py](https://github.com/user-attachments/assets/63bfc926-00a5-4370-ad56-5025694ff13e)  
  - Я использовал команды для добавления и коммита изменений:
    ![git add and commit task_manager py](https://github.com/user-attachments/assets/c9867d55-f210-4afa-8677-34d0f297bae0)  
    
### 3. Завершение функциональности
  - После завершения разработки функции я использовал команду:
    ![git flow feature finish task-management](https://github.com/user-attachments/assets/2c9d64c2-0031-489b-8b13-9fc6010c2a73)  
    > Эта команда завершает работу над веткой функциональности, сливает изменения в ветку `develop` и удаляет ветку функциональности.

### 4. Создание релиза
  - Я начал создание релиза на ветке `develop` с помощью команды:
    ![git flow release start v100](https://github.com/user-attachments/assets/7ccfbdeb-184a-4eae-b4ea-0fbc26a0e8b2)  
    > Эта команда создает новую ветку релиза, основанную на ветке `develop`, и позволяет вносить изменения, связанные с релизом.
  - Я создал файл `version.txt` и добавил в него следующее:
    ![nano version txt](https://github.com/user-attachments/assets/5fe3fcc6-97a5-4dc0-87a2-281da099864c)
    ![texto en version txt](https://github.com/user-attachments/assets/ee97c6f0-ad32-48a9-b55e-c76ec40ddd54)  
  - Затем, когда я хотел завершить релиз и слить его с ветками «develop» и «main», я получил сообщение о том, что мне следует добавить в коммит сообщение, объясняющее, почему слияние необходимо:
    ![final final text on release v100](https://github.com/user-attachments/assets/681af616-c1c6-4628-8655-3e17cd187861)  

### 5. Завершение релиза
  - Я завершил релиз с помощью команды:
    ![git flow release finish v100](https://github.com/user-attachments/assets/dbff8795-c588-4b86-b005-7fb14656cd38)
> [!IMPORTANT]
> Эта команда сливает ветку релиза в ветки `main` и `develop`, создает тег для релиза и удаляет ветку релиза. В процессе завершения мне было предложено ввести сообщение для коммита как показал раньше.

### 6. Создание hotfix
  > Когда я закончил разработку, критической ошибки не было, но я все равно решил создать hotfix, чтобы получить больше практического опыта :monocle_face:.

  - Я создал hotfix с помощью команды:
    ![git flow hotfix start hotfix 101](https://github.com/user-attachments/assets/731d0a85-4b36-450a-8e88-2055023d95f8)  
  - Я созадал файл `file_with_error.py` и использовал команды:
    ![nano file with error git add commit](https://github.com/user-attachments/assets/6b81a368-c2dc-4144-a833-dcd6965fee02)  
  - Я завершил hotfix с помощью команды:
    ![git flow hotfix finish hotfix 101](https://github.com/user-attachments/assets/d499e40b-47c1-40a6-8241-ba3bb14d5f9b)  

### 7. Отправка изменений на удаленный репозиторий
  - Я отправил изменения на удаленный репозиторий с помощью команд:
    ![git push origin develop and main](https://github.com/user-attachments/assets/21968608-3d9b-45f0-827f-a45a52d2e41b)  
  - Я зашел в GitHub и убедился, что все файлы в ветке `main` обновлены.
    ![github con todos los archivos](https://github.com/user-attachments/assets/9b03d071-1f04-4b75-9fa4-b75736e7fbd3)  


---

## Создание репозитория для лабораторной работы 5

  - Я вернулся на уровень выше в директории с помощью команды `cd ..`
  - Я создал новый публичный репозиторий с помощью команды `gh repo create lab-5-NicolasRAA --public`.
  - Затем я клонировал новый репозиторий на свою локальную машину с помощью команды `git clone git@github.com:NicolasRAA/lab-5-NicolasRAA.git`.
  - Я переместился в директорию нового репозитория командой `cd lab-5-NicolasRAA`.
    ![creando lab-5-NicolasRAA](https://github.com/user-attachments/assets/646ca66a-d4d4-442e-9cb2-6ff589a3c22f)  
  - Я добавил подмодуль с помощью команды:
    ```
    git submodule add git@github.com:NicolasRAA/git-practice.git
    ```
> [!IMPORTANT]
> Эта команда добавляет другой репозиторий (в данном случае `git-practice`) как подмодуль в текущий репозиторий. Подмодули позволяют включать и управлять зависимостями между репозиториями, что удобно для организации проектов, состоящих из нескольких компонентов.

  ![adding git-practice to lab-5 as a submodule](https://github.com/user-attachments/assets/222c5619-9403-4d26-a37c-2480f8288106)
    - Я использовал команды для добавления и коммита изменений:
      ```
      git commit -m 
      git push origin main
      ```
  - Потом, ещё в терминале, я создал файл `README.md` для лабораторной работы:
    ![creating and adding readme](https://github.com/user-attachments/assets/efbb9e3a-f9cd-4b15-a6ad-99e79e784e98)  
    - Загрузил его в удалённый репозиторий с помощью команд:
      ```
      git add README.md
      git commit -m ""
      git push origin main
      ```
    - Я зашел в свой репозиторий на GitHub `lab-5-NicolasRAA` и убедился, что подмодуль `git-practice` отображается корректно, а также что файл `.gitmodules` присутствует в корне репозитория :sparkles:.
      ![lab 5 on github with the submodule git-practice](https://github.com/user-attachments/assets/b3986ae6-cfc6-402b-b400-ffbd3f6628be)  
> [!NOTE]
> Файл `.gitmodules` содержит информацию о подмодулях, включая их URL и путь в основном репозитории. Это позволяет Git управлять подмодулями и их конфигурацией.
      - Я также проверил, что файл `README.md` был успешно загружен и отображается на странице репозитория.

---

## Заключение

В ходе выполнения лабораторной работы № 5 я освоил продвинутые возможности системы контроля версий Git.

Работа с ветками и слиянием изменений помогла мне понять, как изолировать новые функции и исправления, что способствует поддержанию стабильности основной ветки проекта. Я также изучил, как разрешать конфликты, возникающие при слиянии, что является важным навыком в командной разработке.  

Автоматизация проверки формата файлов с помощью `Git Hooks` продемонстрировала, как можно улучшить качество кода и избежать ошибок на этапе коммита. Интеграция `Git Flow` в процесс разработки позволила мне организовать работу над функциональностью, релизами и исправлениями ошибок более структурированным образом.  

Кроме того, в качестве бонуса я научился как создовать подмодулы в репозиториях и это дало мне возможность управлять зависимостями между проектами, что является важным аспектом в разработке сложных приложений.  

В целом, данная лабораторная работа значительно углубила мои знания и навыки работы с Git, что, безусловно, будет полезно в будущих проектах :trophy::computer:!
