# ITS-104
ITS 104 


using System;

class StudentGrades
{
    static void Main()
    {

        int[] grades = {85, 90, 78, 92, 88, 95, 75, 80, 72, 89, 94, 91, 65, 70, 68};

        int numStudents = 5; 
        int numSubjects = 3;

       
        Console.WriteLine("Grades Matrix:");
        for (int i = 0; i < numStudents; i++)
        {
            Console.Write($"Student {i + 1}: ");
            for (int j = 0; j < numSubjects; j++)
            {
                Console.Write(grades[i * numSubjects + j] + " ");
            }
            Console.WriteLine();
        }
        Console.WriteLine();

        Console.WriteLine("Average Grades:");
        for (int i = 0; i < numStudents; i++)
        {
            int total = 0;
            for (int j = 0; j < numSubjects; j++)
            {
                total += grades[i * numSubjects + j];
            }
            double average = (double)total / numSubjects;
            Console.WriteLine($"Student {i + 1}: {average:F2}");
        }
        Console.WriteLine();

       
        Console.WriteLine("Lowest Grade per Student:");
        for (int i = 0; i < numStudents; i++)
        {
            int lowest = grades[i * numSubjects];
            for (int j = 1; j < numSubjects; j++)
            {
                if (grades[i * numSubjects + j] < lowest)
                {
                    lowest = grades[i * numSubjects + j];
                }
            }
            Console.WriteLine($"Student {i + 1}: {lowest}");
        }
        Console.WriteLine();

    
        Console.WriteLine("Highest Grade per Subject:");
        for (int j = 0; j < numSubjects; j++)
        {
            int highest = grades[j];
            for (int i = 1; i < numStudents; i++)
            {
                if (grades[i * numSubjects + j] > highest)
                {
                    highest = grades[i * numSubjects + j];
                }
            }
            Console.WriteLine($"Subject {j + 1}: {highest}");
        }
        Console.WriteLine();


        Console.WriteLine("Median Grade per Subject:");
        for (int j = 0; j < numSubjects; j++)
        {
            int[] subjectGrades = new int[numStudents];
            for (int i = 0; i < numStudents; i++)
            {
                subjectGrades[i] = grades[i * numSubjects + j];
            }
            Array.Sort(subjectGrades);
            double median;
            int mid = subjectGrades.Length / 2;
            if (subjectGrades.Length % 2 == 0)
                median = (subjectGrades[mid - 1] + subjectGrades[mid]) / 2.0;
            else
                median = subjectGrades[mid];
            
            Console.WriteLine($"Subject {j + 1}: {median}");
        }
        Console.WriteLine();

      
        Console.WriteLine("Median Grade for All Students (Total):");
        int[] allGrades = new int[numStudents * numSubjects];
        for (int i = 0; i < numStudents; i++)
        {
            for (int j = 0; j < numSubjects; j++)
            {
                allGrades[i * numSubjects + j] = grades[i * numSubjects + j];
            }
        }
        Array.Sort(allGrades);
        double totalMedian;
        int totalMid = allGrades.Length / 2;
        if (allGrades.Length % 2 == 0)
            totalMedian = (allGrades[totalMid - 1] + allGrades[totalMid]) / 2.0;
        else
            totalMedian = allGrades[totalMid];

        Console.WriteLine($"Total Median Grade: {totalMedian}");
    }
}
