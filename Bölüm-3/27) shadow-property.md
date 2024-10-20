# Shadow Property 
<p>
Entity sınıflarında fiziksel olarak tanımlanmayan / modellenmeyen ancak EF Core tarafından ilgili entity için var olan ya da var olduğu kabul edilen property'lerdir.
</p>
 
<p>
Genellikle tabloda gösterilmesini istemediğimiz / lüzumlu görmediğimiz / entity instance'ı üzerinde işlem yapmayacağımız kolonlar için shadow property'ler kullanılabilir.
</p>

<p>
Shadow property'lerin değerleri ve state'leri Change Tracker tarafından kontrol edilir. Yani biz her ne kadar entity instance'ları üzerinde ilgili shadow property'i, bir property ile temsil etmiyor olsak dahi esasında bunun üzerinde yapılan değişiklikler, bunun state'i change tracker tarafından yine de takip ediliyor olacaktır. 
</p>

<p>
Peki biz bu shadow property'i nerelerde kullanıyoruz? Aslında şu ana kadar farkında olmasak da shadow property'i foreign key'lerde kullanıyoruz.
</p>

<br>

## Foreign Key - Shadow Properties

<p>
İlişkisel senaryolarda foreign key property'sini manuel olarak entity içerisinde tanımlamadığımız durumlarda EF Core tarafından bu property dependent entity'e eklenmektedir. İşte bu durumda foreign key property'si, shadow property özelliğini taşımış olacaktır. j 
</p>

<br>

## Shadow Property Oluşturma 
<p>
Bir entity üzerinde shadow property oluşturmak istiyorsak aşağıdaki gibi Fluent Api kullanmamız gerekmektedir.
</p>

<img src="../img/shadow-property.png">

<br>

<p>
Generic olan Property metoduna bu shadow property'sinin hangi tipte olacağını belirtmiş oluyoruz. Peki biz bu shadow property'e nasıl erişeceğiz?
</p>

<br>

## Shadow Property'e Erişim Sağlama

### ChangeTracker İle Erişim

<p>
Change Tracker sayesinde aşağıdaki gibi CreatedDate kolonunun değerine erişebiliriz.
</p>

<img src="../img/shadow-property-1.png">

<br>

### EF.Property İle Erişim

<p>
Özellikle LINQ sorgularında shadow property'lerine erişim için EF.Property static yapılanmasını aşağıdaki gibi kullanabiliriz.
</p>

<img src="../img/shadow-property-2.png">







