# Статические классы 

Существуют классы, не предназначенные для создания экземпляров, например Console, Math, Environment и ThreadPool. У этих классов есть только статические методы. В сущности, такие классы существуют лишь для группировки логически связанных членов.

Компилятор налагает на статический класс ряд ограничений:

* Класс должен быть прямым потомком System.Object — наследование любому другому базовому классу лишено смысла, поскольку наследование применимо только к объектам, а создать экземпляр статического класса невозможно
* Класс не должен реализовывать никаких интерфейсов, поскольку методы интерфейса можно вызывать только через экземпляры класса
* В классе можно определять только статические члены \(поля, методы, свойства и события\). Любые экземплярные члены вызовут ошибку компиляции. 
* Класс нельзя использовать в качестве поля, параметра метода или локальной переменной, поскольку это подразумевает существование переменной, ссылающейся на экземпляр, что запрещено. 

Использовав ключевое слово static для класса, компилятор C\# автоматически делает его абстрактым и запечатанным \(sealed\), что логично т.к экземпляры такого класса создавать нельзя, ровно как и наследование.





