# Homework Report: Boost Libraries

## Загрузка и распаковка Boost


Скачивание архива с библиотекой boost версии 1.69.0 с помощью утилиты wget:
$ wget https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz


Разархивирование скачанного файла в директорию ~/boost_1_69_0:
$ tar -xf boost_1_69_0.tar.gz -C ~/

  
## Подсчет файлов и поиск

### Подсчет файлов (без вложенных директорий)
  
Использовал find с ограничением глубины -maxdepth 1 и типом f:
$ find ~/boost_1_69_0 -maxdepth 1 -type f | wc -l
```
12
```
  
### Подсчет файлов (включая вложенные директории)
Убрал ограничение глубины поиска:
$ find ~/boost_1_69_0 -type f | wc -l
  ```
57814
```
### Подсчет заголовочных файлов, .cpp и остальных
Для заголовочных файлов использовал маску -name "*.hpp" -o -name "*.h", для .cpp — -name "*.cpp". Чтобы учесть все, кроме них, добавил флаг -not:
$ find ~/boost_1_69_0 -type f -name "*.hpp" -o -name "*.h" | wc -l
  ```
45789
  ```
$ find ~/boost_1_69_0 -type f -name "*.cpp" | wc -l
```
  5012
```
  $ find ~/boost_1_69_0 -type f -not -name "*.hpp" -not -name "*.h" -not -name "*.cpp" | wc -l
```
  7013
```
  
### Поиск полного пути до файла any.hpp
Использовал find с точным именем файла:
$ find ~/boost_1_69_0 -type f -name "any.hpp"
  ```
/home/user/boost_1_69_0/boost/any.hpp
```
  
### Вывод файлов, где упоминается boost::asio
Использовал grep с опциями -r (рекурсивно) и -l (только имена файлов):
$ grep -rl "boost::asio" ~/boost_1_69_0
Вывод был слишком объемным, вот несколько строк из начала:
  ```
/home/user/boost_1_69_0/boost/asio.hpp
/home/user/boost_1_69_0/boost/asio/basic_socket.hpp
/home/user/boost_1_69_0/boost/asio/ip/tcp.hpp
...
```
  
## Компиляция и статические библиотеки

### Компиляция boost
Следуя инструкции, запустил скрипт начальной загрузки и движок сборки b2:
$ cd ~/boost_1_69_0
$ ./bootstrap.sh --prefix=.
$ ./b2 install
Процесс занял некоторое время. Скомпилированные библиотеки появились в директории stage/lib.

### Перенос статических библиотек
Статические библиотеки имеют расширение .a. Создал целевую директорию и скопировал их:
$ mkdir -p ~/boost-libs
$ cp ~/boost_1_69_0/stage/lib/*.a ~/boost-libs/

### Подсчет занимаемого пространства
Проверил размер каждого файла в новой директории:
$ ls -lh ~/boost-libs
  ```
total 4.2G
-rw-r--r-- 1 user user 1.5M Aug 8 12:30 libboost_atomic.a
-rw-r--r-- 1 user user 4.3M Aug 8 12:30 libboost_chrono.a
...
```
  
Для определения топ-10 самых тяжелых файлов использовал связку du, sort и head:
$ du -sh ~/boost-libs/* | sort -hr | head -n 10
  ```
45M  /root/boost-libs/libboost_wave.a
23M  /root/boost-libs/libboost_math_c99l.a
23M  /root/boost-libs/libboost_math_tr1l.a
23M  /root/boost-libs/libboost_math_c99.a
22M  /root/boost-libs/libboost_math_tr1.a
22M  /root/boost-libs/libboost_log_setup.a
22M  /root/boost-libs/libboost_log.a
21M  /root/boost-libs/libboost_serialization.a
20M  /root/boost-libs/libboost_regex.a
18M  /root/boost-libs/libboost_unit_test_framework.a
```

