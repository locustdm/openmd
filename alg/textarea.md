### Создание класса TextArea

Класс будет рисовать рисовать текст в прямоугольнике. Текст будет выбран случайный из списка. Выбирается случайный элемент по нажатию клавиши g. 

![Картинка](../../images/text_area.gif)

```py
class TextArea():
    def __init__(self, wn, l_text, rect, font, clr_fill, clr_text):
        self.wn = wn #окно, на котором будем рисовать 
        self.l_text = l_text #список строковых значений
        self.rect = rect #объект, который хранит x, y, width, height
        self.font = font #объект, который хранит шрифт и кегль
        self.clr_fill = clr_fill #фон прямоугольника
        self.clr_text = clr_text #цвет текста

        self.chainge_text()

    #выбрать новый случайный текст из списка l_text
    def chainge_text(self):
        self.choice_text = choice(self.l_text) #ищем случайный элемент списка l_text
        self.fr = self.font.render(self.choice_text, True, self.clr_text) #получили отрендеринный текст

    #нарисовать прямоугольник и текст
    def draw(self):
        pygame.draw.rect(
            self.wn, 
            self.clr_fill, 
            self.rect 
        ) 
        
        self.wn.blit(
           self.fr,
           (self.rect.x + 10, #+10 просто подогнала числа
            self.rect.y + 10) #+10 просто подогнала числа
        )
```


Чтобы нарисовать любой элемет, необходимо знать, на каком окне будем рисовать. Поэтому окно wn передаю в конструктор TextArea.

Так же нам необходимо знать, что нужно напечатать. Список строковых значений будет храниться в переменной l_text. Случайный элемент l_text запишем в переменную choice_text.

Объект font содержит в себе такие характеристики шрифта как стиль и кегль.

Последнее параметры в конструкторе - два тапла, clr_fill и clr_text отвечающие за цвет прямоугольника и текста.
