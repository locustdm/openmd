### Работы с Layout
Перед вами пустое окно с одним вертикальным `Layout` (направляющей). Направляющая занимает все пространство, потому что она одна. Не важно, вертикальная или горизонтальная.

![Картинка](../../images/qt/one_layout.png)

```python
from PyQt5.QtWidgets import QApplication, QWidget, QVBoxLayout
app = QApplication([])
win = QWidget()
win.show()

main_layout = QVBoxLayout() #V - вертикальная направляющая
win.setLayout(main_layout) #устанаваливаем окну win layout - main_layout

app.exec()

```
Если создать `button` и прикрепить его к `layout`, то вне зависимости от того, является направляющая вертикальной или горизонтальной, наша кнопка растянется по всему экрану, потому что направляющая занимает все пространство.

![Картинка](../../images/qt/one_layout_one_button.png)

```python
b1 = QPushButton("Button 1")
main_layout.addWidget(b1)
```
Если мы добавим еще два `button`, то они распределятся на равном расстоянии друг от друга по вертикали, потому что у нас вертикальная направляющая.

![Картинка](../../images/qt/one_vert_layout_three_button.png)

```python
b2 = QPushButton("Button 2")
main_layout.addWidget(b2)

b3 = QPushButton("Button 3")
main_layout.addWidget(b3) 
```
Для горизонтального `layout` выглядело бы так:

![Картинка](../../images/qt/one_hor_layout_three_button.png)

А теперь вернемся к одной кнопке на окне. Удалите или закоментите `b2` и `b3`. Так же при добавлении `b1` в `main_layout` добавим аргумент `alignment=Qt.AlignLeft`. 

![Картинка](../../images/qt/one_layout_one_button_left.png)

```python
main_layout.addWidget(b1, alignment=Qt.AlignLeft)
```

`AlignLeft` - привязать к левому краю. 

Другие варианты:

1. Qt.AlignLeft - лево
2. Qt.AlignRight - право
3. Qt.AlignBottom - низ
4. Qt.AlignTop - верх
5. Qt.AlignCenter - центр 
6. Qt.AlignHCenter - центр по вертикали
7. Qt.AlignVCenter - центр по горизонтали

Так же можно так, используя `|`.

![Картинка](../../images/qt/one_layout_one_button_left_bottom.png)

```python
main_layout.addWidget(b1, alignment=Qt.AlignLeft | Qt.AlignBottom)
```

Еще пример:

![Картинка](../../images/qt/one_layout_two_button_left_bottom_top_right.png)

```python
b1 = QPushButton("Button 1")
main_layout.addWidget(b1, alignment=Qt.AlignLeft | Qt.AlignBottom)

b2 = QPushButton("Button 2")
main_layout.addWidget(b2, alignment=Qt.AlignRight | Qt.AlignTop)
```

У вас всегда должен быть один главный `layout`. Если вам нужно больше направляющих, то они должны быть размещены на одной главной. 
На изображении три вертикальные направляющие. На первой - три кнопки, на второй - две кнопки, на третьей - одна.

![Картинка](../../images/qt/three_layout_more_button.png)

```python
main_layout = QHBoxLayout() #главная горизонтальная направляющая
win.setLayout(main_layout)

left_layout = QVBoxLayout()
center_layout = QVBoxLayout()
right_layout = QVBoxLayout()

main_layout.addLayout(left_layout) #добавляю layout в главный main_layout
main_layout.addLayout(center_layout)
main_layout.addLayout(right_layout)

b1_ll = QPushButton("Button 1")
b2_ll = QPushButton("Button 2")
b3_ll = QPushButton("Button 2")

b1_cl = QPushButton("Button 1")
b2_cl = QPushButton("Button 2")

b1_rl = QPushButton("Button 1")

left_layout.addWidget(b1_ll)
left_layout.addWidget(b2_ll)
left_layout.addWidget(b3_ll)

center_layout.addWidget(b1_cl)
center_layout.addWidget(b2_cl)

right_layout.addWidget(b1_rl)
```

Для того, чтобы реализовать этот пример понадобился один дополнительный горизонтальный `layout`.

![Картинка](../../images/qt/one_add_layout.png)

```python
main_layout = QVBoxLayout()             #Главный вертикальный
win.setLayout(main_layout)

b1 = QPushButton("Button 1")            #Первая кнопка
b2_left = QPushButton("Button left")    #Вторая кнопка
b2_right = QPushButton("Button right")  #Вторая кнопка
b3 = QPushButton("Button 2")            #Третья кнопка

b2_layout = QHBoxLayout()               #Layout для двух вторых кнопок :)
b2_layout.addWidget(b2_left)            #Добавляем в Layout вторую кнопку
b2_layout.addWidget(b2_right)           #Добавляем в Layout вторую кнопку

main_layout.addWidget(b1)               #Добавляем первую кнопку
main_layout.addLayout(b2_layout)        #Добавляем layout с двумя вторыми кнопками
main_layout.addWidget(b3)               #Добавляем третью кнопку
```