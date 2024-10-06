# MVC Example

Цей репозиторій містить приклад патерну проектування "MVC" (Model-View-Controller).

## Патерн MVC (Model-View-Controller)

MVC - це шаблон проектування, який розділяє програму на три основні компоненти: 

- **Model**: представляє дані та бізнес-логіку.
- **View**: відповідає за відображення даних (інтерфейс користувача).
- **Controller**: обробляє введення користувача, взаємодіє з моделлю та оновлює представлення.

### Приклад коду:

```csharp
using System;
using System.Collections.Generic;

// Модель
public class Model
{
    public string Message { get; set; } = "Привіт, MVC!";
}

// Представлення
public class View
{
    public void DisplayMessage(string message)
    {
        Console.WriteLine(message);
    }
}

// Контролер
public class Controller
{
    private readonly Model _model;
    private readonly View _view;

    public Controller(Model model, View view)
    {
        _model = model;
        _view = view;
    }

    public void UpdateView()
    {
        _view.DisplayMessage(_model.Message);
    }
}

class Program
{
    static void Main(string[] args)
    {
        // Ініціалізація компонентів
        Model model = new Model();
        View view = new View();
        Controller controller = new Controller(model, view);

        // Оновлення представлення
        controller.UpdateView();
    }
}
