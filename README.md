# C# Müsahibə sualları (Interview Questions by Ilkin Rufullayev)

## 1) C# nədir ? ##
> C# Microsoft tərəfindən 2001-ci ildə yaradılan obyekt yönümlü proqramlaşdırma dilidir. C# proqramlaşdırma dili C və C++ dillərinin üstün tərəflərini alaraq 
> yaradılıb. Hazırda .Net platformunda ən çox istifadə edilən proqramlaşdırma dilidir. C# ilə web proqramlaşdırma,oyun proqramlaşdırma,masaüstü proqramlar 
> yazmaq və hətta mobile proqramlaşdırma da mümkündür.

## 2) Sinif (class) nədir? ##
> Siniflər dəyişənlərı,metodları,propertiləri yığdığımız bir yerdir. Bu metodlari,dəyişənləri istifadə etmək üçün isə həmin sinifdən obyekt yaradılmalıdır.
> Sinifə bir nümunə olaraq İnsanı göstərə bilərik.
> İnsandakı xüsusiyyətlər məs. göz rəngi,adı,yaşı dəyişənlərimiz,onun danışması,gülməsi,qaçması kimi feili hərəkətləri isə metodlarımız olsun.
> Hər insan bu xüsusiyyətlərə fərd olaraq sahibdir. Proqramlaşdırmada da siniflərdə yazdığımız xüsusiyyətlər, metodlar obyektlərə aid edilir.Obyektlər bizim
> fərdlərimizdir.
```
class Person{
  public string eyeColor;
  public string name;
  public int age;
  
  void Talk(){
    //codes
  }
  
  void Laugh(){
    //codes
  }
}
```

## 3) Obyekt (object) nədir? ##
> Obyekt bir sinifdən yaradılan və yaddaşda yer tutan bir verilən strukturudur. Obyekt sinifin nümunəsidir,sinifin içərisində tanımlanılan metodlara,
> dəyişənlərə və s. obyektlər vasitəsilə çatmaq mümkündür.Obyektlər siniflərdə yazdığımız xüsusiyyətlərə,metodlara sahib olur. 
> Sinifdən bir obyekt yaratmaq üçün `new` açar sözündən istifadə edilir.
> Məsələn aşağıdakı nümunədə `Person` sinifə məxsus `age` dəyişəni `obj` obyekti vasitəsi ilə çağırılıb və 5 dəyəri mənimsədilib.

  ```
    Person obj = new Person();
    obj.age = 5;
  ```
  

## 4) C# propertilər nədir? ##
> C#-da propertilər dəyişənlərə çox bənzəyir lakin adi dəyişənlərdən fərqli olaraq get və set bloklarına malikdir. 
> Bu bloklar dəyərin oxunması və mənimsədilməsi zamanı çalışır.
> Məsələn , propertiyə dəyər mənimsədərkən set blokları çalışır , set blokları vasitəsi ilə mənimsədilən dəyər üzərində müəyyən əməliyyatlar icra etdikdən
> sonra dəyəri get bloklarına ötürüb ekrana çap edə bilərik.

```
  class Test{
    private int number;
    public int Number {get{ return number; } set{ number = value;} } //value menimsetdiyimiz deyeri (12) temsil edir
  }
  
  static void Main(string[] args){
    Test test = new Test();
    test.Number = 12; // Set blokları çalışdı
    Console.WriteLine(test.Number); // Get blokları çalışdı
  }
  
```

## 5) OOP prinsipləri hansılardır? ##
> Obyekt yönümlü proqramlaşdırmada 4 əsas prinsip mövcuddur.

* Encapsulation (Kapsullama)
* Inheritance (Mirasalma)
* Abstraction (Mücərrədlik)
* Polymorphism (Çox yönümlülük)

***Encapsulation (Kapsullama)*** <br>
Encapsulation siniflərdə yazdığımız dəyişənlərin əlçatılabilirliyini propertilər vasitəsilə məhdudlaşdırmaq və istifadəçilərin hər dəyişənə rahatlıqla çata
bilməsinə maneə olmaq məqsədi ilə istifadə edilir.
Məsələn, aşağıdakı nümunədə: 
```
 Person obj = new Person();
 obj.age = 5;
```
`age` dəyişəninə 5 dəyərini mənimsətdik. Burada hər şey normal görsənir,yaxşı bəs əgər 5 deyil -5 mənimsətsəydik?
Texniki baxımdan bunu etməyimiz heç bir xəta səbəbi olmayacaqdı,çünki `age` dəyişənimizin tipi `int`-dir və `int` mənfi dəyərlər ala bilir.
Amma insanın yaşı mənfi ola bilməz. Belə halların qarşısını almaq üçün `age` dəyişənini kapsullayaq.

```
class Person{
    private int age;
    public int Age 
    {
      get{ return  age; } 
      set
      {
        if(value > 0)
          age = value;
      }
   } 
}
```
Bildiyimiz kimi propertilerdeki set bloku dəyər mənimsədən zaman işə düşür,biz də həmin dəyərin 0-dan böyük olduğu vəziyyəti yoxlayıb neticeni ona görə qaytardıq,artıq bu halda istifadəçi `age` dəyişəninə mənfi dəyərlər mənimsədə bilməz (əks halda 0 nəticəsi alacağıq).

***Inheritance (Mirasalma)*** <br>
Bizim siniflərimiz sayca çox olacaq.Bənzər xüsusiyyətlərə sahib siniflərin içərisində eyni kodu təkrar-təkrar yazmaq yerinə həmin kodları üst sinifdən (Base class) miras almaq daha əlverişli olacaq.
Məsələn,
```
class Employee{
  public string eyeColor;
  public string name;
  public int age;
}

class Manager{
  public string eyeColor;
  public string name;
  public int age;
}


```
şəklində `Employee` və `Manager` sinifləri üçün dəyişənləri bu şəkildə yaratmağımızda heç bir problem yoxdur amma fikir verdinizsə eyni kodları yazdıq üstəlik bu xüsusiyyətlər işçi ya da menecer olmağından asılı olmayaraq hər bir insana aiddir. İndi isə bu kodları qısaldaq :
```
class Person{
  public string eyeColor;
  public string name;
  public int age;
}

class Employee:Person{
}

class Manager:Person{
}

```
daha əvvəl `Employee` və `Manager` siniflərində yazdığımız eyni kodların hər insana məxsus olduğunu demişdik,indi o dəyişənləri `Person` adında bir sinifə yazıb yuxarıdakı qayda ilə həm `Employee` həm də `Manager` siniflərində istifadə edə bilərik. Beləliklə, `Employee` və `Manager` sinifləri `Person` sinifindən onun xüsusiyyətlərini miras almış oldu.

Onu da unutmayaq ki,alt siniflər (nümunədə `Employee` və `Manager`) yalnız bir __sinifdən__ miras ala bilər.

***Abstraction (Mücərrədlik)*** <br>
Abstract siniflər üst sinif (Base class) olaraq istifadə edilən mücərrəd siniflərdir. Abstract siniflərin bəzi xüsusiyyətlərinə baxaq.

* Üst sinifdə var olan metod və propertilərin alt siniflərə görə müxtəlif cür işlədiyi vəziyyətlərdə istifadə olunur.
* Bu siniflərdə _abstract_ açar sözü ilə işarələnən metodlar və propertilər onu miras alan alt siniflər tərəfindən mütləq implement olunmalıdır!
* Abstract metodlar və propertilər abstract siniflərdə yazılmalıdır.
* Abstract metodlar və propertilər private ola bilməz!
* Abstract metodlar yazıldığı üst siniflərdə yalnız imza hissəsi ilə qeyd olunur. Onların tam hissəsi implement olunduqları alt siniflərdə yazılır. 
* Abstract siniflərdə abstract olmayan metodlar da yazıla bilər.
* Abstract siniflərdən obyekt yaradıla bilməz!

Nümunə:
```
abstract class Car{
  public abstract void Start();
}

class Audi:Car{
 public override void Go()
 {
    throw new NotImplementedException();
 }
}

```
Baxmayaraq ki , abstract siniflərdən obyekt yaranmır amma onlar obyekt yaradarkən referans olaraq istifadə edilə bilir.
```
Car audi = new Audi();
```

***Polymorphism (Çox yönümlülük)*** <br>
Üst sinifin referans , onun alt siniflərinin isə obyekt olaraq yaradıldığı vəziyyətdir.

Məsələn:
```
  Animal a1 = new Bird();
```
bu nümunədə `Animal` sinifini üst sinif olaraq `Bird` sinifini isə onun alt sinifi olaraq düşünsək, yuxarıdakı kimi obyekt yaratmaq mümkündür.
Amma bunun tərsi mümkün deyil, eyni ilə hər quşun heyvan olması,amma hər heyvanın quş olmaması kimi.
```
Bird a1 = new Animal(); //error
```
nümunələri artırmaq olar:
```
Animal a2 = new Tiger();
Animal a3 = new Cat();
```
Burada üst sinif olan `Animal` hər obyektə görə müxtəlif davranış göstərir yəni çox yönümlü olur. 

## 6) C#-da hansı növ siniflər (class) mövcuddur? ##
> C#-da aşağıdakı növdə siniflər (class) mövcuddur:
* Abstract class
* Static class
* Sealed class
* Partial class

(Hər biri haqqında ətraflı məlumat verilib)

## 7) Abstract classlar və interfacelər arasındakı fərqlər nələrdir? ##

Abstract class| Interface
------------- | -------------
Constructoru olur  | Constructoru olmur
Static dəyərlər ala bilər | Static dəyərlər ala bilməz
Abstract classlardakı elementlər bütün access modifierslərlə işlənə bilər (abstract metodlar private ola bilmaz) | Access modifiersi yalnız public ola bilər
Bir sinif yalnız bir abstract classı miras ala bilər | Bir sinif birdən çox interfeysi miras ala bilər
Bir çox sinif eyni tipdən və ortaq davranış göstərirsə abstract sinif base class olaraq istifadə edilər | Bir çox sinif yalnız ortaq metodlar istifadə edirsə interfeys istifadə etmək lazımdır
Abstract classlar metod,properti,fields,consts və s. elementlər ala bilir | Interfeyslər yalnız metodlarla işlənir
Abstract classdan miras alan alt siniflər yalnızca bu sinifdəki abstract açar sözlü metodları implement etmelidir | Interfeysdən miras alan siniflər interfeysin bütün metodlarını implement etmelidir

## 8) Virtual metodlar nədir? ##
> Bir metodun ``virtual`` açar sözü ilə işarələnməsi o metodun alt siniflərdə dəyişdirilib fərqli davranış göstərə biləcəyi mənasına gəlir.

```
 public class Car
 {
    public virtual void Start()
    {
        Console.WriteLine("Car started");
    }
 }

 public class Audi : Car
 {
    public override void Start()
    {
        Console.WriteLine("Audi started");
    }
 }
```
> Yuxarıdakı nümunədə base classda olan `Start` metodu onun alt sinifində fərqli şəkildə davranış göstərdi, bunun üçün `override` açar sözündən istifadə etmək lazımdır.
> Onu da unutmayaq ki, metodu `override` etmək kimi bir məcburiyyətimiz yoxdur,yəni `Start` metodunu `Audi` sinifində dəyişmək kimi bir məcburiyyətimiz yox idi.

## 9) Metodun override edilməsi nədir? ##
> Metodun override edilməsinə metodun əzilməsi də deyirlər, mənası da üst siniflərdə olan metodun alt siniflərdə dəyişdirilərək istifadə edilməsidir. 
> Unutmayaq ki,yalnız `virtual` açar sözü ilə işarələnmiş metodları əzə (dəyişdirə) bilərik.

## 10) Metodun overload edilməsi nədir? ##
> Bu sual metodun override edilməsi ilə qarışdırılmamalıdır. Override metodu əzmək idisə, overload metodun artıq yüklənməsidir.
> Yəni bir sinifdə var olan bir metodu həmin sinifdə eyni ad altında yenidən yarada bilərik amma necə?
> Bunun üçün bəzi şərtlər var təbii ki birəbir eyni imza ilə 2 eyni metodu yarada bilmərik.

```
class Math{
  public void Sum(int a,int b){
    //code
  }

  public void Sum(int a,int b){ //error 2 eyni imzaya sahib metod ola bilməz
    //code
  }
}
```
> O zaman nə edəcəyik,təbii ki, imzalarını dəyişdirəcəyik.
> Məsələn, birinci metod 2 parametr alıbsa 2-ci Sum metodu 3 parametr ala bilər yaxud ilk metodun parametrləri `int` tipində olub 2-ci metodun parametrləri `double` ola bilər. Bu hallarda eyni ad ilə xəta almadan metodlarımızı yarada bilərik,buna da metodun overload edilməsi deyilir.

```
class Math{
  void Sum(int a, int b)
  {
  //code
  }
  void Sum(int a, int b, int c)
  {
  //code
  }
}
```
yaxud
```
class Math{
  void Sum(double a, double b)
  {
  //code
  }
  void Sum(int a, int b)
  {
  //code
  }
}
```
> hətta geri dönüş tipini də dəyişərək etmək mümkündür
```
class Math{
  void Sum(double a, double b)
  {
  //code
  }
  int Sum(int a, int b)
  {
  //code
  }
}
```
## 11) Static metodlar nədir? ##
> Static metodlar obyekt ilə deyil birbaşa sinifin adı ilə müraciət edilən metodlardır. Bu metodlar çağırılan zaman obyekt yaradılmadığından constructor işə düşməyəcək.
> Static metodlar `static` açar sözü ilə yaradılır və yalnız static classlarda mövcud ola bilir.

```
public static class Math{
  public static int Sum(int num1,int num2){
    return num1+num2;
  }
}
```
> Çağırılan zaman aşağıdakı şəkildə sinifin adı ilə çağırılır.
```
Math.Sum(2,3);
```

## 12) Sealed classlar nədir? ##
> `Sealed` açar sözü ilə tanımlanmış classlar miras alma xüsusiyyətini bloklayır. Yəni bu şəkildə tanımladığımız classlardan artıq miras ala bilmərik.

```
public sealed class Car{
  //methods & properties
}

public class Audi:Car{ //error sealed classlardan miras almaq olmaz
}
```
## 13) Access modifierlar nədir və hansılardır? ##
> Access Modifier-lar kodda xarici müdaxilənin sərhədlərini müəyyən etmək üçün istifadə olunan əsas ifadələrdir. 
> C#-da aşağıdakı access modiferlar mövcuddur:
* Private — Bir dəyərin private olaraq tanımlanması , o dəyərin yalnız aid olduğu sinifdən əlçatılan olması mənasına gəlir.
* Public — Bir dəyərin public olaraq tanımlanması , o dəyərin istənilən yerdən əlçatılan olması deməkdir. Public-də məhdudiyyət yoxdur.
* Protected — Bir dəyərin protected olaraq tanımlanması , o dəyərin aid olduğu sinifdən və o sinifi miras alan alt siniflərdən əlçatılan olması deməkdir.
* Internal — Bir dəyərin internal olaraq tanımlanması , o dəyərin yalnız eyni proyektdən əlçatılan olması deməkdir.
* Protected Internal — Bir dəyərin protected internal olaraq tanımlanması , o dəyərin aid olduğu sinif , onun alt sinifləri və hətta onun digər proyektdəki alt sinifindən əlçatılan olması deməkdir.

## 14) Value type və referance type nədir və hansılardır? ##
> C#-da tiplər yaddaşda tutduğu yerə görə 2 yerə bölünür _value tiplər_ və _referance tiplər_.
> Value typelar yaddaşda stack adlanan hissədə tutulur. Value typelar aşağıdakılardır:
* int                                    
* double                   
* decimal                  
* float                      
* byte
* bool
* char
* struct
* enum
> Referans tiplər isə yaddaşın heap hissəsində saxlanılır, lakin onların stackda unikal adresləri olur,heapdakı referans tipə keçid məhz stack bölməsindəki unikal adresdən keçir. Referans typelar əsasən `new` açar sözü ilə yaradılan obyektlərdir.
* Object
* Class
* Interface
* string
* array (hər tipdən olan arraylar bura daxildir)
* List

![ValueVsRef](https://user-images.githubusercontent.com/96441243/218277073-5966810f-e6a1-46c6-9bd4-ac6a1056ec54.png)
> Şəkildən gördüyümüz kimi referans tiplərin adresləri stackda saxlanılır 

```
int num1;
int num2 = 12;

num1 = num2; // num1-in yeni dəyəri 12 olacaq
num2 = 19;  // num2-nin yeni dəyəri 19 olacaq amma num1-in dəyəri dəyişməyəcək,çünki o bir value typedır!
```

```
string[] cities = new string[]{"Bakı","Masallı","Sumqayıt"}; // array referans tipdir heapda saxlanılacaq,amma unikal adresi stackdadır

string[] cities2 = new string[]{"Gəncə","Lənkəran","Şamaxı"}; // başqa bir referans tipli obyekt

cities = cities2; // İki referansı tipi bir-birinə mənimsədən zaman onların stackdəki adreslərini eyni referansa yönəltmiş oluruq
```

![valref2](https://user-images.githubusercontent.com/96441243/218277772-2b0fb5c9-764a-49fc-8a9f-0ce0cadb8ae1.png)
> `cities = cities2` nəticəsi şəkildəki kimi olacaq , 2 adres də eyni referansa yönələcək. Nümunəyə davam edək..
```
cities[0] = "Naxçıvan";
```
> Bu zaman hər iki adres eyni referansı göstərdiyindən `cities[0]="Naxçıvan"` yazdıqdan sonra eyni dəyər `cities2` arrayında da dəyicək.
```
Console.WriteLine(cities2[0]); // Naxçıvan
```
> Bəs `cities` arrayının heapdakı referansına ({"Bakı","Masallı","Sumqayıt"}) nə olacaq ? Bu zaman Garbage Collector dediyimiz obyekt heapda adresi olmayan bütün referansları siləcək.

## 15) Garbage collector nədir? ##
> Obyekt yönümlü proqramlaşdırma dillərində mövcud olan Garbage Collectorun vəzifəsi heap bölməsində işini tamamlamış obyektlərin referanslarını təmizləməkdir.
> Bir sinifdən obyekt yaratdığımız zaman heap bölməsində onun üçün yer ayırılır,bu obyektin işi bitdikdən sonra Garbage Collector avtomatik olaraq həmin obyektin referansını heapdan təmizləyir.

> Garbage Collector yalnız heap bölməsində fəaliyyət göstərir!

> Garbage collectoru bizim işə salmağımıza ehtiyac yoxdur,o avtomatik olaraq işə düşür amma özümüz Garbage colelctoru çağırmaq istəsək bu qayda ilə çağıra bilərik.
```
GC.Collect();
```

## 16) Constructor metod nədir? ##
> Bir classdan obyekt yaradılarkən ilk işə düşən metodlardır. Constuctor public olmalı, class adı ilə eyni olmalıdır və constuctor metodların geri dönüş tipləri yoxdur.
```
MyClass myObj = new MyClass();  
```
> `new`-dən sonra `MyClass()` referansını çağırdıq və bildiyimiz kimi `()` mötərizə C# və Java kimi obyekt yönümlü dillərdə yalnız metodlarda istifadə olunur. Myclass-dan sonra gələn mötərizələr bəs hansı metodu aktivləşdirir? Məhz constructor metodları..
> Beləliklə, constuctor metodlar `new` açar sözü ilə obyket yaradılarkən ilk işə düşən metodlardır. 
> Obyekt yaradılarkən constructor metodlar mütləq işə düşür !
```
class MyClass{
  public MyClass(){
    // obyekt yaradılarken ilk bura çalışır
  }
}
```
> Hər classda biz yazmasaq da, default olaraq boş bir constuctor mövcuddur.
> Bir classda istənilən qədər constructor yaradıla bilər,parametr ala bilər və overload edilə bilər.
> ***Constructor metod private olarsa, həmin sinifdən obyekt yaratmaq mümkün olmayacaq,çünki obyekt yaradılarkən mütləq constuctor metod işə düşməlidir,amma access modifiersi private olarsa , constructor metoda kənardan əlçatmaq mümkün olmayacağından ötrü obyekt yarada bilməyəcəyik.***

## 17) Destructor metod nədir? ##
> Constructor metodun əksidir,bir classdan yaradılan obyekt yaddaşdan təmizlənərkən yaddaşdan silinmədən son dəfə çalışan metoddur.

> C# dilində destructor sadəcə classlarda mövcuddur və ***hər bir classın sadəcə 1 destructoru olur!***
> Destructor metod parametr ala bilməz buna görə də overload da edilə bilməz!
> Bir obyekt hansı şərtlərdə yox edilir (yaddaşdan silinir)?
* Əgər obyekt hər hansı bir referans tərəfindən işarələnmirsə.. (həmin obyektin stackdakı adresi artıq o referansı göstərmirsə)
* Obyektin yaradıldığı və istifadə edildiyi scope bitibsə.. (bu hal obyekt kənar bir scopeda istifadə edilməyibsə keçərlidir)
* Obyket bir daha əlçatılan deyilsə..
> Bu hallarda obyekt Garbage Collector tərəfindən yaddaşdan silinir,silinmədən öncə son bir dəfə destructor metod işə düşür.

> Destructor metodun tanımlanması:
```
class MyClass{

  ~MyClass(){
    // obyekt imha edilərkən son dəfə çalışacaq kodlar  
  }
}
```
> C# classlarında biz yaratmadığımız təqdirdə default olaraq destructor mövcud olmur!

## 18) C#-da Dispose və Finalize metodları arasındakı fərq nədir? ##
> Hər iki metod yaddaşda istifadə edilməyən obyekti sərbəst buraxmaq üçün istifadə olunur. Yəni artıq istifadə olunmayan obyektləri silir.

> Amma aralarında bəzi fərqlər mövcuddur:
* Hər ikisi yaddaşdakı obyekti təmizləmək üçün istifadə edilir ancaq:
  * Dispose metodu yaddaşdakı obyekti təmizləmək üçün _manuel_ olaraq istifadə edilir. 
  * Finalize metodu isə yaddaşdakı obyekti təmizləmək üçün  _Garbage Collector_ tərəfindən istifadə edilir.
* Dispose metodu manuel olaraq istifadə edildiyindən Garbage Collectora görə daha performanslı çalışır.
* Digər tərəfdən Finalize metodu Garbage Collector tərəfindən çağırılırdığından performans baxımından yavaşdır.
* Garbage collectorun nə zaman çalışacağı naməlumdur, bu da təhlükəsizlik baxımından risklidir.
> Bu səbəblərdən C# -da Dispose metodunu istifadə etməyimiz tövsiyə edilir.


## 19) C#-da using açar sözü nə üçün istifadə olunur? ##
> C#-da using açar sözü 2 məqamda istifadə olunur.
* Başqa bir namespace-də yazılmış class və metodları import etmək üçün:
* Dispose metodunu manuel yazmaq yerine avtomatik olaraq çağırmaq üçün:
> Birinci nümunədə `Models` folderi altında olan `Context` sinifini cari sinifində istifadə etmək istəyiriksə,həmin `Context` sinifini burada import edirik.
```
using Models;
Context con = new Context();
```
> Ikinci nümunədə isə biz Dispose metodunun manuel olaraq çağırıldığını qeyd etmişdik..
```
MyClass myObj = new MyObj();
((IDisposable)myObj).Dispose();
```
> Hər obyekt yaratdıqdan sonra Dispose metodunu bu cür manuel olaraq çağırmaq yerinə `using` açar sözündən istifadə edə bilərik
```
using (FileStream stream = File.OpenRead("e"))
{
  //kodlar
}
```
> Daha qısa yazsaq..
```
using FileStream stream = File.OpenRead("e");
```
> `using` açar sözündən istifadə edərək manuel olaraq Dispose sinifini çağırmağa ehtiyac yoxdur

> ***`using` açar sözü ancaq və ancaq `IDisposable` interfeysindən implement alan siniflərlə istifadə edilə bilir!***

## 20) Namespace nədir? ##
> C# -da namespacelar classların sərhədləridir/adresləridir əgər həmin classı başqa sərhəd daxilində istifadə etsək,adresini `using` açar sözü vasitəsilə bəyan etməliyik.
```
using Models.Entities;

Product prod = new();
```
> Bu nümunədə /Models/Entities adresindəki/namespaceindəki sinifləri import etdik və artıq cari sinifdə istifadə edə bilərik.

## 21) Managed və Unmanaged kod nədir?  ##
> Managed kod .Net framework içərisindəki CLR(Common Language Runtime) tərəfindən idarə olunan koddur.
> Managed code C# kimi .Net dəstəkli dillər tərəfindən yazılır ve Intermediate Language (IL) olaraq compile edilir,daha sonra CLR tərəfindən idarə olunur.
> CLR yaddaşın idarəsi, xəta idarəsi (exception handling) və digər sistem səviyyəli xidmətləri bu kodlarda (managed) üzərinə götürür.

> Unmanaged code isə .Net frameworkdən və CLR nəzarətindən kənar kodlardır,hansı ki bu kodlar .Net dəstəkli dillərdən birində yazılmayıb,bu cür kodlar birbaşa əməliyyat sistemi tərəfindən compile edilir. Bu kodlar CLR-ın nezaretinden kənar olduğundan belə kodlarda xəta idarəsi,yaddaşın idarəsi və s. xidmətlər proqramçı tərəfindən manuel olaraq həyata keçirilməlidir.

## 22) C#-da class və struct arasındakı fərqlər nələrdir? ##
> C#-da həm siniflər, həm də structlar fərdi data tiplərini müəyyən etmək üçün istifadə olunur, lakin onların bəzi əsas fərqləri var.

Class  | Struct
------------- | -------------
Class referance typedır və Heapda saxlanılır  | Structlar isə value typedır və Stackdə saxlanılır
Classlar inheritance və polymorphismi dəstəkləyir  | Structlar isə inheritance və polymorphismi dəstəkləmir
Classlar Abstract olaraq tanımlana bilərlər | Structlar abstract ola bilməz
Classların bütün üzvləri default olaraq private olur | Structlarda isə üzvlər default olaraq public olur
Classlar referance type olduğundan yaddaş idarəsində Garbage Collectordan istifadə edə bilir | Structlar value type olduğundan Garbage Collectordan istifadə edə bilmir
Classlar böyük və mürəkkəb modellər üçün daha uyğundur | Structlar isə kiçik həcmli modellər üçün uyğundur.

## 23) Enum nədir? ##
> Proqram içində istifadə edilən sabitlərə mənalı adlar verilməsi məqsədilə bu sabitləri bir qrup altında toplaya bilərik. Bu cür qruplara enum (enumeration) deyilir.
> Enumlar value typedır ,buna görə də yaddaşın stack bölməsində saxlanılır. Enumun istifadəsinə aid bir nümunə aşağıdakı kimidir:
```
public enum DaysOfWeek
{
    Monday,
    Tuesday,
    Wednesday,
    Thursday,
    Friday,
    Saturday,
    Sunday
}
```
> Enumlarda ilk deyer default olaraq 0-dan başlayır, amma bunu dəyişmək mümkündür.
```
public enum DaysOfWeek
{
    Monday = 1,
    Tuesday,
    Wednesday,
    Thursday,
    Friday,
    Saturday,
    Sunday
}
```
> Çağırarkən isə bu cür çağırılacaq:
```
DaysOfWeek day = DaysOfWeek.Monday;
```
## 24) C# -da boxing və unboxing nədir? ##
> Boxing - bir value tipin referans tipə çevirilməsi, unboxing isə referans tipin value tipə çevirilməsidir.

**Boxing**
* Value tip (int,float,char və s.) dəyişənin referans tipə (object) çevirilməsidir.
```
int num = 10;
Object obj = num; // boxing
```
> Üstdəki kod nəticəsində `num` dəyişəni value tip olduğundan stackda saxlanılacaq, `obj` dəyişəni isə referans tip olduğundan heap bölməsində tutulacaq.

**Unboxing**
* Referans tip dəyişənin value tipə çevirilməsidir.
```
Object obj = 41;
int i = (int)obj; // unboxing zamanı xeta ilə qarşılaşsaq casting istifade edeceyik
```

## 25) C# -da partial classlar hansılardır? ##
> Siniflərin həddindən artıq böyüdüyü hallarda həmin sinifi bölüb idarə etməkdir.
> Partial classlar bizə bir sinifi birdən çox sinifə bölməyimizə, constructor , metod, dəyişən , properti və s. səliqəli şəkildə ayırmağımıza imkan verir.Fiziki olaraq birdən çox parçaya bölünmüş siniflər çalışma zamanında tək bir sinif kimi hərəkət edir.

```
public partial class Car
{
    public Car()
    {
       //codes
    }
}

public partial class Car
{
    public string Name { get; set; }
    public string Color { get; set; }
}

public partial class Car
{
    void Start()
    {
        //codes
    }
}
```
> Yuxarıdakı nümunədə `Car` sinifini 3 yerə bölüb constructor,properti və metodlara görə ayırdıq. Buna baxmayaraq `Car` sinifi vahid bir sinif kimi davranır.
> Fərqli partial classlarda eyni adlı metod yaxud dəyişən yarada bilmərik eynilə normal siniflərdə olduğu kimi. Unutmayaq partial classlar normal classlar kimi davranır,normal classlarda edilən hər əməliyyat burada da edilə bilər.


















