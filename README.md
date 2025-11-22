# tdl

<img align="right" src="docs/assets/img/logo.png" height="280" alt="">

> 📥 Telegram Downloader, but more than a downloader

English | <a href="README_zh.md">简体中文</a>

<p>
<img src="https://img.shields.io/github/go-mod/go-version/iyear/tdl?style=flat-square" alt="">
<img src="https://img.shields.io/github/license/iyear/tdl?style=flat-square" alt="">
<img src="https://img.shields.io/github/actions/workflow/status/iyear/tdl/master.yml?branch=master&amp;style=flat-square" alt="">
<img src="https://img.shields.io/github/v/release/iyear/tdl?color=red&amp;style=flat-square" alt="">
<img src="https://img.shields.io/github/downloads/iyear/tdl/total?style=flat-square" alt="">
</p>

#### Features:
- Single file start-up
- Low resource usage
- Take up all your bandwidth
- Faster than official clients
- Download files from (protected) chats
- Forward messages with automatic fallback and message routing
- Upload files to Telegram
- Export messages/members/subscribers to JSON

## Preview

It reaches my proxy's speed limit, and the **speed depends on whether you are a premium**

![](docs/assets/img/preview.gif)

## Documentation

Please refer to the [documentation](https://docs.iyear.me/tdl/).

## Sponsors

![](https://raw.githubusercontent.com/iyear/sponsor/master/sponsors.svg)

## Contributors
<a href="https://github.com/iyear/tdl/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=iyear/tdl&max=750&columns=20" alt="contributors"/>
</a>

Для установки набора инструментов Telegram tdl на локальный ПК можно воспользоваться несколькими способами:

**Самый простой способ для Windows:**

1. Откройте PowerShell от имени администратора.
2. Выполните команду (установится последняя версия, путь: `C:\tdl`, директория будет добавлена в переменную PATH):
   ```
   iwr -useb https://docs.iyear.me/tdl/install.ps1 | iex
   ```
3. После установки откройте новый терминал и проверьте команду:
   ```
   tdl version
   ```

**Для Linux, macOS:**

- Откройте терминал и выполните:
  ```
  curl -sSL https://docs.iyear.me/tdl/install.sh | sudo bash
  ```

**Через пакетные менеджеры (Windows, macOS, Linux):**
- Windows (через Scoop):
  ```
  scoop bucket add extras
  scoop install telegram-downloader
  ```
- macOS (через Brew):
  ```
  brew install telegram-downloader
  ```
- Linux (например, через yay):
  ```
  yay -S tdl
  ```

**Установка конкретной версии или через Docker — подробности и инструкции есть в официальной документации:**
https://docs.iyear.me/tdl/getting-started/installation/

**Инструкция по установке вручную (prebuilt binaries):**
- Скачать архив с бинарниками для вашей ОС.
- Разархивировать и переместить исполняемый файл в нужную директорию.
- Добавить эту директорию в переменную PATH.
- Проверить права на выполнение файла.

Если нужна сборка из исходников (требуется Go 1.23+):
```
go install github.com/iyear/tdl@latest
```

Для большинства пользователей хватит автоскрипта для Windows или Linux. Все ключевые способы описаны в официальной документации.[1]

Вот как пользоваться tdl (Telegram Downloader):

**1. Первый запуск и авторизация**
- После установки откройте терминал и выполните:
  ```
  tdl login
  ```
  tdl поддерживает авторизацию через QR-код, телефон и код или автоматический поиск установленного Telegram Desktop. Для входа можно использовать:
  ```
  tdl login -T qr           # через QR-код 
  tdl login -T code         # через телефон и код
  tdl login -d /path/to/TelegramDesktop    # указать путь вручную
  ```
- Если нужно работать с разными аккаунтами, используйте namespace:
  ```
  tdl -n your_namespace login
  ```
  Или предварительно экспортируйте переменную окружения:
  ```
  export TDL_NS=your_namespace
  ```

**2. Скачивание файлов**
- Скачать все медиа из чата или канала:
  ```
  tdl chat export -c CHAT
  ```
  Где `CHAT` — это username, id или публичная ссылка группы/канала. Пример для канала по ссылке:
  ```
  tdl chat export -c @yourchannel
  ```
- Скачать определённые сообщения/видео/файлы:
  ```
  tdl dl -u https://t.me/yourchannel/1234
  ```
  Можно сразу указать несколько ссылок:
  ```
  tdl dl -u https://t.me/yourchannel/1234 -u https://t.me/yourchannel/1235
  ```

**3. Экспорт сообщений**
- Экспортировать сообщения с вложениями в JSON:
  ```
  tdl chat export -c CHAT
  ```
  Для экспорта сообщений с указанием диапазона времени/ID:
  ```
  tdl chat export -c CHAT -T id -i 100,200       # ID
  tdl chat export -c CHAT -T time -i 1650000000,1650001000   # Unixtime 
  ```

**4. Загрузка файлов на Telegram**
- Отправить файл в чат:
  ```
  tdl upload -c CHAT -f /path/to/file
  ```

**5. Проверка версии и справка**
  ```
  tdl version
  tdl --help
  tdl download --help        # подробная справка по download
  ```

**6. Поддержка расширений (Extensions)**
- Установка расширения:
  ```
  tdl extension install iyear/tdl-whoami
  ```
  Запуск расширения:
  ```
  tdl whoami
  ```

**Официальная документация** — https://docs.iyear.me/tdl/
Там приведены все опции, команды, примеры работы и расширенные флаги.[1][2][3][4][5]

**Возможности tdl**:
- Быстрое скачивание файлов даже из защищённых чатов
- Forward/пересылка сообщений с fallback и маршрутизацией
- Экспорт участников/подписчиков чата/канала
- Удобная CLI-интеграция и поддержка Docker

Для быстрой работы начните с первой команды `tdl login`, а затем воспользуйтесь `tdl chat export` или `tdl dl`. Остальные команды — в официальном гиде.

## LICENSE

AGPL-3.0 License
