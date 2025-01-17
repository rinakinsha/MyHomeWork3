# Инструкция по работе с Git

## Что такое Git?

**Git** — это набор консольных утилит, которые отслеживают и фиксируют *изменения* в файлах. Программа была создана **Линусом Торвальдсом** при разработке ядра Linux.

![Линус Торвальдс стесняется](Linus.jpg)

С помощью Git можно сравнивать, анализировать, редактировать, сливать изменения и возвращаться назад к последнему сохранению. Этот процесс называется **контролем версий**.

## Установка Git

Установка Git в зависимости от ОС:

* **Linux** — нужно просто открыть терминал и установить приложение при помощи пакетного менеджера вашего дистрибутива. Для Ubuntu команда будет выглядеть следующим образом:

   **sudo apt-get install git**

* **Windows** — рекомендуется установить __*git for windows*__, так как он содержит и клиент с графическим интерфейсом, и эмулятор bash.

* **OS X** — проще всего воспользоваться __*homebrew*__. После его установки запустите в терминале:

    **brew install git**.

## Настройка Git

Первым делом необходимо "представиться" программе, т.е. указать наше имя и адрес электронной почты. Для этого необходимо открыть терминал и запустить следующие команды:

**git config --global user.name "Имя на английском"**

**git config --global user.email "Адрес электронной почты"**

Теперь каждое наше действие будет отмечено именем и почтой. Таким образом, пользователи всегда будут в курсе, кто отвечает за какие изменения — это вносит порядок.

## Создание нового репозитория (git init)

Git хранит свои файлы и историю **прямо в папке проекта**. Чтобы создать новый репозиторий, нам нужно открыть терминал, зайти в папку нашего проекта и выполнить команду **git init**. Это включит приложение в этой конкретной папке и создаст **скрытую директорию .git**, где будет **храниться** история репозитория и настройки.

## Определение состояния (git status)

 **Git status** — это еще одна важнейшая команда, которая показывает **информацию о текущем состоянии** репозитория: актуальна ли информация на нём, нет ли чего-то нового, что поменялось, и так далее. Запуск git status на нашем свежесозданном репозитории должен выдать:

 ![Никто ничего никому не должен](gitinit.jpg)

 Сообщение говорит о том, что файл **неотслеживаемый**. Это значит, что файл новый и система еще не знает, нужно ли следить за изменениями в файле или его можно просто игнорировать. Для того, чтобы начать отслеживать новый файл, нужно его **специальным образом объявить**.

## Подготовка файлов (git add)

В git есть концепция области подготовленных файлов. Можно представить ее как холст, на который наносят изменения, которые нужны в коммите. Сперва он пустой, но затем мы добавляем на него файлы (или части файлов, или даже одиночные строчки) командой **add**:

**git add название_созданного_файла.md**.

_На заметку: После ввода команды "git add" необязательно полностью вводить имя файла, достаточно набрать пару первых символов и нажать клавишу **Tab**_.

Теперь файл готов к коммиту.

## Фиксация изменений (git commit -m)

Теперь создадим непосредственно сам коммит с помощью следующей команды:

**git commit -m "Add some code"**

Флажок -m задаст commit message - комментарий разработчика. Он необходим для описания закоммиченных изменений. И здесь работает золотое правило всех комментариев в коде: «Максимально ясно, просто и содержательно обозначь написанное!» (это задание я, похоже, провалила :(  )

## Как посмотреть коммиты (git log)

Для просмотра все выполненных фиксаций можно воспользоваться историей коммитов. Она содержит сведения о каждом проведенном коммите проекта. Запросить ее можно при помощи команды **git log**. В ней содержиться вся информация о каждом отдельном коммите, с указанием его хэша (пугающе длинный номер сохранения), автора, списка изменений и даты, когда они были сделаны.

## Переключение между версиями (git checkout)

После ввода команды git log мы, как уже указывалось ранее, можем увидеть номера наших версий сохранений файла, хэши. Если мы хотим переключится между этими версиями, необходимо ввести следующую команду:

**git checkout первые_четыре_символа_хэша_нужной_версии**

Все те данные, которые мы ввели позднее той версии, на которую мы переключись, не будут видны, пока мы не переключимся на актуальную версию с помощтю команды **git checkout master** (master - название оснавной ветки, на которой мы работаем).

## Разница между текущим файлом и сохраненным (git diff)

![Скрин из лекции](gitdiff.jpg)

## Синтаксис языка Markdown

1. Выделение полужирным - **2 знака * по обе стороны слова или предложения**;
2. Курсивный текст - *1 знак * по обе стороны слова или предложения*;
3. Зачеркнутый текст - ~~ 2 знака ~ по обе стороны слова или предложения~~;
4. Заголовок - # в начале строки;
5. Подзаголовок - ## в начале строки;
6. Нумерованные Списки - обозначаются
обычными цифрами 1, 2, 3;
7.  Ненумерованные списки - обозначаются
*знаками в начале строки;
8. Вложенные списки - выполняем отступы.

## Работа с черновиками (git branch)

Если у нас несколько версий черновика, мы
можем вывести на экран ветку, где находимся,
командой **git branch**.

![А все уже, раньше нужно было](branch.jpg)

С помощью команды git branch также можно создавать новые ветки. Для этого в терминал необходимо ввести следующее:

**git branch branch_name**

*Примечание: название ветки может состоять только из одного слова*.

**ВНИМАНИЕ!** Создание дополнительных веток осуществляется с **основной** ветки.

Для переключения между ветками в терминал необходимо ввести команду **git checkout branch_name**.

## Совмещение 2 вариантов текста, или слияние веток (git merge)

Когда мы поработали в одной из веток и в полном восторге от ее содержимого, мы можем слить 2 ветки в одну командой **git merge branch_name**.

**ВНИМАНИЕ!** Команду на слияние веток давать **ТОЛЬКО** с основной ветки!

## Удаление веток (git branch -d name)

После слияния 2 веток та ветка, котрую мы слили с основной, по сути, больше не нужна. Ее можно удалить с помощью команды **git branch -d branch_name**.

## Добавление изображения

Обычно в git работают преимущественно с текстом, но возможность добавления изображения все же есть. Итак, для этого в месте, где мы хотим вставить картинку, необходимо прописать конструкцию, которая будет состоять из !, [] и (). В [] мы прописываем текст, который будет выводиться на экран в случае, если по неизвестным причинам картинка не отобразится. В () мы вставляем название нужного изображения с указанием его формата. Должно получиться следующее:

![2077](cyberpunk.jpg)

Чтобы git спокойно пропускал подобные фокусы, нужно создать специальный файл под названием .gitignore, только так и никак иначе, в противном случае магия не получится! Далее в данный файл необходимо прописать название нашего изображения (не забыв про формат), и закоммитить.

## Конфликт изменений

При работе в двух ветках одновременно может
возникнуть ситуация, когда в одной и другой
ветке мы по-разному изменили блок текста.
Если затем мы попробуем слить эти ветки, Git
сообщит о конфликте и предложит выбрать,
какие же изменения записать. 

Возможны 3 варианта решения конфликта:

1. accept current change - принятие текущего решения;
2. accept incoming change - принятие входящего решения;
3. accept both changes - принять оба варианта.

## Визуализация всех веток (git log --graph)

Для визуализации всех веток используется команда **git log -- graph**.

После ввода команды в терминале мы будем видеть историю сделанных коммитов в виде древа. Каждый коммит будет отображаться на ветке, на которой он был сделан.

## Работа с удаленными репозиториями. Скачивание из текущего репозитория и слияние со своей версией (git clone, git pull, git push)

Копировать внешний репозиторий на свой ПК можно командой **git clone**. 

Эта команда не только загружает все изменения, но и пытается слить все ветки на локальном компьютере и в удаленном репозитории.

Команда **git pull** позволяет скачать все из текущего репозитория и автоматически сделать *merge* с нашей версией.

Команда **git push** позволяет отправить свою версию репозитория во внешний репозиторий. 

**ВНИМАНИЕ!** При первом её использовании нужна **АВТОРИЗАЦИЯ**.

## Как настроить совместную работу?

1. Создать аккаунт на GitHub.com;
2. Создать локальный репозиторий;
3. “Подружить” ваш локальный и удалённый репозитории. *GitHub при создании нового репозитория подскажет, как это можно сделать*;
4. Отправить (push) ваш локальный репозиторий в удалённый (на GitHub), при этом, возможно, вам нужно будет авторизоваться на удалённом репозитории;
5. Провести изменения “с другого компьютера”;
6. Выкачать (pull) актуальное состояние из удалённого репозитория.

## Предложение изменений в репозиторий (pull request)

* Делаем **fork** (ответвление) репозитория;
* Делаем **git clone СВОЕЙ** версии репозитория;
* Создаем **новую ветку и в НЕЕ** вносим свои изменения
* Фиксируем изменения (делаем коммиты);
* Отправляем свою версию в свой GitHub;
* На сайте GitHub нажимаем кнопку **pull request**.



















