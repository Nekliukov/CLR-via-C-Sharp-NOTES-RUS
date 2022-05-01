### Обобщённые интерфейсы
Конечно же, основное преимущество обобщений — это способность определять обобщенные ссылочные и значимые типы. Но для CLR также исключительно важна поддержка обобщенных интерфейсов. Без них любая попытка работы со значимым типом через необобщенный интерфейс (например, IComparable) всякий раз будет приводить к необходимости упаковки и потере безопасности типов в процессе компиляции, что сильно сузило бы область применения обобщенных типов.
Определение обобщенного интерфейса из библиотеки FCL (из пространства имен System.Collections.Generic) выглядит следующим образом:
```
public interface IEnumerator<T> : IDisposable, IEnumerator {
  T Current { get; }
}
```
Использование обобщённых интерфейсов очень удобно в случае, когда мы будем реализоваывать его в некотором классе, но с каким именно типом будет работать интерфейс, ещё не решили. Например, операция ADD. В случае типа Int32 нам нужно будет реализовать обобщённый интерефейс с этим типов так, чтобы числа складывались по правилам математики. Если же выбранный нами тип будет String, то в методе ADD реализуемого интерфейса, мы должны произвести конкатенацию строк. Пример:
```
interface IOperators<T> {
        T Add(T arg1, T arg2);
    }

    public class Ints: IOperators<int>{
        public int Add(int arg1, int arg2){
            return arg1 + arg2;
        }
    }

    public class Strings: IOperators<string>{
        public string Add(string s1, string s2){
            return s1 + s2;
        }
    }

    class Program{
        static void Main(string[] args){
            Console.WriteLine("-------Generic Interfaces----------");
            
            Strings strs = new Strings();
            Console.WriteLine(strs.Add("Ro", "man")); //Roman

            Ints ints = new Ints();
            Console.WriteLine(ints.Add(66, 3)); //69
            Console.ReadLine();
        }
    }
```
