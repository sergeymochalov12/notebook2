package ru.geekbrains.api.lesson4.test;

import java.util.HashMap;
import java.util.HashSet;
import java.util.Map;
import java.util.Scanner;
import java.util.Set;


public class Notebook {
    // значания для каждого ноутбука
    String name;
    String cpu;
    int hdd;
    int ram;
    String os;
    int price;
    double diagonal;

    public Notebook(String name, int ram, int hdd, String cpu, String os, double diagonal, int price) { // конструктор для объекта
        //this.id = counter++;
        this.name = name; // производитель
        this.ram = ram; // ОЗУ Гб
        this.os = os; // Операционная система
        this.diagonal = diagonal; // диагональ экрана
        this.cpu = cpu; // тип процессора
        this.hdd = hdd; // объем жесткого диска
        this.price = price; // цена
    }
    @Override // описываем метод toSting для вывода строки с характеристиками товара
    public String toString() {
        return String.format("Производитель: %s \n объем оперативной памяти: %d Гб \n объем накопителя % d Гб \n ОС %s \n Тип процессора %s \n Диагональ %1f \n Цена, руб.  %d \n",
                this.name, this.ram, this.hdd, this.os, this.cpu, this.diagonal, this.price);
    }
}
         class App {

            public static void main(String[] args) throws Exception {
                Set<Notebook> unicNotebook = getNotebooks();
                System.out.printf("Всего  ноутбуков: %d \n",unicNotebook.size(), " шт.");

                Map<Integer, String> mapCrit = new HashMap<>();

                mapCrit.put(1, "объем оперативной памяти");
                mapCrit.put(2, "объем накопителя");
                mapCrit.put(3, "ОС");
                mapCrit.put(4, "CPU");
                mapCrit.put(5, "Диагональ");
                mapCrit.put(6, "Цена");

                Scanner sc = new Scanner(System.in);
                System.out.println("Введите желаемые характеристики: \n бъем оперативной памяти:");
                int ramUser = sc.nextInt();
                System.out.println("объем накопителя: ");
                int hddUser = sc.nextInt();

                System.out.println("Цена ");
                double priceUser = sc.nextInt();

                for (Notebook note : unicNotebook) {

                    if ((note.ram   >= ramUser) && (note.hdd >= hddUser) && note.price  >= priceUser) {
                        System.out.println(note.toString());
                    }
                }
                sc.close();
            }

             private static Set<Notebook> getNotebooks() {
                 Notebook notebook1 = new Notebook("Lenovo", 8, 500, "Intel", "Windows 11",  15.6, 40000);
                 Notebook notebook2 = new Notebook("Acer", 4, 250,"Intel", "Windows 10",  11, 35000);
                 Notebook notebook3 = new Notebook ("Honor", 16, 512, "AMD",  "Ubuntu",16.1, 55000);
                 Notebook notebook4 = new Notebook( "Apple", 32, 1024, "M1", "MacOs", 13.3, 100000);
                 Notebook notebook5 = new Notebook("HP", 16, 1024,  "Intel", "nonOS", 15.6, 40000);
                 Notebook notebook6 = new Notebook("XiomiRedmiBook", 16, 2048, "AMD","Windows 11",  17, 70000);

                 Set<Notebook> unicNotebook = new HashSet<Notebook>();// создаем коллекцию из объектов Notebook
                 unicNotebook.add(notebook1); // добавляем ноутбуки в коллекцию unicNotebook
                 unicNotebook.add(notebook2);
                 unicNotebook.add(notebook3);
                 unicNotebook.add(notebook4);
                 unicNotebook.add(notebook5);
                 unicNotebook.add(notebook6);
                 return unicNotebook;
             }
         }



