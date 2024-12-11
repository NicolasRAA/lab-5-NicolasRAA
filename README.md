# Лабораторная работа № 5: Git advanced workshop

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
> Конфликты возникают, когда изменения в разных ветках затрагивают один и тот же участок кода. Git не может автоматически объединить такие изменения, и требуется ручное разрешение конфликта.

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





