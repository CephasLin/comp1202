```csharp
using System;

namespace Final
{
    class MainClass
    {
        static int hailstone(int n)
        {
            int length = 1;
            string hs = "" + n;
            //stop the loop while n=1
            while (n != 1)
            {
                if (n % 2 == 1)
                {
                    n = n * 3 + 1;
                    hs += " " + n;
                    length++;
                }
                else
                {
                    n = n / 2;
                    hs += " " + n;
                    length++;
                }
            }

            Console.WriteLine(hs);
            Console.WriteLine(length);
            return length;
        }

        static double costOfRenting(int days)
        {
            double cost = 0;
            if (days == 1)
            {
                cost = 8.5;
            }
            if(days > 1 && days <= 5)
            {
                cost = 8.5 + 6.2 * (days - 1);
            }
            if(days>5)
            {
                cost = 8.5 + 6.2 * 4 + 4.5 * (days-5);
            }
            Console.WriteLine(cost);
            return cost;

        }



        static int countEven(int n)
        {
            int count = 0;
            //if the number is 0, return 1
            if (n == 0)
            {
                count = 1;
                Console.WriteLine(count);
                return count;
            }
            //if n is not 0, stop the loop if n<=0, eg： 1/10=0;
            while (n>0)
            {
                
                if (n % 10 % 2 == 0)
                {
                    count++;
                    n = n / 10;
                }
                else
                {
                    n = n / 10;

                }
            }
            Console.WriteLine(count);
            return count;

        }
        static void print1s(int n)
        {
            string s = "";
            while (n >= 1)
            {
                s += n % 10+ " ";
                n = n / 10;
            }
            Console.WriteLine(s);
        }

        static int findNum(int[] num, int n)
        {

            for (int i = 0; i < num.Length; i++)
            {
                if (num[i] > n)
                {
                    return i;
                }
            }
            return -1;
        }

        public static void Main(string[] args)
        {
            Console.WriteLine("Task1:");
            //hailstone(1);
            hailstone(10);
            //hailstone(200);
            Console.WriteLine("Task2:");
            costOfRenting(6);
            Console.WriteLine("Task3:");
            countEven(0);
            Console.WriteLine("Task4:");
            print1s(123456);
            Console.WriteLine("Task5:");
            int[] arr = { 12, 22, 32, 42, 52 };
            Console.WriteLine(findNum(arr, 32));

        }
    }
}
