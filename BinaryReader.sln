using System;
using System.IO;

class Program
{
    static void Main()
    {
        //  створити двійковий файл
        using (BinaryWriter bw = new BinaryWriter(File.Open("Products.dat", FileMode.Create)))
        {
            // write some data to the file
            bw.Write("Surname and Initials\tDay 1\tDay 2\tDay 3\tDay 4\tDay 5\tTotal Products");
            bw.Write("Smith J.\t\t\t100\t120\t140\t150\t130\t640");
            bw.Write("Doe J.\t\t\t\t80\t100\t90\t120\t110\t500");
            bw.Write("Johnson S.\t\t\t90\t110\t120\t130\t110\t560");
        }

        // відобразити повну таблицю даних файлу
        using (BinaryReader br = new BinaryReader(File.Open("Products.dat", FileMode.Open)))
        {
            Console.WriteLine(br.ReadString());
            Console.WriteLine(br.ReadString());
            Console.WriteLine(br.ReadString());
            Console.WriteLine(br.ReadString());
        }

        // відобразити частину даних файлу з інформацією про працівника
        using (BinaryReader br = new BinaryReader(File.Open("Products.dat", FileMode.Open)))
        {
            string line;
            while ((line = br.ReadString()) != null)
            {
                if (line.StartsWith("Surname and Initials"))
                {
                    Console.WriteLine(line);
                    while ((line = br.ReadString()) != null && !line.StartsWith("\n"))
                    {
                        Console.WriteLine(line);
                    }
                    break;
                }
            }
        }

        // прочитайте файл, щоб знайти працівників, які виготовили принаймні вказану кількість продуктів
        int minProducts = 550;
        using (BinaryReader br = new BinaryReader(File.Open("Products.dat", FileMode.Open)))
        {
            string line;
            while ((line = br.ReadString()) != null)
            {
                if (line.StartsWith("\n")) continue;
                string[] fields = line.Split('\t');
                int totalProducts = int.Parse(fields[6]);
                if (totalProducts >= minProducts)
                {
                    Console.WriteLine($"{fields[0]} produced {totalProducts} products.");
                }
            }
        }

        // додати дані до файлу
        using (BinaryWriter bw = new BinaryWriter(File.Open("Products.dat", FileMode.Append)))
        {
            bw.Write("Anderson L.\t\t80\t90\t100\t80\t70\t420");
        }
    }
}
