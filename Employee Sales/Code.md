```c#
using System;

namespace ConsoleApp3PastPaperJan2020_EmployeeSales
{
    class Program
    {
        static void Main(string[] args)
        {
            //declarations 
            int numberOfEmployees;

            Console.WriteLine("How many employees have worked this week?");
            numberOfEmployees = int.Parse(Console.ReadLine());

            //while loop performing as validation to enusre user enters number between 2 and 5
            while (numberOfEmployees < 2 || numberOfEmployees > 5)
            {
                Console.WriteLine("Please enter a number between 2 and 5!!");
                Console.WriteLine("How many emplyees have worked this week?");
                numberOfEmployees = int.Parse(Console.ReadLine());
            }

            double totalCommission = 0;
            int totalnumOfPropSold = 0;
            int m;
            int n;
            int bubbleSortVar = numberOfEmployees;

            //temps
            string employeeNametemp;
            string employeeIdTemp;
            int numOfPropSoldTemp;
            double salesCommissionForEachEmployeeTemp;

            double fiffteenPerCentbonus;
            double commissionRate = 500;
            int count = 0;

            string[] employeeName = new string[numberOfEmployees];
            string[] employeeID = new string[numberOfEmployees];
            int[] numOfProp = new int[numberOfEmployees];
            int[] numOfPropSold = new int[numberOfEmployees];

            double[] salesCommissionForEachEmployee = new double[numberOfEmployees];


            //enter employee details
            while (count < numberOfEmployees)
            {
                Console.WriteLine($"What is employee number {count}'s name?");
                employeeName[count] = Console.ReadLine();

                // user enters the employee's ID number - can be a mixture of letters of number 
                Console.WriteLine("What is " + employeeName[count] + "'s ID number? (It can be a mixture of letters and numbers");
                employeeID[count] = Console.ReadLine();

                // user entering number of properties to be sold 
                //validation to esnure user enters a number and a string 
                try
                {
                    Console.WriteLine("How many properties has " + employeeName[count] + " sold?");
                    numOfPropSold[count] = int.Parse(Console.ReadLine());

                }
                catch (Exception e)
                {
                    Console.WriteLine("Please only enter a number");
                    Console.WriteLine("How many properties has " + employeeName[count] + " sold?");
                    numOfPropSold[count] = int.Parse(Console.ReadLine());
                }

                count++;
            }

            //set count to 0
            count = 0;

            //Bubble sort into highester seller first 

            for (m = 0; m < numberOfEmployees - 1; m++)
            {
                for (n = 0; n < numberOfEmployees - 1; n++)
                {
                    if (numOfPropSold[n] < numOfPropSold[n + 1])

                    {
                        //sort num of properties sold 
                        numOfPropSoldTemp = numOfPropSold[n];
                        numOfPropSold[n] = numOfPropSold[n + 1];
                        numOfPropSold[n + 1] = numOfPropSoldTemp;

                        //sort names 
                        employeeNametemp = employeeName[n];
                        employeeName[n] = employeeName[n + 1];
                        employeeName[n + 1] = employeeNametemp;

                        //sort id
                        employeeIdTemp = employeeID[n];
                        employeeID[n] = employeeID[n + 1];
                        employeeID[n + 1] = employeeIdTemp;

                        //sort sales commission in order
                        salesCommissionForEachEmployeeTemp = salesCommissionForEachEmployee[n];
                        salesCommissionForEachEmployee[n] = salesCommissionForEachEmployee[n + 1];
                        salesCommissionForEachEmployee[n + 1] = salesCommissionForEachEmployeeTemp;

                    }

                }
            }

            //set count to 0
            count = 0;
            while (count < numberOfEmployees)
            {
                //calculate commission for each employee
                salesCommissionForEachEmployee[count] = numOfPropSold[count] * commissionRate;

                //calculate total commission for compnay to pay 
                totalCommission += salesCommissionForEachEmployee[count];

                //calculate total properties sold by 
                totalnumOfPropSold += numOfPropSold[count];

                count++;
            }

            Console.WriteLine("");

            //outputs
            Console.WriteLine("##############");
            Console.WriteLine("The order of who sold the most properties is:");
            Console.WriteLine("");


            count = 0;
            count = 0;

            //loop through employees in order of who sold most properties
            while (count < numberOfEmployees)
            {
                //output amount of houses sold by employee with their ID number
                Console.WriteLine(employeeName[count] + " (ID number: " + employeeID[count] + " sold " + numOfPropSold[count] + "houses");
                Console.WriteLine(employeeName[count] + " will receive a commission of " + salesCommissionForEachEmployee[count].ToString("c2"));
                Console.WriteLine("");
                count++;
            }

            //output commission and properties sold in week 
            count = 0;
            Console.WriteLine("");
            Console.WriteLine($"The total sales commission for the week is: {totalCommission.ToString("c2")}");
            Console.WriteLine($"The total amount of properties sold this week is: {totalnumOfPropSold}");

            //if statement to calculate bonus and amount of houses if there is a highest seller and has sold 1 or more houses
            if (numOfPropSold[0] > 0)
            {
                //calculate bonus 
                fiffteenPerCentbonus = (numOfPropSold[0] * commissionRate) / 100 * 15;
                //output number of houses properties by highest seller
                Console.WriteLine($"{employeeName[0]} has sold the most properties in the week. Sold {numOfPropSold[0]}");
                Console.WriteLine($"{employeeName[0]} will receive a bonus of {fiffteenPerCentbonus.ToString("c2")}");
            }

            Console.WriteLine("Press enter to exit the program");
            Console.ReadLine();
        }
    }
}

```
