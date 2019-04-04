```csharp
using System;
using System.IO;
using System.Text;
using static System.Console;

namespace GroupProject101198598
{
    class MainClass
    {
        public static void Main(string[] args)
        {
            var watch = System.Diagnostics.Stopwatch.StartNew();
            //read the file text line by line
            try
            {
                var fileStream = new FileStream("exam.txt", FileMode.Open, FileAccess.Read);
                using (var streamReader = new StreamReader(fileStream, Encoding.UTF8))
                {
                    string line, sAns;
                    int sId;
                    string key = "";
                    int[] corRes = new int[20];
                    int counter = 0;

                    Console.WriteLine("**********MCQ STUDENT EXAM REPORT**********");
                    Console.WriteLine("ID\t\t\tMark");
                    while ((line = streamReader.ReadLine()) != "0")
                    {
                        //first line is the key
                        if (counter == 0)
                        {
                            key = line;
                            counter++;
                            continue;
                        }
                        //number of examiner
                        counter++;
                        //from the second line, split the string by space
                        string[] s = line.Split(' ');
                        //first part of string as student ID
                        sId = Convert.ToInt32(s[0]);
                        //second part of string as student answer
                        sAns = s[1];
                        //output student ID
                        int totalMark = 0;

                        //Totalmark function
                        for (int q = 0; q < 20; q++)
                        {

                            if (sAns[q] == key[q])
                            {
                                totalMark += 4;
                                //If the answer is correct, count the number of correct answer.
                                corRes[q]++;

                            }
                            else
                            {
                                if (sAns[q] == 'X')
                                {
                                    totalMark += 0;
                                }
                                else
                                {
                                    totalMark = totalMark - 1;
                                }
                            }
                        }
                        Console.WriteLine("{0}\t\t\t{1} ", sId, totalMark);
                    }

                    //if the first line of the file is not 0.
                    if (counter != 0)
                    {
                        //output the number of examinations
                        Console.WriteLine("The total number of examinations marked: {0}", counter - 1);


                        Console.Write("Question:");
                        //output the question number 1-10
                        for (int r = 0; r < 10; r++)
                        {
                            Console.Write("{0}    ", r + 1);
                        }
                        Console.WriteLine("");
                        Console.Write("#Correct:");
                        //output the #Response 1-10
                        for (int m = 0; m < 10; m++)
                        {

                            Console.Write("{0}    ", corRes[m]);
                        }
                        Console.WriteLine("");
                        Console.Write("Question:");
                        //output the question number 10-20
                        for (int r = 10; r < 20; r++)
                        {
                            Console.Write("{0}   ", r + 1);
                        }
                        Console.WriteLine("");
                        Console.Write("#Correct:");
                        //output the #Response 10-20
                        for (int m = 10; m < 20; m++)
                        {

                            Console.Write("{0}    ", corRes[m]);
                        }
                    }
                    else
                    {
                        //if the first line is 0, then output answeres not found.
                        Console.WriteLine("No student answers are found!");
                    }
                }
            }
            catch (FileNotFoundException e)
            {
                Console.WriteLine($"The file was not found: '{e}'");
            }
            catch (DirectoryNotFoundException e)
            {
                Console.WriteLine($"The directory was not found: '{e}'");
            }
            catch (IOException e)
            {
                Console.WriteLine($"The file could not be opened: '{e}'");
            }


            Console.WriteLine("");
            //stop watching the code, execution time function.
            watch.Stop();
            var elapsedMs = watch.ElapsedMilliseconds;
            Console.WriteLine("Execution time: {0}", elapsedMs * 0.001);
            Console.ReadKey();

        }


    }
}
