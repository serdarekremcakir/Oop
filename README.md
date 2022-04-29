# Nesne Yönelimli Programlama (OOP)
Nesne yönelimli programlama sınıflar ve nesneler kavramına dayanan bir programlama yaklaşımıdır. Bu yaklaşımın amacı ihtiyaç duyulan programı daha küçük parçalara bölerek, yönetilebilir ve yeniden kullanılabilir hale getirmektir. Her küçük parçanın kendine ait özelliği, verileri ve diğer küçük parçalarla nasıl iletişim kuracağı bilgileri bulunur.

Nesne Yönelimli Programlama:
* Don’t Repeat Youself ilkesini uygular ve kodun bakımını, düzenlemesini ve hata ayıklamasını kolaylaştırır.
* Daha az kod ve daha kısa geliştirme süresiyle, yeniden kullanılabilir uygulamalar oluşturmayı mümkün kılar.
* Yapılara daha sonradan yeni özellikler ekleyerek genişletilebilirlik sağlar.

## Nesne (Object)
Tdk tanımı: Belli bir ağırlığı ve hacmi, rengi olan her türlü cansız varlık, şey , obje.

Nesnenin kendine ait nitelikleri ve davranışları vardır. Nesneler birbirlerinden farklıdır ve kendi varoluşlarına göre davranırlar, kendi kimliklerine sahiptirler.

Nitelik: Bir nesnenin özellikleridir. Nesnenin mevcut durumunu tanımlar.

Davranış: Bir nesnenin kendine özel yaptığı eylemlerdir.

## Sınıf (Class)

Sınıflar bir problemi soyutlamak ve genelleştirmek için kullanılan yapılardır veya şablonlardır.

Sınıflar bir nesneye ait tüm özellikleri temsil eder. Bu özellikler nesnenin ne tür nitelikleri ve davranışları olacağını belirler.

Sınıflar nesne yönelimli programlamanın en önemli öğesidir. 

````
class SinifAdi
{
    [Erişim Belirleyici][Veri Tipi] ÖzellikAdı;
    [Erişim Belirleyici][Geri Dönüş Değerinin Tipi] MetotAdi([Parametreler])
    {
        //Metot Gövdesi
    }
}
````

Sınıf içerisinde tanımlanan değişkenlere field denir.

````
class MyClass
{
  // Class members
  string color = "red";        // field
  int maxSpeed = 200;          // field
  public void fullThrottle()   // method
  {
    Console.WriteLine("The car is going as fast as it can!");
  }
}
````

## Constructor (Yapıcı)

Bir sınıftan bir nesne oluşturulduğunda biz tanımlamasak bile arka planda çalışan varsayılan yapıcı metotlara constructor denir. Sınıf nesnesi ilk oluşturulduğunda yapılması istenen işler kurucu metotlar içerisinde yapılır.

Constructor tanımlarken:

* Yapıcı Metotların isimleri sınıf isimleri ile aynı olmalıdır.
* Public olarak bildirilmeleri gerekir.
* Geri dönüş değeri yoktur.

````
class Car
{
  public string model;
  public string color;
  public int year;

  // Create a class constructor with multiple parameters
  public Car(string modelName, string modelColor, int modelYear)
  {
    model = modelName;
    color = modelColor;
    year = modelYear;
  }

  static void Main(string[] args)
  {
    Car Ford = new Car("Mustang", "Red", 1969);
    Console.WriteLine(Ford.color + " " + Ford.year + " " + Ford.model);
  }
}


// Outputs Red 1969 Mustang
`````

## Erişim Belirleyiciler (Access Modifiers)

Bir sınıfa ait nitelik ve davranışlara ulaşabilmek için erişim belirleyiciler kullanılır. Erişim belirleyiciler değişken, metot ve sınıfların önüne yazılır ve yazıldıkları konuların erişebilecekleri alanları belirler.

Public :  Her yerden erişilebilir.

Private: Sadece tanımlandığı sınıf içerisinden doğrudan erişilebilir.

Internal: Sadece tanımlandığı proje dosyası içinden erişilebilir.

Protected: Sadece tanımlandığı sınıfta veya o sınıftan miras alan diğer sınıflardan erişilebilir.

## Kapsülleme (Encapsulation)

Encapsulation yani kapsülleme ilkesi, bir sınıfa ait değişkenlerin veya niteliklerin ancak o sınıfa ait metotlar tarafından değiştirilebilmesi ve okunabilmesi ilkesidir. 

Kapsülleme sayesinde nesneler bilinçsiz olarak kullanımdan korunmuş olur. Fakat bazı durumlarda private field’lara erişmemiz ve özelliklerini değiştirmemiz gerekebilir. Bu durumda Property Kavramı devreye girer. 

Örneğin bir özellik tanımı yaptınız ve diğer sınıflar içerisinden sadece okumak için erişilsin istiyorsanız bunu kapsülleme yaparak sağlayabilirsiniz. Kapsülleme işlemini ise propertyleri kullanarak yapabilirsiniz.

Property bir field’in değerini geri döndürme(GET) ve yeni bir değer(SET) atamaya olanak sağlar.

````
class Person
{
  private string name; // field
  public string Name   // property
  {
    get { return name; }
    set { name = value; }
  }
}

class Program
{
  static void Main(string[] args)
  {
    Person myObj = new Person();
    myObj.Name = "Liam";
    Console.WriteLine(myObj.Name);
  }
}
````
## Static Sınıf

Bir sınıfın static olmayan üyelerine nesneler aracılığıyla erişirken static olan metotlara ve özelliklere ise nesne oluşturmadan o sınıfın ismi aracılığıyla erişiriz.

Static bir sınıfın bütün field ve methodları static olmak zorundadır.

Static sınıflara kalıtım uygulanamaz.

````
class Ogrenci
{
    public static int OgrenciSayisi = 0;
    public string Isim;
    public string Soyisim;
    public Ogrenci()
    {
        OgrenciSayisi++;
    }
}

class Program
{
    static void Main(string[] args)
    {
        //Static sınıf üyesine erişim
        Console.WriteLine("Öğrenci sayısı: {0}",Ogrenci.OgrenciSayisi);

        //Static olmayan sinif üyesine erişim
        Ogrenci ogrenci1 = new Ogrenci();
        ogrenci1.Isim = "Deniz";
        ogrenci1.Soyisim = "Arda";
        
        Ogrenci ogrenci2 = new Ogrenci();
        ogrenci2.Isim = "Ayşe";
        ogrenci2.Soyisim = "Yılmaz";

        Console.WriteLine("Öğrenci Sayısı: {0}", Ogrenci.OgrenciSayisi);
    }
}
````

## Yapı Kavramı (Struct)

Structlar sınıflara çok benzerler. Class kullanmayacak kadar kompleks olmayan yapılar tasarlamak için kullanılır.

* Classlar referans tipli özellikler gösterir, Yapılar ise değer tipli özellikler gösterir.
* Diğer struct ya da sınıflardan kalıtım almazlar
* Interfacelerden kalıtım alabilirler.
* New anahtar sözcüğü ile nesneleri yaratılabilir.
* Sınıflar gibi metot, property ve fieldlardan oluşurlar.
* Static üye barındırabilirler.
* Structların kurucu methodları parametre vermeden tanımlanamaz.

````
struct Ogrenci {
    public string Isim;
    public string Soyisim {get;set;}
    public static int OgrenciSayısı=0;
}
````

## Enum
“enum” anahtar kelimesi enumeration yani numaralandırma kelimesinden gelir. Sayısal verileri string ifadelerle saklamanızı sağlar.  Enumlar default olarak 0’dan başlar.

````
enum Months
{
  January,    // 0
  February,   // 1
  March,      // 2
  April,      // 3
  May,        // 4
  June,       // 5
  July        // 6
}

static void Main(string[] args)
{
  int myNum = (int) Months.April;
  Console.WriteLine(myNum);
}
````

## Kalıtım (Inheritance)

Bir sınıfın başka bir üst sınıftan miras almasına kalıtım denir. Bir sınıfın başka bir sınıftan kalıtım yapması demek, kalıtımı yapan sınıfın diğer sınıftaki nitelik ve davranışlarını kendisine alması demektir. 

Kalıtım yapan sınıfa alt sınıf, kalıtım veren sınıfa ata sınıf denir.

````
class Vehicle  // base class (parent) 
{
  public string brand = "Ford";  // Vehicle field
  public void honk()             // Vehicle method 
  {                    
    Console.WriteLine("Tuut, tuut!");
  }
}

class Car : Vehicle  // derived class (child)
{
  public string modelName = "Mustang";  // Car field
}

class Program
{
  static void Main(string[] args)
  {
    // Create a myCar object
    Car myCar = new Car();

    // Call the honk() method (From the Vehicle class) on the myCar object
    myCar.honk();

    // Display the value of the brand field (from the Vehicle class) and the value of the modelName from the Car class
    Console.WriteLine(myCar.brand + " " + myCar.modelName);
  }
}
````

Bir sınıfın başka sınıflara kalıtım vermesi engellenmek istendiğinde **sealed** anahtar kelimesi kullanılır.

````
sealed class Vehicle 
{
  ...
}

class Car : Vehicle 
{
  ...
}

//'Car': cannot derive from sealed type 'Vehicle'
````

## Çok Biçimlilik (Polymorphism)
Polymorphism metotları ve türetilmiş sınıfları yeniden tanımlama yeteneğidir.

Polymorphism, alt sınıfların ata sınıflardaki metotları geçersiz kılması (Method overriding) sayesinde çok biçimli olarak davranmasına denir. Bu sayede alt sınıf ata sınıfından gelen davranışı kendine göre şekillendirebilir.

Miras veren sınıf içerisindeki bir metotla, miras alan sınıf içerisindeki bir metotun aynı fakat gövdesinin farklı olduğunu varsayalım. Nesneler üretilip metotlar kullanıldığında miras veren sınıftaki metot çalışmaktadır.

 Miras veren sınıftaki metotun erişim belirleyicisinden sonra virtual kelimesi kullanılır ve miras alan sınıflardaki metotun erişim belirleyicinden sonra override kelimesi kullanılır. İstenen çıktılar elde edilir. (C#)

````
class Animal  // Base class (parent) 
{
  public virtual void animalSound() 
  {
    Console.WriteLine("The animal makes a sound");
  }
}

class Pig : Animal  // Derived class (child) 
{
  public override void animalSound() 
  {
    Console.WriteLine("The pig says: wee wee");
  }
}

class Dog : Animal  // Derived class (child) 
{
  public override void animalSound() 
  {
    Console.WriteLine("The dog says: bow wow");
  }
}

class Program 
{
  static void Main(string[] args) 
  {
    Animal myAnimal = new Animal();  // Create a Animal object
    Animal myPig = new Pig();  // Create a Pig object
    Animal myDog = new Dog();  // Create a Dog object

    myAnimal.animalSound();
    myPig.animalSound();
    myDog.animalSound();
  }
}

//The animal makes a sound
//The pig says: wee wee
//The dog says: bow wow
````

## Soyutlama (Abstraction)

Soyutlama, bir sınıfa veya metoda temel görevlerin tanımlanması, detayların ise tanımlanmaması demektir.

### Arayüz (Interface)

Interface, sınıfların içermesi gereken metotların imzalarının yer aldığı, özelliklerinin tanımlandığı bir taslaktır.

Interface içerisinde propertylere bir değer ataması yapılmaz, metotların ise gövdesi yazılmaz. Sadece implemente eden sınıfın ne iş yaptığının bir ara yüzüdür. Bir sınıf birden fazla interfaceden kalıtım alabilir.

````
interface Animal 
{
  void animalSound(); // interface method (does not have a body)
  void run(); // interface method (does not have a body)
}
````

### Soyut sınıf (Abstract Class)

Abstract anahtar kelimesi ile tanımlanan sınıflardır. Abstract sınıflar sadece kalıtım için kullanılan sınıflar gibi düşünülebilir. 


* Normal sınıflar gibi new() anahtar kelimesi ile türetilmez.
* Interfaceler gibi metot bildirimi yapabilir.
* Soyut veya soyut olmayan fonksiyonlar tanımlanabilir.
* Sanal metotları override eder gibi abstract metotlar da override edilebilir.
* Abstract metotların gövdesi yazılmaz.
* Bir abstract class bir abstract metot içeriyorsa, abstract sınıftan türeyen tüm sınıflar bu metodu override etmek zorundadır.
* Bir sınıf sadece tek abstract sınıftan kalıtım alabilir.

````
abstract class Animal
{
  // Abstract method (does not have a body)
  public abstract void animalSound();
  // Regular method
  public void sleep()
  {
    Console.WriteLine("Zzz");
  }
}

// Derived class (inherit from Animal)
class Pig : Animal
{
  public override void animalSound()
  {
    // The body of animalSound() is provided here
    Console.WriteLine("The pig says: wee wee");
  }
}

class Program
{
  static void Main(string[] args)
  {
    Pig myPig = new Pig(); // Create a Pig object
    myPig.animalSound();  // Call the abstract method
    myPig.sleep();  // Call the regular method
  }
}

//The pig says: wee wee
//Zzz
````

