# Inheritance
## Basic Inheritance

```cs
using System.Drawing;

namespace InstanceExample
{
    // base class
    class Animal
    {
        private Color bodyColor, hairColor;
        public void SetBodyColor(Color color)
        { 
            bodyColor = color;
        }
        public Color GetBodyColor()
        {
            return bodyColor;
        }
        public void SetHairColor(Color color)
        {
            hairColor = color;
        }
        public Color GetHairColor()
        {
            return hairColor;   
        }
    }
    // derived class
    class Cat : Animal
    { 
    
    }

    internal class Program
    {
        static void Main(string[] args)
        {
            var cat1 = new Cat();
            cat1.SetBodyColor(Color.White);
            cat1.SetHairColor(Color.Black);
            Console.WriteLine($"Cat 1 body color is {cat1.GetBodyColor().Name}");
            Console.WriteLine($"Cat 1 hair color is {cat1.GetHairColor().Name}");
        }
    }
}
```
## การ inherited จาก base class หลายชั้น

``` cs
 using System.Drawing;

namespace InstanceExample
{
    class Person
    {
        public int Age { get; set; }
        public string Name { get; set; }
        public void PrintAge() { Console.WriteLine($"Age = {Age}"); }
        public void PrintName() { Console.WriteLine($"Name = {Name}"); }
    }
  
    class Student : Person
    {
        public string? Major { get; set; }
        public void PrintMajor() { Console.WriteLine($"Major = {Major}"); }
        public void PrintDuty() { Console.WriteLine($"Student duty = study"); }
    }

    class Teacher : Person 
    {
        public string? Department { get; set; }
        public void PrintDepartment() { Console.WriteLine($"Department = {Department}"); }
        public void PrintDuty() { Console.WriteLine($"Teacher duty = teaching"); }
    }

    internal class Program
    {
        static void Main(string[] args)
        {
            Person p = new Person();
            Console.WriteLine($"Type of p = {p.GetType().Name}");
            p.Name = "Abdule";
            p.Age = 25;
            p.PrintName();
            p.PrintAge();

            Console.WriteLine("---------------");
            Student s = new Student();
            Console.WriteLine($"Type of s = {s.GetType().Name}" );
            s.Name = "Assanee";
            s.Age = 20;
            s.Major = "Computer";
            s.PrintName();
            s.PrintAge();
            s.PrintMajor();
            s.PrintDuty();

            Console.WriteLine("---------------");
            Teacher t1 = new Teacher();
            Console.WriteLine($"Type of t1 = {t1.GetType().Name}");
            t1.Name = "Wasant";
            t1.Age = 40;
            t1.Department = "Mathematics";
            t1.PrintName();
            t1.PrintAge();
            t1.PrintDepartment();
            t1.PrintDuty();

            Console.WriteLine("---------------");
            Teacher t2 = new Teacher();
            Console.WriteLine($"Type of t2 = {t2.GetType().Name}");
            t2.Name = "Pongsit";
            t2.Age = 40;
            t2.Department = "Mathematics";
            t2.PrintName();
            t2.PrintAge();
            t2.PrintDepartment();
            t2.PrintDuty();
        }
    }
}

```


## การปิดบัง (Masking)  สมาชิกของ Base Class
```cs
using System.ComponentModel.DataAnnotations.Schema;
using System.Drawing;

namespace InstanceExample
{
    class Person
    {
        public int? ID { get;  }
        public string? Name { get; set; }
        public Person()
        {
            ID = this.GetHashCode();
        }
    }
    class Employee : Person
    {
        public string? Department { get; set; }
        public string? Specialist { get; set; }
        public void Introduce() 
        {
            Console.WriteLine($"Hi, I'm {Name}[id = {ID}], I work in {Department}, my job is {Specialist}.");
        }

    }

    class Supervisor : Employee 
    {
        public new void Introduce()
        {
            Console.WriteLine($"Hi, I'm {Name}, a supervisor of department {Department}, I work as {Specialist}");
        }
    }

    internal class Program
    {
        static void Main(string[] args)
        {
            Employee emp = new Employee();
            emp.Name = "Wichai";
            emp.Department = "store";
            emp.Specialist = "forklift operator";
            emp.Introduce();


            Supervisor supervisor = new Supervisor();
            supervisor.Name = "Wichai";
            supervisor.Department = "store";
            supervisor.Specialist = "store supervisor";
            supervisor.Introduce();
        }
    }
}
```











