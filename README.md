# AADS course: lab2.3 - hash tables

Необходимо реализовать хеш-таблицу, использующую два пространства ключей:
+ Просматриваемая таблица, организованная вектором.
+ Перемешанная таблица, использующая перемешивание сложением.

### Структура для элементов первой таблицы:

``` C
struct KeySpace1 {
  // ключ элемента
  KeyType1 key;
  // указатель на информацию
  Item* info;
};
```

### Структура для элементов второй таблицы:
 
``` C
struct KeySpace2 {
  // признак занятости элемента
  BusyType2 busy;
  // ключ элемента
  KeyType2 key;
  // указатель на информацию
  Node2* node;
};
```

### Указатель на информацию, определяющий список элементов с одинаковыми значениями ключей:
``` C
struct Node2 {
  // номер версии элемента
  RelType2 release;
  // указатель на информацию
  InfoType *info;
  // указатель на следующий элемент
  Node2 *next;
};
```

### Общие замечания:
В таблице не могут присутствовать два элемента с одинаковыми составными ключами.

### Замечание к первой таблице:
+ максимальный размер пространства ключей ограничен величиной msize1, значение которой
определяется при инициализации таблицы.
+ в пространстве не может быть двух элементов с одинаковыми ключами.
В данном пространстве ключей предусмотрены следующие особые операции:
  + поиск элементов, заданных диапазоном ключей; в таблице могут отсутствовать элементы с
ключами, задающими диапазон; результатом поиска должна быть новая таблица, содержащая
найденные элементы.

### Замечания ко второй таблице:
+ максимальный размер массива указателей ограничен величиной msize2, значение которой определяется при инициализации таблицы
+ для доступа к элементам таблицы использовать двойное хеширование.
+ в пространстве могут находиться несколько элементов с одинаковыми ключами и разными номерами версий. В данном пространстве ключей предусмотрены следующие особые операции:
  + поиск в таблице всех версий элемента, заданного ключом, или конкретной (заданной) версии
элемента, также заданного своим ключом; результатом поиска должна быть новая таблица, содержащая найденные элементы;
  + удаление из таблицы всех элементов с заданным ключом или элемента определенной версии,
также заданного своим ключом.
