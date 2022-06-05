# Словарь: общая информация и использование в Java
Словарь (dictionary) — это структура данных, позволяющая хранить информацию в виде комбинации «ключ» — «значение» (```key``` — ```value```). То есть, с каким либо значением (```value```) мы ассоциируем ключ (это может быть: id, термин и т. д.) и эту пару заносим в словарь. Обращение к элементу словаря, удаление, поиск по словарю производится по ключу.

В Java словарь определяется следующим образом:

```java
Map<String,String> dictionary = new HashMap<String,String>();
```

Класс HashMap реализует интерфейс Map.

Добавление элемента производится с помощью метода put:

```java
dictionary.put(key, value);
```

Получение значения элемента по ключу выполняется с помощью метода get:
```java
dictionary.get(key);
```

Для удаления записи с определенным ключом используется remove:
```java
dictionary.remove(key);
```

Метод ```containsKey(key)``` возвращает  ```true```, если в словаре содержится элемент с ключом key, в противном случае будет возвращено ```false```:

```Java
dictionary.containsKey(key);
```

Чтобы получить все ключевые слова, всех элементов словаря, можно вызвать keySet:
```java
dictionary.keySet();
```

Аналогично, для получения всех значений элементов ассоциативного массива используется метод ```values```:

```java
dictionary.values();
```
Метод ```size``` возвращает количество записей в словаре:
```java
dictionary.size();
```
Конструкция:

```java
dictionary.toString();
```

возвращает все пары «ключ» — «значение», содержащиеся в данном словаре.

Заметим, что методы ```keySet()```, ```values()``` и ```toString()``` возвращают элементы не в том порядке, в котором они были добавлены в словарь, а в произвольном.

# Словарь: пример программы на Java
Создадим программу на языке программирования Java, демонстрирующую работу со структурой данных — словарь (dictionary). В качестве примера возьмем такую предметную область, как «Англо-русский словарь»: добавим в него слова, обозначающие дни недели и их перевод.

В данной программе показана работа со всеми методами, разобранными выше. Весь код сопровождается комментариями.

```java
package dictionarypractice;

import java.util.HashMap;
import java.util.Map;


public class DictionaryPractice {

    public static void main(String[] args) {
        // English to Russian Dictionary
        Map<String,String> engRus = new HashMap<String,String>();

        //добавление элементов
        engRus.put("Monday", "Понедельник");
        engRus.put("Tuesday", "Вторник");
        engRus.put("Wednesday", "Среда");
        engRus.put("Thursday", "Четверг");
        engRus.put("Friday", "Пятница");

        //получение элементов
        System.out.println(engRus.get("Monday"));
        System.out.println(engRus.get("Tuesday"));
        System.out.println(engRus.get("Wednesday"));
        System.out.println(engRus.get("Thursday"));
        System.out.println(engRus.get("Friday"));

        //содержит ли словарь запись с ключом "Wednesday"?
        System.out.println(engRus.containsKey("Wednesday"));

        System.out.println(engRus.keySet());
        System.out.println(engRus.values());

        System.out.println(engRus.size());

        engRus.remove("Monday");

        System.out.println(engRus.toString());
    }
    
}
```

Демонстрация работы программы, использующей структуру данных — словарь:

![Фото примера](https://vscode.ru/wp-content/uploads/2016/08/dictionaryDemo.png)

Источник: https://vscode.ru/prog-lessons/dictionary-in-java.html
