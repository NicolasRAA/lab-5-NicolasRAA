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

