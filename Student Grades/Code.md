```c#
using System;

namespace ConsoleApp3StudentGradesPastPaper2021
{
    class Program
    {
        static void Main(string[] args)
        {
            //declaring the amount of students
            int numberOfStudents;

            //user will enter the amouunt of students
            Console.WriteLine("How many students in your class?");
            //Once number of students is entered, this part of code will convert this input into an integer and store in variable numberOfStudents
            numberOfStudents = int.Parse(Console.ReadLine());

            //this while loop is used to ensure user enters a min od 6 students. If user enters less, program will keep looping until a number of 6 or above is entered
            while (numberOfStudents < 6)
            {
                Console.WriteLine("The minumum students in a class are 6. Please enter a number which is 6 or above!!");
                Console.WriteLine("How many students in your class?");
                numberOfStudents = int.Parse(Console.ReadLine());
            }

            //declarations of arrays tp store the names, marks and grades of students
            string[] nameOfStudents = new string[numberOfStudents];
            int[] studentGrades = new int[numberOfStudents];
            int[] studentMarks = new int[numberOfStudents];

            // these variables will be used later in the program to sort the entered marks for the students
            int m = 0;
            int n = 0;
            int temp;
            string studentNameTemp;
            // the count variable will be used to control the while loops in the program
            int count = 0;


            // this loop will be used to allow the user to enter the names and marks for the students
            while (count < numberOfStudents)
            {
                Console.WriteLine($"Please enter a name for student {count}: ");
                nameOfStudents[count] = Console.ReadLine();


                Console.WriteLine($"Please enter a test result for {nameOfStudents[count]}: ");
                studentGrades[count] = int.Parse(Console.ReadLine());

                //ythis while loop serves as a means of validation to ensure user only enters a mark opf 100 or lower
                while (studentGrades[count] > 100)
                {
                    Console.WriteLine("The maximum test score is 100. Please enter a number which is 100 or lower");
                    Console.WriteLine($"Please enter a test result for {nameOfStudents[count]}: ");
                    studentGrades[count] = int.Parse(Console.ReadLine());
                }

                count++;
            }

            count = 0;

            //this section of the code sorts the names and marks of the students into highest to lowest order
            for (m = 0; m < studentGrades.Length - 1; m++)
            {
                for (n = 0; n < studentGrades.Length - 1; n++)
                {
                    if (studentGrades[n] < studentGrades[n + 1])
                    {
                        temp = studentGrades[n];
                        studentGrades[n] = studentGrades[n + 1];
                        studentGrades[n + 1] = temp;

                        studentNameTemp = nameOfStudents[n];
                        nameOfStudents[n] = nameOfStudents[n + 1];
                        nameOfStudents[n + 1] = studentNameTemp;
                    }
                }
            }


            string[] studentMark = new string[numberOfStudents];

            // this loop is being used to assign a grade to the students depending on the mark they receive
            count = 0;
            while (count < numberOfStudents)
            {
                if (studentGrades[count] < 40)
                {
                    studentMark[count] = "Fail";
                }

                else if (studentGrades[count] >= 40 && studentGrades[count] <= 50)
                {
                    studentMark[count] = "Pass";
                }

                else if (studentGrades[count] >= 51 && studentGrades[count] <= 69)
                {
                    studentMark[count] = "Merit";
                }

                else if (studentGrades[count] >= 70)
                {
                    studentMark[count] = "Distinction";
                }

                count++;
            }

            Console.WriteLine("");
            Console.WriteLine("###################");
            Console.WriteLine("");
            Console.WriteLine("The following is a list of student and their grades from highest to lowest");
            Console.WriteLine("");

            count = 0;

            //this part of code outputs students names, marks and grades
            while (count < numberOfStudents)
            {
                Console.WriteLine($"{nameOfStudents[count]} received a score of {studentGrades[count]}. Their grade is: {studentMark[count]}");
                Console.WriteLine("");
                count++;
            }

            Console.WriteLine("");
            Console.WriteLine("");


            // this section of code alerts the teacher if any students have achieved a distinction
            count = 0;
            while (count < numberOfStudents)
            {

                if (studentMark[count] == "Distinction")
                {
                    Console.WriteLine($"ALERT!!!! {nameOfStudents[count]} has achieved a DISTINCTION!!!");
                }
                count++;
            }

            Console.WriteLine("");
            Console.ReadLine();

        }

    }
}

```
