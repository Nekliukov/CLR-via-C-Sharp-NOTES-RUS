# Свойства с параметрами \(Индексаторы\)

**Индексаторы** позволяют индексировать объекты и использовать их как массивы. Фактически индексаторы позволяют нам создавать специальные хранилища объектов или коллекции. По форме они напоминают свойства со стандартными методами `get` и `set`, которые возвращают и присваивают значение.

Допустим, у нас есть класс Book, представляющий книгу, и класс Library, который представляет библиотеку и используется для хранения набора книг. Используем индексаторы для определения класса Library:

```
class Program
{
    static void Main(string[] args)
    {
        Library library = new Library();
 
        Console.WriteLine(library[0].Name);
 
        library[0] = new Book("Преступление и наказание");
 
        Console.WriteLine(library[0].Name);
 
        Console.ReadLine();
    }
}
 
class Book
{
    public Book(string name)
    {
        this.Name=name;
    }
    public string Name { get; set; }
}
     
class Library
{
    Book[] books;
 
    public Library()
    {
        books = new Book[] { new Book("Отцы и дети"), new Book("Война и мир"), 
                new Book("Евгений Онегин") };
    }
 
    public int Length
    {
        get { return books.Length; }
    }
 
    public Book this[int index]
    {
        get
        {
            return books[index];
        }
        set
        {
            books[index] = value;
        }
    }
}
```

В классе Library определен массив Book, к которому мы будем обращаться с помощью индексатора. А само определение индексатора напоминает свойство: `public Book this[int index]`. Здесь определяем, во-первых, тип возвращаемого или присваиваемого объекта, то есть Book. Во-вторых, определяем через параметр `int index` способ доступа к элементам.

И после этого в основной программе можно обращаться к объекту Library как к массиву: `library[0].Name`. Так как индексатор использует тип Book, то library\[0\] будет представлять объект Book.

