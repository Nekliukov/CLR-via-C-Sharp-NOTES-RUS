# Обобщённые делегаты

Поддержка обобщенных делегатов в CLR позволяет передавать методам обратного вызова любые типы объектов, обеспечивая при этом безопасность типов. Более того, благодаря обобщенным делегатам экземпляры значимого типа могут передаваться методам обратного вызова без упаковки. Делегат — это просто определение класса с помощью четырех методов: конструктора и методов Invoke, BeginInvoke и EndInvoke. При определении типа делегата с параметрами типа компилятор задает методы класса делегата, а параметры типа применяются ко всем методам, параметры и возвращаемые значения которых относятся к указанному параметру типа.  
Например, обобщенный делегат определяется следующим образом:

```
 public delegate TReturn CallMe<TReturn, TKey, TValue>(
    TKey key, TValue value);
```

Компилятор превращает его в класс, который на логическом уровне выглядит так:

```
 public sealed class CallMe<TReturn, TKey, TValue> : MulticastDelegate {
    public CallMe(Object object, IntPtr method);    
    public virtual TReturn Invoke(TKey key, TValue value);
    public virtual IAsyncResult BeginInvoke(TKey key, TValue value,
         AsyncCallback callback, Object object);  
    public virtual TReturn EndInvoke(IAsyncResult result);
}
```



