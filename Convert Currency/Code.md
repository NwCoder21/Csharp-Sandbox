```c#

using System;

namespace ConsoleApp3MockTest20._10._21
{
    class Program
    {
        static void Main(string[] args)
        {

            //declarations 
            double amountToConvert;
            double convertTo;
            string choice = "";
            string choice1;
            double afterConvert = 0;
            double maxLimit = 2500;
            double americanDollars = 1.40;
            double euros = 1.14;
            double brazillianReal = 4.77;
            double japaneseYen = 151.05;
            double turkishLira = 5.68;
            string [] currency = new string [6] { "", "American Dollars", "Euros", "Brazilian Real", "Japanese Yen", "Turkish Lira" };
            double transactionFee;
            double totalCost;
            double discount;  
            bool memberOfStaff = false;
            int i = 0;

            Console.WriteLine("How much would you like to convert from pounds?");

            //inputs
            amountToConvert = double.Parse(Console.ReadLine());

            //loop to ensure no more han 2500 is being converted
            while (amountToConvert > maxLimit)
            {
                Console.WriteLine("You can convert a maximum of £2500 in one transaction");
                Console.WriteLine("How much would you like to convert from pounds?");
                amountToConvert = double.Parse(Console.ReadLine());
            }

            //loop to output options of conversion
            for (i = 1; i <6; i++)
            {
                Console.WriteLine("Press " + i + " to convert to " + currency [i]);
            }

            convertTo = double.Parse(Console.ReadLine());

            //if statement to calculate conversion 
            if (convertTo == 1)
            {
                afterConvert = amountToConvert * americanDollars;
                choice = "American Dollars";
            }
            else if (convertTo == 2)
            {
                afterConvert = amountToConvert * euros;
                choice = "Euros";
            }
            else if (convertTo == 3)
            {
                afterConvert = amountToConvert * brazillianReal;
                choice = "Brazillian Real";
            }
            else if (convertTo == 4)
            {
                afterConvert = amountToConvert * japaneseYen;
                choice = "Japanese Yen";
            } 
            
            else if (convertTo == 5)
            {
                afterConvert = amountToConvert * turkishLira;
                choice = "Turkish Lira";
            }
            //else statement to ensure only number between 1-5 is entered
            else
            {
                Console.WriteLine("Enter a number between 1 - 6");
                for (i = 0; i < 6; i++)
                {
                    Console.WriteLine("Press " + i + "to convert to " + currency[i]);
                    convertTo = double.Parse(Console.ReadLine());
                }

            }

            // If statement to calculate transaction fee
            if (amountToConvert <= 300)
            {

                transactionFee = amountToConvert / 100 * 3.5;
            }

            else if (amountToConvert > 300 && amountToConvert <= 750)
            {
                transactionFee = amountToConvert / 100 * 3;
            }

            else if (amountToConvert > 750 && amountToConvert <= 1000)
            {
                transactionFee = amountToConvert / 100 * 2;
            }

            else
            {
                transactionFee = amountToConvert / 100 * 1.5;
            }

            totalCost = afterConvert + transactionFee;
            Console.WriteLine("Is the customer a member of staff? (true or false) ");


            try
            {
                memberOfStaff = bool.Parse(Console.ReadLine());
            }
            
            catch (Exception e)
            {
                Console.WriteLine("Please enter true or false");
                memberOfStaff = bool.Parse(Console.ReadLine());
            }

            if (memberOfStaff == true)
            {
                totalCost -= totalCost / 100 * 5;
            }

            //outputs
            Console.WriteLine("========================");
            Console.WriteLine("SUMMARY");
            Console.WriteLine("£"+ amountToConvert + " when converted into " + choice +  " will be "  + afterConvert.ToString("0.00"));
            Console.WriteLine("The transaction fee is £" + transactionFee.ToString("0.00"));

            //if statement to display discount only if customer is member of staff
            if (memberOfStaff == true)
            {
                discount = totalCost / 100 * 5;
                Console.WriteLine("Today you receive a discount of £" + discount.ToString("0.00"));
            }

            Console.WriteLine("The total amount you need to pay is £" + totalCost.ToString("0.00"));

            //console.readline to prevent program from closing automatically 
            Console.ReadLine();

        }
    }
}

```
