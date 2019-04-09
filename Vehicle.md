```csharp
//************Vehicle Class**************
using System;
namespace wk12_2
{
    public class Vehicle
    {
        private string plateNumber;
        private bool status;
        private int fuelLevel;
        private int maxFuel;
        private int speed;
        private int maxSpeed;
        private int passenger;
        private string name;

        public Vehicle(string pl,int mf, int ms)
        {
            plateNumber = pl;
            maxFuel = mf;
            maxSpeed = ms;

            status = false;
            fuelLevel = 30;
            speed = 0;

            passenger = 0;
            name = "";
        }
        public void turnOn()
        {
            if(fuelLevel > 0)
            {
                status = true;
                Console.WriteLine("Car {0} turned on!", plateNumber);
            }
            else
            {
                Console.WriteLine("Car {0} turned off!", plateNumber);
            }
        }

        public void turnOff()
        {
            speed = 0;
            status = false;
            Console.WriteLine("Car {0} turned off!", plateNumber);
        }

        //addFuel
        public void addFuel(int amt)
        {
            if (status == false)
            {
                if (amt + fuelLevel <= maxFuel)
                {
                    fuelLevel += amt;
                }
                else
                {
                    Console.WriteLine("Too must fuel to add!");
                }
            }
            else
            {
                Console.WriteLine("You must turn off to add fuel!");
            }


        }

        //speedUp()
        public void speedUp()
        {
            if(status == true)
            {
                if ((fuelLevel>1) && (speed+5<maxSpeed))
                {
                    speed += 5;
                    fuelLevel -= 1;
                }
                else
                {
                    status = false;
                }
            }
            else
            {
                Console.WriteLine("You must turn the car on first!");
            }
        }

        public void slowDown()
        {
            if(status == true)
            {
                if (speed - 5 >= 0)
                {
                    speed -= 5;
                }
            }
            else
            {
                Console.WriteLine("You must turn the car on first");
            }
        }

        public void addPerson(string n)
        {
            if (passenger <= 5)
            {
                passenger++;
                name = n;
                Console.WriteLine("Guest {0}:{1}", passenger, name);
            }
            else
            {
                Console.WriteLine("Car is full now!");
            }
        }


        public void setPlateNumber(string pn) { plateNumber = pn; }
        public void setStatus(bool s) { status = s; }
        public void setfuelLevel(int fl) { fuelLevel = fl; }
        public void setMaxFuel(int mf) { maxFuel = mf; }
        public void setMaxSpeed(int ms) { maxSpeed = ms; }
        public void setSpeed(int s) { speed = s; }
       

        public string toString()
        {
            string s = "Plate number:" + plateNumber + "\nFuel level " + fuelLevel
                + "\nMax fuel:" + maxFuel + "\nMax speed:" + maxSpeed + "\nSpeed:"
                + speed + "\nPassenger number:"+passenger;
            if (status)
            {
                s += "\nStatus:" + "ON\n";
            }
            else
            {
                s += "\nStatus:" + "OFF\n";
            }


            return s;
        }
    }
}

******************Main***********************
using System;

namespace wk12_2
{
    class MainClass
    {
        public static void Main(string[] args)
        {
            /* Vehicle car1 = new Vehicle("BMW",35,205);
             Vehicle car2 = new Vehicle("SAD", 135, 125);
             Vehicle car3 = new Vehicle("ERF", 95, 125);
             Console.WriteLine(car1.toString());
             Console.WriteLine(car2.toString());
             Console.WriteLine(car3.toString());*/

            Vehicle car1 = new Vehicle("BMW", 50, 200);
            Console.WriteLine(car1.toString());

            car1.addFuel(15);
            Console.WriteLine(car1.toString());


            car1.turnOn();
            Console.WriteLine(car1.toString());

            car1.speedUp();
            Console.WriteLine(car1.toString());
            
            car1.speedUp();
            Console.WriteLine(car1.toString());

            car1.slowDown();
            Console.WriteLine(car1.toString());
            
            car1.turnOff();
            Console.WriteLine(car1.toString());

            Person p1 = new Person("Frank", 18);
            car1.addPerson(p1.getName());
            Person p2 = new Person("Tom", 18);
            car1.addPerson(p2.getName());
            Person p3 = new Person("Jim", 18);
            car1.addPerson(p1.getName());
            Console.WriteLine(car1.toString());

        }
    }
}

****************Person Class*****************
using System;
namespace wk12_2
{
    public class Person
    {
        private string name;
        private int age;

        public Person(string n, int a)
        {
            name = n;
            age = a;
        }

        public string getName()
        {
            return name;
        }

    }
}
