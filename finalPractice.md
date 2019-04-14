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
************************************************************************
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

************************************************************************
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
************************************************************************
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
************************************************************************
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
************************************************************************        
         //1  2   3   4   5   6
        //-1 -1  -1  -1  -1  -1
        //-1 0   -1  0   -1  0
        //-1 0   0   0   -1  -1
        //-1 0   0   -1   -1  -1
        //-1 0   0   -1   0  -1
        //-1 0   0   -1   0  0
        static int closedLocker(int n )
        {

            bool[] locker= new bool[n];
            //assign "false" to each locker
            for(int q = 0; q < n; q++)
            {
                locker[q] = false;
            }

            //loop through locker number 2 to locker number n
            for (int i = 1; i < n; i++)
            {
                //Update the value of the locker
                //from number i, i+i,i+i+i
                //eg: number 2,4,6  //3,6,9 //4,8,12...
                for(int j = i; j < n; j+=i+1)
                {
                    if (locker[j] == false)
                    {
                        locker[j] = true;
                    }
                    else
                    {
                        locker[j] = false;
                    }

                }
            }
            //count the number of closed locker
            int count = 0;
            for(int p = 0; p < n; p++)
            {
                if (locker[p] == false)
                {
                    count++;
                    //Console.Write(p+" ");
                }
            }
            Console.WriteLine("");
            return count;
                      
        }
************************************************************************
        static double costOfOverdue(int days)
        {
            double cost = 0;
            for (int i = 1; i <= days; i++)
            {
                cost += 0.5 * (i - 1) + 1;
            }
            return cost;
        }
************************************************************************
        static int nthDigit(int num, int num2)
        {
            int found;
            string sNum = Convert.ToString(num);
            if (num2 <= sNum.Length)
            {
                found = sNum[num2-1];
                return found;
            }
            return -1;
        }
************************************************************************
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
            Console.WriteLine("Task6:");
            Console.WriteLine(closedLocker(6));
            Console.WriteLine("Task7:");
            Console.WriteLine(costOfOverdue(5));
            Console.WriteLine("Task8:");
            Console.WriteLine(nthDigit(9356,1));
        }
    }
}
