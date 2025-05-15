using System;
using System.Collections.Generic;
using System.Linq;

class Rectangle
{
   // Захищені поля
   protected int a, b;
   protected int color;

   // Конструктор
   public Rectangle(int a, int b, int color)
   {
       this.a = a;
       this.b = b;
       this.color = color;
   }

   // Властивості
   public int A
   {
       get { return a; }
       set { a = value; }
   }

   public int B
   {
       get { return b; }
       set { b = value; }
   }

   public int Color
   {
       get { return color; }
   }

   // Методи
   public void Display()
   {
       Console.WriteLine($"Прямокутник: Сторони = {a}, {b}; Колір = {color}");
   }

   public int Perimeter()
   {
       return 2 * (a + b);
   }

   public int Area()
   {
       return a * b;
   }

   public bool IsSquare()
   {
       return a == b;
   }
}

class task1
{
   static void Main()
   {
       List<Rectangle> rectangles = new List<Rectangle>
       {
           new Rectangle(4, 5, 1),
           new Rectangle(6, 6, 2),
           new Rectangle(3, 4, 3),
           new Rectangle(5, 5, 4),
           new Rectangle(7, 8, 5)
       };

       int squareCount = 0;

       foreach (var rect in rectangles)
       {
           rect.Display();
           Console.WriteLine($"Периметр: {rect.Perimeter()}");
           Console.WriteLine($"Площа: {rect.Area()}");
           if (rect.IsSquare())
           {
               Console.WriteLine("Це квадрат!");
               squareCount++;
           }
           Console.WriteLine();
       }

       Console.WriteLine($"Кількість квадратів: {squareCount}");
   }
}


using System;
using System.Collections.Generic;
using System.Linq;


// Базовий клас
abstract class Employee
{
    protected string name;
    protected int age;
    protected double salary;

    public Employee(string name, int age, double salary)
    {
        this.name = name;
        this.age = age;
        this.salary = salary;
    }

    public abstract void Show();

    public double Salary => salary;
}

// Похідні класи
class Worker : Employee
{
    private string position;

    public Worker(string name, int age, double salary, string position)
        : base(name, age, salary)
    {
        this.position = position;
    }

    public override void Show()
    {
        Console.WriteLine($"Робiтник: {name}, Вiк: {age}, Посада: {position}, Зарплата: {salary}");
    }
}

class HR : Employee
{
    private int employeesManaged;

    public HR(string name, int age, double salary, int employeesManaged)
        : base(name, age, salary)
    {
        this.employeesManaged = employeesManaged;
    }

    public override void Show()
    {
        Console.WriteLine($"Кадровик: {name}, Вiк: {age}, Кiлькiсть спiвробiтникiв: {employeesManaged}, Зарплата: {salary}");
    }
}

class Engineer : Employee
{
    private string specialty;

    public Engineer(string name, int age, double salary, string specialty)
        : base(name, age, salary)
    {
        this.specialty = specialty;
    }

    public override void Show()
    {
        Console.WriteLine($"Iнженер: {name}, Вiк: {age}, Спецiальнiсть: {specialty}, Зарплата: {salary}");
    }
}

class Administration : Employee
{
    private string department;

    public Administration(string name, int age, double salary, string department)
        : base(name, age, salary)
    {
        this.department = department;
    }

    public override void Show()
    {
        Console.WriteLine($"Адмiнiстрацiя: {name}, Вiк: {age}, Вiддiл: {department}, Зарплата: {salary}");
    }
}

class task2
{
    static void Main()
    {
        List<Employee> employees = new List<Employee>
        {
            new Worker("Iван", 30, 25000, "Слюсар"),
            new HR("Марiя", 40, 30000, 50),
            new Engineer("Петро", 35, 35000, "Електронiка"),
            new Administration("Ольга", 45, 40000, "Фiнанси"),
            new Worker("Андрiй", 28, 24000, "Маляр")
        };

        Console.WriteLine("Данi про працiвникiв до сортування:");
        foreach (var emp in employees)
        {
            emp.Show();
        }

        employees = employees.OrderBy(e => e.Salary).ToList();

        Console.WriteLine("\nПрацiвники пiсля сортування за зарплатою:");
        foreach (var emp in employees)
        {
            emp.Show();
        }
    }
}
