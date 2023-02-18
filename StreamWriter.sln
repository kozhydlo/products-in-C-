using System;
using System.IO;

class Program
{
    static void Main()
    {
       // створити текстовий файл
        StreamWriter sw = new StreamWriter("Products.txt");

        // write some data to the file
        sw.WriteLine("Surname and Initials\tDay 1\tDay 2\tDay 3\tDay 4\tDay 5\tTotal Products");
        sw.WriteLine("Smith J.\t\t\t100\t120\t140\t150\t130\t640");
        sw.WriteLine("Doe J.\t\t\t\t80\t100\t90\t120\t110\t500");
        sw.WriteLine("Johnson S.\t\t\t90\t110\t120\t130\t110\t560");

        // close the file
        sw.Close();

        // відобразити повну таблицю даних файлу
        StreamReader sr = new StreamReader("Products.txt");
        Console.WriteLine(sr.ReadToEnd());
        sr.Close();

        // відобразити частину даних файлу з робочою інформацією
        sr = new StreamReader("Products.txt");
        string line;
        while ((line = sr.ReadLine()) != null)
        {
            if (line.StartsWith("Surname and Initials"))
            {
                Console.WriteLine(line);
                while ((line = sr.ReadLine()) != null && !line.StartsWith("\n"))
                {
                    Console.WriteLine(line);
                }
                break;
            }
        }
        sr.Close();

// прочитати файл, щоб знайти працівників, які виготовили принаймні вказану кількість продуктів
        int minProducts = 550;
        sr = new StreamReader("Products.txt");
        while ((line = sr.ReadLine()) != null)
        {
            if (line.StartsWith("\n")) continue;
            string[] fields = line.Split('\t');
            int totalProducts = int.Parse(fields[6]);
            if (totalProducts >= minProducts)
            {
                Console.WriteLine($"{fields[0]} produced {totalProducts} products.");
            }
        }
        sr.Close();
// додати дані до файлу
        sw = new StreamWriter("Products.txt", true);
        sw.WriteLine("Anderson L.\t\t80\t90\t100\t80\t70\t420");
        sw.Close();
    }
}
