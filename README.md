# DataStructures
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
/*
 Author: Devin Bennett
 * Project Title: Data Structures Basic Assignment
 * Description: Using queues and dictionaries keep track of how many customers ate how many burgers and display it to the console.
 this is my change
and im going to make this change
 */
namespace ConsoleApplication4
{
    class Program
    {
        public static Random random = new Random();

        public static string randomName()
        {
            string[] names = new string[8] { "Dan Morain", "Devin Bennett", "Alison Bennett", "Chris Pratt", "Bryce Trueman", "Greg Anderson", "Alex Anderson", "Michael Jordan" };
            int randomIndex = Convert.ToInt32(random.NextDouble() * 7);
            return names[randomIndex];
        }

        public static int randomNumberInRange()
        {
           return Convert.ToInt32(random.NextDouble() * 20);
        }

        static void Main(string[] args)
        {
            //////////////////////////////////////// create variables ////////////////////////////////////////////
            int icount;
            // create the queue variable 
            Queue<string> qCustLine = new Queue<string>();
            // create dictionary variable
            Dictionary<string, int> dictionary = new Dictionary<string, int>();



            // add 100 customers to the queue line 
            for (icount = 0; icount < 100; icount++ )
            {
                qCustLine.Enqueue(randomName());

            }

           

            //////////////////// put customer and number eaten in the dictionary ///////////////////////////////
            IEnumerator<String> MyQueueEnumerator = qCustLine.GetEnumerator();

            while (MyQueueEnumerator.MoveNext())
            {
                string name = MyQueueEnumerator.Current;
                // check to see if key is already there. 
                if (dictionary.ContainsKey(name))// key is there
                {
                    dictionary[name] += randomNumberInRange();
                }
                else // key is not there
                {
                    dictionary.Add(name, randomNumberInRange());

                }

            }



            //////////////////////////////////////////// print out results ///////////////////////////////////////////
            dictionary.ToList().ForEach(x => Console.WriteLine(x.Key.PadRight(20) + x.Value));

            

            
           
            // pauses the console
            Console.ReadLine();
        }
    }
}
