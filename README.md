# Загрузчик исходного кода функций в Яндекс облако

Редактируй код в любимом IDE, и в одно нажатие загрузи  функцию с локальной машины в облако. 

    ./update  # вот так в одну команду код полетел в облако

Долгое время у меня возникали сложности с загрузкой обновленного кода в облако. Вот, например, я написал новую версию функции: теперь её надо заархивировать, зайти в консоль, загрузить. Или ввести через cli кучу параметров. Если обновления или частые или редкие, это всегда головная боль.


Например, если я целый год не обновлял одну функцию, но знаю где лежит её код дома, то мне надо вспомнить в какой организации в каком облаке лежит эта функция, потом вспомнить параменты авторизации, потом ввести имя функции и каталов в котором она лежит. 

У меня очень много функций и хотелось создать какой-то унифицированный скрипт для загрузки исходного кода в облако, будь это функция написанная на go, python или javascript.

Как раз для таких нужд используется этот модуль. Достаточно раз сконфигурировать, и потом постоянно пользоваться.

Автоматически добавляет авторизационные данные в `.gitignore`

## Перед использованием

Модуль `PowerShell-Yaml`

    Install-Module Powershell-Yaml

Командная строка Яндекс.Облака `yc`

    iex (New-Object System.Net.WebClient).DownloadString('https://storage.yandexcloud.net/yandexcloud-yc/install.ps1')
    yc init

При запуске скрипт проверит зависимости и позволит установить нужные

## Использование

При первом запуске нужно инициализировать конфигурацию:

    ./update -Init

После чего создадутся файлы `.ycloud_conf` и `.ycloud_ignore`. В них нужно вбить нужные данные

После чего функцию легко загрузить командой

    ./update

# Что дальше
Будет создан специальный модуль для PowerShell c установкой из репозитория

# TODO

+ [ ] add .* by default to the .ycloud_conf
+ [ ] .ycloud-conf looks better
+ [ ] Init by language
+ [x] -Debug, printing excluded files and stuff
+ [ ] How verbosity works in Powershell, like Write-Debug and other verbosity params
+ [ ] use of service accounts
+ [ ] check for updates of script