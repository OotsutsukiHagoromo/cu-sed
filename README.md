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

### Windows

Для Windows есть [порт](https://github.com/mbuilov/sed-windows) (см. раздел «Pre-built executables»). Если вы скачали файл `sed-4.9-x64.exe`, то для запуска нужно набрать
```shell
sed-4.9-x64.exe -Ef redact.sed your_file
```
Если оболочка, из которой запускается программа (обычно это командная строка), знает, где находится `exe`-файл, то может сработать автозаполнение по нажатию клавиши `Tab`: достаточно набрать `sed`, а затем нажать `Tab`, и получится `sed-4.9-x64.exe`.

## Комментарии

* Вывод будет показан в терминале. Если вывод слишком длинный, можно
  использовать команду `less` или `batcat` (она же `bat`):

  ```bash
  sed -E -f redact.sed your_file | less
  # или
  sed -E -f redact.sed your_file | bat
  # или
  sed -E -f redact.sed your_file | batcat
  ```

* Если результат устраивает, можно попросить `sed` записать изменения в файл с помощью ключа `-i` перед именем файла:
  ```bash
  sed -E -f redact.sed -i your_file
  ```

* К ключу `-i` можно приписать строку (без пробелов!), которая будет интерпретироваться как суффикс имени файла резервной копии. Например,
  ```bash
  sed -E -f redact.sed -i.bak your_file
  ```
  сохранит исходный файл в `your_file.bak`, а `your_file` станет модифицированной версией.


* Альтернативно можно перенаправить вывод в файл:
  ```bash
  sed -E -f redact.sed > your_file
  ```

* Чтобы закомментировать строку или часть строки, используйте `#`

vim:ts=2:sw=2:expandtab
