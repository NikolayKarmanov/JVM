# Домашнее задание по теме «JVM. Организация памяти, сборщики мусора, VisualVM»
### Задача 1 (обязательная)

Просмотрите код ниже и опишите (текстово или с картинками) каждую строку с точки зрения происходящего в JVM

Не забудьте упомянуть про:

* ClassLoader’ы,
* области памяти (стэк (и его фреймы), heap)
* сборщик мусора


public class JvmComprehension {

    public static void main(String[] args) {
        int i = 1;                      // 1
        Object o = new Object();        // 2
        Integer ii = 2;                 // 3
        printAll(o, i, ii);             // 4
        System.out.println("finished"); // 7
    }

    private static void printAll(Object o, int i, Integer ii) {
        Integer uselessVar = 700;                   // 5
        System.out.println(o.toString() + i + ii);  // 6
    }
}

1. Объявляется переменная i типа int и добавляется в стек.
2. Создается объект в куче (heap) и ссылка на него, которая добавляется в стек.
3. Ссылочная переменная ii типа Integer будет создана в стеке, но само значение 1 будет храниться в куче.
4. В момент вызова метода printAll() в стеке выделяется блок памяти (frame), отведенный для его нужд.
5. Ссылочная переменная uselessVar типа Integer будет создана в стеке, но само значение 700 будет храниться в куче.
6. Объект типа String создается в куче (heap).
7. 
