# Автоматические свойства

Если необходимо создать свойства для инкапсуляции резервных полей, то в С\# есть упрощенный синтаксис, называемый автоматически реализуемыми свойствами \(Automatically Implemented Properties, AIP\). Приведу пример для свойства Name: 

```
public sealed class Employee {   
// Это свойство является автоматически реализуемым  
  public String Name { get; set; }
  private Int32 m_Age;  
  public Int32 Age {
    get { return(m_Age); }    
    set {       
      if (value < 0) // value всегда идентифицирует новое значение
         throw new ArgumentOutOfRangeException("value", value.ToString(),
           "The value must be greater than or equal to 0");      m_Age = value;
    }
  }
} 
```



