# Справочник по работе с Git

--- 

1. #### Создадим репозиторий. ####

#### Для этого установим git bash и откроем его. #### 
#### Для перехода в корневую директорию вводим следующую команду в консоли: ####

```bash
    cd /c
```

#### Далее указываем имя и @email: #### 

```bash
    git congig --global user.name "указать имя"
    git congig --global user.email "указать @email"
```

#### Далее следуем по такому алгоритму: ####

```bash
    git init "создать репозиторий в нужной папке"
```

#### Командой ####

```bash
    git status 
```

#### мы можем узнать текущее состояние репозитория. ####

--- 

2. #### Теперь создадим файл README.dm. В нём обычно указывают описание проекта: ####

```bash
    touch README.dm
```

#### Заходим в созданный файл и меняем его содержимое. Все изменения производятся на языке разметки Markdown ####

#### Теперь готовим файл с сохранению командой ####

```bash
    git add --all
```

#### Можем посмотреть статус репозитория. Сохраняем файл: ####

```bash
    git commit -m "описание"
```

#### Описание принято делать осмысленным, чтобы было понятно, о каких изменениях идёт речь. #### 

#### Следующая команда позволяет посмотреть все коммиты: ####

```bash
    git log
```

#### Далее регистрируемся на GitHub и создаём удалённый репозиторий. ####

#### Теперь нам нужно создать специальный ключ по протоколу SSH. Но для ####
#### начала посмотрим, нет ли уже созданных ключей: ####

```bash
    cd ~ # перешли в домашнюю директорию
    ls -la .ssh/ # вывели список созданных ключей
```

#### Если есть какие-то файлы, их нужно удалить. #### 

#### Для генерации ключа можно использовать идну из следующих команд: ####

```bash
    ssh-keygen -t ed25519 -C "электронная почта, к которой привязан ваш аккаунт на GitHub" 
    ssh-keygen -t rsa -b 4096 -C "электронная почта, к которой привязан ваш аккаунт на Git
```

#### Проверим, что ключи действительно сгенерировались: ####

```bash
    ls -a ~/.ssh
```

#### Теперь скопируем содержимое ключа в буфер обмена: ####

```bash
    clip < ~/.ssh/id_rsa.pub 
    # или так 
    clip < ~/.ssh/id_ed25519.pub
```

#### Теперь переходим в GitHub и выбираем пункт **Settings**. Ищем окно **SSH and GPG keys**. ####
#### Выбираем **New SSH key** и вставлем в него наш ключ. ####

#### Проверить парвильность ключа можно при помощи следующей команды: ####

```bash
    ssh -T git@github.com
```

#### Теперь копируем SSH адрес репозитория и в пишем в консоли: ####

```bash
    git remote add origin "скопированный адрес"
```

#### Следующей командой можно убедиться, что репозитории связаны: ####

```bash
    git remote -v
```

3. #### Итак, файл README.md заполнен. Синхронизируем локальный и удалённый репозитории: #### 

```bash
    git push -u origin main # или master
```

#### В дальнейшем можно писать просто ####

```bash
    git push 
```

#### Поздравляею! Всё готово. ####