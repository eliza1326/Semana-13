# Semana-13
Uso de arbol binario
Link de ejecutable del programa: https://www.programiz.com/online-compiler/9DM9VpXQy0rlF

using System;
using System.Collections.Generic;

class Program
{
    static void Main(string[] args)
    {
        // Crear un catálogo de revistas
        List<string> catalogo = new List<string>
        {
            "La Pandilla",
            "Vistazo",
            "Nature Garden",
            "Bionatura",
            "KAIROS",
            "Revista Politecnica",
            "Alteridad",
            "La Granja",
            "Revista Eugenio Espejo",
            "Carburando"
        };

        // Menú de opciones
        while (true)
        {
            Console.WriteLine("\nMenu de busqueda:");
            Console.WriteLine("1. Busqueda recursiva");
            Console.WriteLine("2. Busqueda iterativa");
            Console.WriteLine("3. Salir");
            Console.Write("Seleccione una opcion: ");
            string opcion = Console.ReadLine();

            if (opcion == "3")
            {
                break;
            }

            Console.Write("Ingrese el título a buscar: ");
            string titulo = Console.ReadLine();

            bool encontrado = false;

            switch (opcion)
            {
                case "1":
                    encontrado = BusquedaRecursiva(catalogo, titulo, 0, catalogo.Count - 1);
                    break;
                case "2":
                    encontrado = BusquedaIterativa(catalogo, titulo);
                    break;
                default:
                    Console.WriteLine("Opción no válida.");
                    continue;
            }

            Console.WriteLine(encontrado ? "Encontrado" : "No encontrado");
        }
    }

    // Búsqueda recursiva
    static bool BusquedaRecursiva(List<string> catalogo, string titulo, int inicio, int fin)
    {
        if (inicio > fin)
        {
            return false;
        }

        int medio = (inicio + fin) / 2;
        int comparacion = string.Compare(catalogo[medio], titulo, StringComparison.OrdinalIgnoreCase);

        if (comparacion == 0)
        {
            return true;
        }
        else if (comparacion > 0)
        {
            return BusquedaRecursiva(catalogo, titulo, inicio, medio - 1);
        }
        else
        {
            return BusquedaRecursiva(catalogo, titulo, medio + 1, fin);
        }
    }

    // Búsqueda iterativa
    static bool BusquedaIterativa(List<string> catalogo, string titulo)
    {
        int inicio = 0;
        int fin = catalogo.Count - 1;

        while (inicio <= fin)
        {
            int medio = (inicio + fin) / 2;
            int comparacion = string.Compare(catalogo[medio], titulo, StringComparison.OrdinalIgnoreCase);

            if (comparacion == 0)
            {
                return true;
            }
            else if (comparacion > 0)
            {
                fin = medio - 1;
            }
            else
            {
                inicio = medio + 1;
            }
        }

        return false;
    }
}
