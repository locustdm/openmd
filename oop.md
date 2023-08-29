# Всё есть объектfffff

![Картинка](../images/oop/everything_is_object.jpg)

**Функция type возвращает, к какому классу относится объект**

```py
a = 555
res = type(a) #class int
a = "cat dog" 
res = type(a) #class str
a = []
res = type(a) #class list
```

**Функции split(), isdigit() и replace() на самом деле являются методам класса str**
```py
a = "cat dog frog"
res = a.split(" ")

res = a.isdigit()
    
a = "52323"
res = a.isdigit()

a = "cat-dog-frog"
res = a.replace("-","F")
```

**Так как str это обычный класс, то мы можем наследоваться от него:**
```py
class MyClass(str):
    def my_method(self):
        print("мой метод")

a = MyClass("cat") #конструктор super класса str
a.my_method() #новый метод в дочернем классе MyClass
a = a.replace(" ", "") #метод super класса
```

**Когда мы пишем int() или list(), то на самом деле создаем объекты класса int и str**
```py
a = int(5)
res = type(a) #class int

a = list()
res = type(a) #class list
```
