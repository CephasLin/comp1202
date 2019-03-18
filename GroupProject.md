```csharp
using System;
using System.IO;
using System.Text;
using static System.Console;

namespace GroupProject
{
    class MainClass
    {

        static void CheckAns(string ans,string corAns)
        {
            int totalMark = 0;
            for(int i =0; i<20; i++)
            {
                if (ans[i] == corAns[i])
                {
                    totalMark += 4;
                }
                if (ans[i] == 'X')
                {
                    totalMark += 0;
                }
                else
                {
                    totalMark -= 1;
                }
            }
            Console.WriteLine("{0} ",totalMark);

        }

        public static void Main(string[] args)
        {
            var fileStream = new FileStream("exam.txt", FileMode.Open, FileAccess.Read);
            using (var streamReader = new StreamReader(fileStream, Encoding.UTF8))
            {
                string line, sid, sans;
                string corAns =" ";
                int i = 0;
                Console.WriteLine("**********MCQ STUDENT EXAM REPORT**********");
                Console.WriteLine("ID\t\t\tMark");
                while ((line = streamReader.ReadLine()) != null)
                {
                    if (i == 0)
                    {
                        corAns = line;
                        i++;
                        continue;
                    }
                    string[] s = line.Split(' ');
                    sid = s[0];
                    sans = s[1];

                    Console.Write("{0}\t\t\t", sid);
                    CheckAns(sans, corAns);
                }

            }
            Console.ReadKey();


        }


    }
}
