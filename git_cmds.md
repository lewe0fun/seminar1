# I. Первоначальная настройка
Настройка информации о пользователе для всех локальных репозиториев

$ git config --global user.name "[имя]"

Устанавливает имя, которое будет отображаться в поле автора у выполняемых вами коммитов

$ git config --global user.email "[адрес электронной почты]"

Устанавливает адрес электронной почты, который будет отображаться в информации о выполняемых вами коммитах
# II. Основные комманды  
1. git add
Команда git add добавляет содержимое рабочей директории в индекс (staging area) для последующего коммита. По умолчанию git commit использует лишь этот индекс, так что вы можете использовать git add для сборки слепка вашего следующего коммита.

2. git status
Команда git status показывает состояния файлов в рабочей директории и индексе: какие файлы изменены, но не добавлены в индекс; какие ожидают коммита в индексе. Вдобавок к этому выводятся подсказки о том, как изменить состояние файлов.

3. git diff
Команда git diff используется для вычисления разницы между любыми двумя Git деревьями. Это может быть разница между вашей рабочей директорией и индексом (собственно git diff), разница между индексом и последним коммитом (git diff --staged), или между любыми двумя коммитами (git diff master branchB).

4. git difftool
Команда git difftool просто запускает внешнюю утилиту сравнения для показа различий в двух деревьях, на случай если вы хотите использовать что-либо отличное от встроенного просмотрщика git diff.

5. git commit
Команда git commit берёт все данные, добавленные в индекс с помощью git add, и сохраняет их слепок во внутренней базе данных, а затем сдвигает указатель текущей ветки на этот слепок.

6. git reset
Команда git reset, как можно догадаться из названия, используется в основном для отмены изменений. Она изменяет указатель HEAD и, опционально, состояние индекса. Также эта команда может изменить файлы в рабочей директории при использовании параметра --hard, что может привести к потере наработок при неправильном использовании, так что убедитесь в серьёзности своих намерений прежде чем использовать его.

7. git rm
Команда git rm используется в Git для удаления файлов из индекса и рабочей директории. Она похожа на git add с тем лишь исключением, что она удаляет, а не добавляет файлы для следующего коммита.

8. git mv
Команда git mv — это всего лишь удобный способ переместить файл, а затем выполнить git addдля нового файла и git rm для старого.

9. git clean
Команда git clean используется для удаления мусора из рабочей директории. Это могут быть результаты сборки проекта или файлы конфликтов слияний.

## II. Ветвлениe и слияниe

1. git branch
Команда git branch — это своего рода “менеджер веток”. Она умеет перечислять ваши ветки, создавать новые, удалять и переименовывать их.

2. git checkout
Команда git checkout используется для переключения веток и выгрузки их содержимого в рабочую директорию.

3. git merge
Команда git merge используется для слияния одной или нескольких веток в текущую. Затем она устанавливает указатель текущей ветки на результирующий коммит.

4. git mergetool
Команда git mergetool просто вызывает внешнюю программу слияний, в случае если у вас возникли проблемы слияния.

5. git log
Команда git log используется для просмотра истории коммитов, начиная с самого свежего и уходя к истокам проекта. По умолчанию, она показывает лишь историю текущей ветки, но может быть настроена на вывод истории других, даже нескольких сразу, веток. Также её можно использовать для просмотра различий между ветками на уровне коммитов.

6. git stash
Команда git stash используется для временного сохранения всех незакоммиченных изменений для очистки рабочей директории без необходимости коммитить незавершённую работу в новую ветку.

7. git tag
Команда git tag используется для задания постоянной метки на какой-либо момент в истории проекта. Обычно она используется для релизов.

# III. Совсместная работа

Не так уж много команд в Git требуют сетевого подключения для своей работы, практически все команды оперируют с локальной копией проекта. Когда вы готовы поделиться своими наработками, всего несколько команд помогут вам работать с удалёнными репозиториями.

1. git fetch
Команда git fetch связывается с удалённым репозиторием и забирает из него все изменения, которых у вас пока нет и сохраняет их локально.

2. git pull
Команда git pull работает как комбинация команд git fetch и git merge, т.е. Git вначале забирает изменения из указанного удалённого репозитория, а затем пытается слить их с текущей веткой.

3. git push
Команда git push используется для установления связи с удалённым репозиторием, вычисления локальных изменений отсутствующих в нём, и собственно их передачи в вышеупомянутый репозиторий. Этой команде нужно право на запись в репозиторий, поэтому она использует аутентификацию.

3. git remote
Команда git remote служит для управления списком удалённых репозиториев. Она позволяет сохранять длинные URL репозиториев в виде понятных коротких строк, например "origin", так что вам не придётся забивать голову всякой ерундой и набирать её каждый раз для связи с сервером. Вы можете использовать несколько удалённых репозиториев для работы и git remote поможет добавлять, изменять и удалять их.

4. git archive
Команда git archive используется для упаковки в архив указанных коммитов или всего репозитория.

5. git submodule
Команда git submodule используется для управления вложенными репозиториями. Например, это могут быть библиотеки или другие, используемые не только в этом проекте ресурсы. У команды submodule есть несколько под-команд — add, update, sync и др. — для управления такими репозиториями.

Осмотр и сравнение
6. git show
Команда git show отображает объект в простом и человекопонятном виде. Обычно она используется для просмотра информации о метке или коммите.

7. git shortlog
Команда git shortlog служит для подведения итогов команды git log. Она принимает практически те же параметры, что и git log, но вместо простого листинга всех коммитов, они будут сгруппированы по автору.

8. git describe
Команда git describe принимает на вход что угодно, что можно трактовать как коммит (ветку, тег) и выводит более-менее человекочитаемую строку, которая не изменится в будущем для данного коммита. Это может быть использовано как более удобная, но по-прежнему уникальная, замена SHA-1.



# III. Осмотр и сравнение
## git show
Команда git show отображает объект в простом и человекопонятном виде. Обычно она используется для просмотра информации о метке или коммите.


## git describe
Команда git describe принимает на вход что угодно, что можно трактовать как коммит (ветку, тег) и выводит более-менее человекочитаемую строку, которая не изменится в будущем для данного коммита. Это может быть использовано как более удобная, но по-прежнему уникальная, замена SHA-1.
# IV. Игнорирование некоторых файлов
Исключение временных и вторичных файлов и директорий

*.log
build/
temp-*
Git будет игнорировать файлы и директории, перечисленные в файле .gitignore с помощью wildcard синтаксиса

$ git ls-files --others --ignored --exclude-standard

Список всех игнорируемых файлов в текущем проекте

# V. Как переименовать локальные и удаленные ветки git
Если вы неправильно дали название ветки и поместили в удаленный репозиторий, выполните следующие шаги, пока никто из разработчиков не заметил, что вы не следовали соглашению по именованию.

1. Как переименовать локальную ветку

Если вы хотите переименовать ветку, на которой находитесь

git branch -m new-name

Если вы на другой ветке:

git branch -m old-name new-name

2. Удалите удаленную ветку old-name и добавьте локальную ветку new-name

git push origin :old-name new-name

3. Снова добавьте ветку для локальной ветки new-name

Переключитесь к ветке и дальше задайте:

git push origin -u new-name

Как более быстрый способ, вы можете использовать следующие шаги (команда для вашего терминала):

git branch -m old_branch new_branch         # Rename branch locally

git push origin :old_branch                 # Delete the old branch

git push --set-upstream origin new_branch   # Push the new branch, set local branch to track the new remote  
![final document](lewe.png)
# GitHub:
## Скоздать репозиторий  
### Cпособ 1: нажать на "New repository".
### Способ 2: нажать на большую кнопку "Start a project" ("Создать проект"):
### Способ 3: нажать на зеленую кнопку "New repository" ("Новый репозиторий") в окошке Repositories ("Репозитории")

1. Создаем репозиторий на github вида Имя_репозитория.git  
2. git remote add origin https://github.com/lewe0fun/Имя_репозитория.git (связываание репозитоория)
3. git branch -M main (создаем ветку main)
4. git push -u origin main (публикуем в GitHub)
5. git pull (локалный<-удаленный)
6. git push (локалный->удаленный)
