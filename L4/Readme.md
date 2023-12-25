### Задание
- запустить ZooKeeper,
- изучить директорию с установкой ZooKeeper,
- запустить интерактивную сессию ZooKeeper CLI и освоить её команды,
- научиться проводить мониторинг ZooKeeper,
- разработать приложение с барьерной синхронизацией, основанной на ZooKeeper,
- запустить и проверить работу приложения.


С помощью zkServer.cmd запускаем сервер. Интерактивную оболочку запускаем с помощью zkCli.cmd. Выведем результат командв /help

![](https://github.com/MyCatsGitHub/big_data/blob/main/L4/screen/1.JPG?raw=true)

С помощью команды ls / получим список узлов в корне иерархической структуры данных ZooKeeper

![](https://github.com/MyCatsGitHub/big_data/blob/main/L4/screen/2.JPG?raw=true)

С помощью команды /mynode создадим новый узел "first" и проверим что он добавился

![](https://github.com/MyCatsGitHub/big_data/blob/main/L4/screen/3.JPG?raw=true)

Изменим узел на "second" и проверим что он изменился

![](https://github.com/MyCatsGitHub/big_data/blob/main/L4/screen/4.JPG?raw=true)

Создадим два нумерованных узла "seq1" и "seq2" в качестве дочерних. Флаг -s означает что узел нумерованный. Это позволяет узлы создавать улзы с уникальными именами, с помощью которых можно узнать порядок поступления
запросов на сервер

![](https://github.com/MyCatsGitHub/big_data/blob/main/L4/screen/5.JPG?raw=true)


Эмулируем работу мониторинга принадлежности клиентов к группе CLI. Для этого откроем вторую консоль и запустим zkCli.cmd. В каждой консоли создадим дочерний узел в узле mygroup и проверим что добавленные дочерние узлы
являются членами группы

![](https://github.com/MyCatsGitHub/big_data/blob/main/L4/screen/7.JPG?raw=true)

Эмулируем отключение клиента. С помощью клавиш Ctrl + D прекратим выполнение скрипта. Далее проверим что соответствующий узел пропал из списка mygroup. Изменение списка может произойти не сразу, а в промежутке времени
указанного в конфиге zoo.cfg

![](https://github.com/MyCatsGitHub/big_data/blob/main/L4/screen/8.JPG?raw=true)

В конце удалим созданные нами узлы из mygroup

![](https://github.com/MyCatsGitHub/big_data/blob/main/L4/screen/9.JPG?raw=true)


## Упражнения

### Animal task

```
Philosopher 0 is going to eat
Philosopher 4 is going to eat
Philosopher 1 is going to eat
Philosopher 2 is going to eat
Philosopher 3 is going to eat
Philosopher 2 picked up the left fork
Philosopher 2 picked up the right fork
Philosopher 5 picked up the left fork
Philosopher 5 picked up the right fork
Philosopher 4 picked up the left fork
Philosopher 5 put the right fork
Philosopher 5 put the loft fork and finished eating
Philosopher 4 picked up the right fork
Philosopher 5 is thinking
Philosopher 1 picked up the left fork
Philosopher 2 put the right fork
Philosopher 2 put the loft fork and finished eating
Philosopher 1 picked up the right fork
Philosopher 3 picked up the left fork
Philosopher 2 is thinking
Philosopher 4 put the right fork
Philosopher 1 put the right fork
Philosopher 1 put the loft fork and finished eating
Philosopher 4 put the loft fork and finished eating
Philosopher 3 picked up the right fork
Philosopher 1 is thinking
Philosopher 4 is thinking
Philosopher 4 is going to eat
Philosopher 5 picked up the left fork
Philosopher 5 picked up the right fork
Philosopher 1 is going to eat
Philosopher 2 picked up the left fork
Philosopher 5 put the right fork
Philosopher 5 put the loft fork and finished eating
Philosopher 1 picked up the left fork
Philosopher 5 is thinking
Philosopher 3 is going to eat
Philosopher 3 put the right fork
Philosopher 3 put the loft fork and finished eating
Philosopher 2 picked up the right fork
Philosopher 3 is thinking
Philosopher 4 picked up the left fork
Philosopher 4 picked up the right fork
Philosopher 2 put the right fork
Philosopher 2 put the loft fork and finished eating
Philosopher 1 picked up the right fork
Philosopher 2 is thinking
Philosopher 2 is going to eat
Philosopher 3 picked up the left fork
Philosopher 1 put the right fork
Philosopher 1 put the loft fork and finished eating
Philosopher 1 is thinking
Philosopher 4 put the right fork
Philosopher 4 put the loft fork and finished eating
Philosopher 3 picked up the right fork
Philosopher 4 is thinking
Philosopher 3 put the right fork
Philosopher 3 put the loft fork and finished eating
Philosopher 3 is thinking
```

### Двуфазный коммит
```
Waiting others clients: []
Client 1 request commit
Client 0 request rollback
Client 2 request rollback
Client 4 request commit
Client 3 request commit
Check clients
Client 0 do commit
Client 1 do commit
Client 2 do commit
Client 3 do commit
Client 4 do commit
Waiting others clients: []

