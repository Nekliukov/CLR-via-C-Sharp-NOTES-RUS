# Оператор new

CLR требует, чтобы все объекты создавались оператором new. Например, объект Employee будет создаваться следующим образом:

Employee e = new Employee\("ConstructorParam1"\); 

### Оператор new выполняет следующие действия:

1. Вычисление кол-ва байтов, необходимых для хранения экземплярных полей типа и его базовых типов. В каждом объекте должны быть: указатель на объект-тип, индекс блока синхронизации.

2. Выделение памяти для объекта в управляемой куче

3. Инициализация указателя на объект-тип и индекс блока синхронизации

4. Вызов конструктора экземпляра типа

Выполнив все эти операции, new возвращает ссылку \(или указатель\) на вновь созданный объект. В предыдущем примере кода эта ссылка сохраняется в переменной e типа Employee. Кстати, у оператора new нет пары — оператора delete, то есть нет явного способа освобождения памяти, занятой объектом.

Уборкой мусора занимается среда CLR, которая автоматически находит объекты, ставшие ненужными или недоступными, и освобождает занимаемую ими память.





