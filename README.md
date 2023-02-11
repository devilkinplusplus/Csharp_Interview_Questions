# C# Müsahibə sualları

1) **C# nədir ?**
> C# Microsoft tərəfindən 2001-ci ildə yaradılan obyekt yönümlü proqramlaşdırma dilidir. C# proqramlaşdırma dili C və C++ dillərinin üstün tərəflərini alaraq 
> yaradılıb. Hazırda .Net platformunda ən çox istifadə edilən proqramlaşdırma dilidir. C# ilə web proqramlaşdırma,oyun proqramlaşdırma,masaüstü proqramlar 
> yazmaq və hətta mobile proqramlaşdırma da mümkündür.

2) **Sinif (class) nədir?**
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

3) **Obyekt (object) nədir?**
> Obyekt bir sinifdən yaradılan və yaddaşda yer tutan bir verilən strukturudur. Obyekt sinifin nümunəsidir,sinifin içərisində tanımlanılan metodlara,
> dəyişənlərə və s. obyektlər vasitəsilə çatmaq mümkündür.Obyektlər siniflərdə yazdığımız xüsusiyyətlərə,metodlara sahib olur. 
> Sinifdən bir obyekt yaratmaq üçün `new` açar sözündən istifadə edilir.
> Məsələn aşağıdakı nümunədə `Person` sinifə məxsus `age` dəyişəni `obj` obyekti vasitəsi ilə çağırılıb və 5 dəyəri mənimsədilib.

  ```
    Person obj = new Person();
    obj.age = 5;
  ```
  

4) **C# propertilər nədir?**
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

5) **OOP prinsipləri hansılardır?**
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
Bildiyimiz kimi propertilerdeki set bloku dəyər mənimsədən zaman işə düşür,biz də həmin dəyərin 0-dan böyük olduğu vəziyyəti yoxlayıb neticeni ona görə qaytardıq,artıq bu halda istifadəçi `age` dəyişəninə mənfi dəyərlər mənimsədə bilməz (əks halda 0 nəticəsini qaytaracaqdır).

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









