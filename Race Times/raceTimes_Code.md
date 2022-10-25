```c#
using System;

namespace ConsoleApp3PastPaperApril2018_RaceTimes
{
    class Program
    {
        static void Main(string[] args)
        {

            //declaration of variables and assigning default values to some of them
            string typeOfRace;
            double  numberOfParticipants;
            int[] athelteNumber = new int [] { 1, 2, 3, 4, 5, 6, 7, 8 };
            int count = 0;
            int i;
            int m;
            int n;
            double temp;
            int athelteNumberTemp; 
            int counter = 0;
    

//mens record times 
            double menWorldReTime = 9.58;
            double menEuropeanRecTime = 9.86;
            double menBritishRecRecTime = 9.87;

//wommens record times 
            double wommenWorldReTime = 10.49;
            double womenEuropeanRecTime = 10.73;
            double womenBritishRecRecTime = 10.99;


// method for error handling numbers in the program
            double ValidationAndErrorHandling (string question)
            {
                double enteredValue = 0;
                bool success = false;
                do
                {   //try and catch statment which performs part of error handling. this will ensure the user enters a number and not a letter
                    try
                    {
                        Console.WriteLine(question);
                        enteredValue = double.Parse(Console.ReadLine());
                        success = true;
                    }
                    catch (Exception e)
                    {
                        Console.WriteLine("Please enter a number only");
                    }
                }
                while (success == false);
                return enteredValue;
            }

//check if male or female race
            Console.WriteLine("Does the race involve male or female atheltes? (enter m for male, or f for female)");
            typeOfRace = Console.ReadLine();

//validation - while loop to keep running until user enters either m or f
            while (typeOfRace != "m" && typeOfRace != "f")
            {
                Console.WriteLine("please only enter (m) or (f)");
                Console.WriteLine("Does the race involve male or female atheltes? (enter m for male, or f for female)");
                typeOfRace = Console.ReadLine();
            }

// check number of participants
           numberOfParticipants = ValidationAndErrorHandling("How many Athletes participated?");
           
//validation to ensure user enters a number between 4 and 8 
            while (numberOfParticipants <4 || numberOfParticipants > 8)
            {
                Console.WriteLine("Please enter a number between 4 and 8");
// the number returned from the ValidationAndErrorHandling method will be added to the numberOfParticipants variable
                numberOfParticipants = ValidationAndErrorHandling("How many Athlete s participated?");
            }

//array to store race times
           double[] raceTimes = new double[(int)numberOfParticipants] ;

//for loop to ask the user to enter the times for each Athlete 
            for (i = 0; i < numberOfParticipants; i++)
            {
                raceTimes[i] = ValidationAndErrorHandling($"Please enter the race time for Athlete {athelteNumber[i]} in lane {i+1}");
            }

            ///bubble sort to sort the values into highest to lowest
            for (m = 0; m < raceTimes.Length -1; m++)
            {
                for (n = 0; n < raceTimes.Length -1; n++)
                {
                    if (raceTimes[n] > raceTimes[n+1])
                    {
                        // this code will spap two elements of the array and arrange in order of highest to lowest
                        temp = raceTimes[n];
                        raceTimes[n] = raceTimes[n + 1];
                        raceTimes[n + 1] = temp;

                        athelteNumberTemp = athelteNumber[n];
                        athelteNumber[n] = athelteNumber[n + 1];
                        athelteNumber[n + 1] = athelteNumberTemp;
                    }
                }
            }

            //from here will start to output results
            Console.WriteLine("");
            Console.WriteLine("The following are race times in order from highest to lowest");
            Console.WriteLine("");

            // while loop to loop through times and output the race times 
            while (count < numberOfParticipants)
            {

                Console.WriteLine($"Athlete {athelteNumber[count]} time was {raceTimes[count].ToString("0.00")} seconds");
                count++;
            }

            count = 0;
            Console.WriteLine("");

            //this statement will run if user enters race times for male race 
            if (typeOfRace == "m")
            {
                while (count < raceTimes.Length)

                {
                    if (raceTimes[count] <= menWorldReTime)
                    {
                        Console.WriteLine($"Athlete {athelteNumber[count]} has achieved a World Record Time");
                    }

                    else if (raceTimes[count] > menWorldReTime && raceTimes[count] <= menEuropeanRecTime)
                    {
                        Console.WriteLine($"Athlete {athelteNumber[count]} has achieved a European Record Time");
                    }

                    else if (raceTimes[count] > menEuropeanRecTime && raceTimes[count] <= menBritishRecRecTime)
                    {
                        Console.WriteLine($"Athlete {athelteNumber[count]} has achieved a British Record Time ");
                    }
                    count++;
                }
            }

            //this else if statement will run if user enters race times for female race 

            else if (typeOfRace == "f")
            {
                while (counter < raceTimes.Length)
                {
                    if (raceTimes[counter] <= wommenWorldReTime)
                    {
                        Console.WriteLine($"Athlete {athelteNumber[counter]} has achieved a World Record Time");
                    }

                    else if (raceTimes[counter] > wommenWorldReTime && raceTimes[counter] <= womenEuropeanRecTime)
                    {
                        Console.WriteLine($"Athlete {athelteNumber[counter]} has achieved a European Record Time");
                    }

                    else if (raceTimes[counter] > womenEuropeanRecTime && raceTimes[counter] <= womenBritishRecRecTime)
                    {
                        Console.WriteLine($"Athlete {athelteNumber[counter]} has achieved a British Record Time ");
                    }
                    counter++;
                }
 
            }

        }
    }
}
```
