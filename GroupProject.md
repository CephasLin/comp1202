```csharp
using System;
using System.IO;
using System.Text;
using static System.Console;

namespace GroupProject
{
    class MainClass
    {
        //check answer function
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
            //outpu the mark
            Console.WriteLine("{0} ",totalMark);

        }

        public static void Main(string[] args)
        {
            //read the file text line by line
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
                    //first line is the key
                    if (i == 0)
                    {
                        corAns = line;
                        i++;
                        continue;
                    }
                    //number of examiner
                    i++;
                    //from the second line, split the string by space
                    string[] s = line.Split(' ');
                    //first part of string as student ID
                    sid = s[0];
                    //second part of string as student answer
                    sans = s[1];
                    //output student ID
                    Console.Write("{0}\t\t\t", sid);
                    CheckAns(sans, corAns);
                   
                }
                //output the number of examinations
                Console.WriteLine("The total number of examinations marked: {0}", i-1);

            }
            Console.ReadKey();

        }


    }
}
