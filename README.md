# Eelarve-Arvutaja
```
namespace Eelarve_Arvutaja
{
    internal class Program
    {
        static void Main(string[] args)
        {
            string kasutajaNimi = "";
            while (kasutajaNimi == "")
            {
                Console.WriteLine("Tere, sisesta oma nimi");
                kasutajaNimi = Console.ReadLine();
            }

            string sisestus = "";
            Console.WriteLine("Sisesta tulud ükshaaval, kui on kõik, siis kirjuta \"rohkem pole\"");
            List<float> tulud = VõtaKasutajaltMituSisenditJärjest();
            Console.WriteLine("Sisesta OMA MULUD ükshaaval, kui on kõik, siis kirjuta \"rohkem pole\"");
            List<float> kulud = VõtaKasutajaltMituSisenditJärjest();


            float tuludkokku = 0;
            tuludkokku = ArvutaKokku(tulud);
            float kuludkokku = ArvutaKokku(kulud);


            float kokku = (float) Math.Round((tuludkokku - kuludkokku),2);

            Console.WriteLine($"Kasutaja: {kasutajaNimi}, teie kontoseis on: {kokku}");
        }



 


        
        private static float ArvutaKokku(List<float> tulud)
        {
            float kokku = 0;
            for (int i = 0; i < tulud.Count; i++)
            {
                kokku += tulud[i];
            }

            return kokku;
        }

        private static List<float> VõtaKasutajaltMituSisenditJärjest()
        {
            List<float> tulud = new List<float>();
            string sisestus;
            do
            {
                Console.WriteLine("Sisesta oma andmed *ÜKSHAAVAL* - järgmine sisestus");
                sisestus = Console.ReadLine();
                if (sisestus == "rohkem pole")
                {
                    break;
                }
                float conversion = float.Parse(sisestus);
                tulud.Add(conversion); 
            } while (sisestus != "rohkem pole") ;
            return tulud;
        }
    }
}
