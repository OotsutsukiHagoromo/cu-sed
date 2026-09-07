# Набор регулярок

## Запуск

### Linux

```bash
sed -E -f redact.sed your_file
```
или
```bash
sed -E -f <путь_к_основному_каталогу>/redact.sed your_file
```
Здесь:
* `-E` — extended regexp;
* `-f` — file.

Также можно объединить ключи `-E` и `-f`:
```bash
sed -E -f redact.sed your_file
```

### MacOS

Вместо `sed` нужно везде писать `gsed`.

Установка:
```bash
brew install gsed
```

## Комментарии

* При этом вывод будет показан в терминале. Если вывод слишком длинный, можно
  использовать команду `less` или `batcat` (она же `bat`):

  ```bash
  sed -E -f redact.sed your_file | less
  # или
  sed -E -f redact.sed your_file | bat
  # или
  sed -E -f redact.sed your_file | batcat
  ```

* Если результат устраивает, можно попросить `sed` записать изменения в файл
  с помощью ключа `-i` перед именем файла:
  ```bash
  sed -E -f redact.sed -i your_file
  ```

* К ключу `-i` можно приписать строку (без пробелов!), которая будет
  интерпретироваться как суффикс имени файла резервной копии. Например,
  ```bash
  sed -E -f redact.sed -i.bak your_file
  ```
  сохранит исходный файл в `your_file.bak`, а `your_file` станет
  модифицированной версией.


* Альтернативно можно перенаправить вывод в файл:
  ```bash
  sed -E -f redact.sed > your_file
  ```

vim:ts=2:sw=2:expandtab
