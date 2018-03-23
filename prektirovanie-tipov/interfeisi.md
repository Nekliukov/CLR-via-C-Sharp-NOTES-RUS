# Интерфейсы

Многие программисты знакомы с концепцией множественного наследования \(multiple inheritance\) — возможности определения класса, производного от двух или более базовых классов. Допустим, имеется класс TransmitData, предназначенный для передачи данных, и класс ReceiveData, обеспечивающий получение данных. Допустим, нужно создать класс SocketPort, который может и получать, и передавать данные. Для этого класс SocketPort должен наследовать одновременно от обоих классов: TransmitData и ReceiveData. Некоторые языки программирования разрешают множественное наследование, позволяя создать класс SocketPort, производный от двух базовых классов. Однако CLR \(а значит, и все основанные на этой среде языки программирования\) множественное наследование не поддерживает. Вместе с тем CLR позволяет реализовать ограниченное множественное наследование через интерфейсы \(interfaces\).

Внутри интерфейса могут хранится методы, события, свойства. Последние два в принципе и являются методами, просто в упрощённом синтаксисе. Пример объявления интерфейса:

```
public interface IDisposable {
  void Dispose();
}
public interface IEnumerable {
  IEnumerator GetEnumerator();
}
public interface IEnumerable<T> : IEnumerable {
  IEnumerator<T> GetEnumerator();
}

public interfaceICollection<T>:IEnumerable<T>,IEnumerable {
  void Add(T item);
  void Clear();
  Boolean Contains(T item);
  void CopyTo(T[] array,Int32 arrayIndex);
  Boolean Remove(T item);
  Int32  Count{get;} //Свойство только для чтения
  Boolean IsReadOnly{get;} //Свойство только для чтения
}
```

* 


