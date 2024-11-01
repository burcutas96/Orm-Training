# Özelleştirici Entity Konfigürasyonları - 1

## EF Core'da Neden Yapılandırmalara İhtiyacımız Olur?
<p>
Yeri geldiğinde default davranışları geçersiz kılmak ve özelleştirmek isteyebiliriz. Bundan dolayı yapılandırmalara ihtiyacımız olacaktır.
</p>

<br>

## OnModelCreating() Metodu
<p>
EF Core'da yapılandırma deyince akla ilk gelen metot OnModelCreating() metodudur. Bu metot DbContext sınıfı içerisinde virtual olarak ayarlanmı bir metottur.
</p>

<p>
Bizler bu metodu kullanarak model'larımızla ilgili temel konfigürasyonel davranışları (Fluent Api) sergileyebiliriz.
</p>

<p>
Bir model'ın yaratılışıyla ilgili tüm konfigürasyonları burada gerçekleştirebilmekteyiz.
</p>

<br>

## GetEntityTypes() Metodu
<p>
Ef Core'da kullanılan entity'leri elde etmek, programatik olarak öğrenmek istiyorsak bu fonksiyonu kullanabiliriz.
</p>


<img src="../img/getEntityTypes.png" width="60%">

<br>

## Configurations | Data Annotations & Fluent API

### Table - ToTable
<p>
Generate edilecek tablonun ismini belirlememizi sağlayan yapılandırmadır. Normalde yani default olarak bir entity'e karşılık gelen table'ı veri tabanına migrate ederken tablonun ismi DbContext sınıfındaki DbSet property'sinden alınır. Ama biz bu davranışı ezmek istiyorsak, başka bir isim verilmesini istiyorsak o zaman Table attribute'unu ya da ToTable() metodunu kullanabiliriz.
</p>

<img src="../img/table-attribute.png" width="60%">

<br>

<img src="../img/table-fluent-api.png" width="60%">

<br>

<p>
Peki biz hem attribute hem de fluent api kullanırsak ef core'da hangisi daha önceliklidir? Her daim fleunt api son karardır. Yani fluent api en baskınıdır. Biz bütün konfigürasyonları uygulayabiliriz ama fluent api varsa ef core en son onu baz alacaktır.
</p>

<br>

### Column - HasColumnName, HasColumnType, HasColumnOrder
<p>
Ef Core'da tabloların kolonları entity sınıfları içerisindeki property'lere karşılık gelmektedir. Ve default olarak property'lerin adı kolon adıyken, türleri / tipleri ise kolon türleridir.
</p>

<p>
Eğer ki bu durumu değiştirmek istiyorsak alt başlıkta da yazılan yapılandırmaları kullanabiliriz.
</p> 

<img src="../img/column-attribute.png" width="60%">

<br>

<img src="../img/column-fluent-api.png" width="60%">

<br>

### ForeignKey - HasForeignKey
<p>
Foreign key, ilişkisel tablolarda dependent entity'nin principal entity'e karşı olan ilişkisel verisini tutan kolondur. Ve dependent entity'de tutuluyordu.
</p>

<p>
Ef Core'da foreign key kolonu genellikle entity tanımlama kuralları gereği default yapılanmalarla oluşturulur. Ama biz bu kuralların dışında farklı bir isimle foreign key tanımlamak istiyorsak o zaman bu yapılandırmalara ihtiyaç duyarız. 
</p>

<p>
Örneğin aşağıdaki çalışmada 'ahmet' kolonunu ForeignKey attribute'u ile foreign key olmasını sağladık.
</p>

<img src="../img/foreign-key-data-annotations.png" width="60%">

<br>

<p>
Eğer ki foreign key tanımlamasını fluent api ile sağlayacaksak ilgili iki entity arasındaki ilişkiyide modellememiz gerekmektedir. Aksi taktirde HasForeignKey fonksiyonunu kullanamayız.
</p>

<img src="../img/foreign-key-fluent-api.png" width="60%">

<br>

### NotMapped - Ignore
<p>
Ef Core, default olarak entity sınıfları içerisindeki tüm property'leri modellenen tabloya kolon şeklinde ekler. Ama bazen bizler entity sınıfları içerisinde tabloda bir kolona karşılık gelmeyen property'ler tanımlamak mecburiyetinde kalabiliriz.  
</p>

<p>
Bu property'lerin ef core tarafından kolon olarak tabloya eklenmesini istemediğimizi bildirebilmek için de NotMapped ya da Ignore fonksiyonlarını kullanabiliriz.
</p>

<img src="../img/notmapped.png" width="60%">

<br>

<img src="../img/ignore.png" width="60%">

<br>

### Key - HasKey
<p>
Ef Core'da default convension olarak bir entity'nin içerisindeki Id, ID, EntityId, EntityID vs şeklinde tanımlanan tüm property'lere varsayılan olarak primary key constraint uygulanır.
</p>

<p>
Key yada HasKey yapılanmalarıyla istediğimiz herhangi bir property'e, default convension dışında primary key uygulayabiliriz.
</p>

<p>
Ef Core'da br entity içerisinde kesinlikle primary key'i temsil edecek bir property bulunmalıdır. Aksi taktirde Ef core migration oluştururken hata verecektir.
</p>

<p>
Eğer tablonun primary key kolonu olmayacaksa bunun belirtilmesi gerekir.
</p>
 
<img src="../img/primary-key-1.png" width="60%">

<br>

<img src="../img/primary-key-2.png" width="60%">

<br>

### Timestamp - IsRowVersion
<p>
Sonraki konularda Ef core'da veri tutarlığını görücez. Bu derste bir satırdaki verinin bütünsel olarak değişikliğini takip etmemizi sağlayacak olan versiyon mantığını konuşuyor olucaz.
</p>

<p>
İşte bir verinin versiyonunu bu konfigürasyonlarla oluşturuyoruz.
</p>

<img src="../img/timestamp.png" width="60%">

<br>

<img src="../img/isrowversion.png" width="60%">

<br>

### Required - IsRequired
<p>
Bir kolonun nullable olup olmamasını bu konfigürasyonla belirleyebiliriz. Ef Core'da bir property default olarak not null şeklinde tanımlanır. Eğer ki property'i nullable yapmak istiyorsak tür üzerinde ?(nullable) operatörü ile bildirimde bulunmamız gerekmektedir.  
</p>

<img src="../img/required-data-annotations.png" width="60%">

<br>

<img src="../img/required-fluent-api.png" width="60%">

<br>

### MaxLength - StringLength - HasMaxLength
<p>
Bir kolonun maksimum karakter sayısını belirlememizi sağlar.
</p>

<img src="../img/max-length-data-annotations.png" width="60%">

<br>

<img src="../img/string-length-data-annotations.png" width="60%">

<br>

<img src="../img/max-length-fuent-api.png" width="60%">

<br>

### Precision - HasPrecision
<p>
Küsüratlı sayılarda bir kesinlik belirtmemizi ve virgülün sağında kalan hane sayısını bildirmemizi sağlayan yapılandırmadır.
</p>

<img src="../img/precision-data-annotations.png" width="60%">

<br>

<p>
Şimdi yukarıdaki çalışmada Salary kolonuna girilecek olan ondalıklı sayının tamamının beş haneli ve virgülden sonraki kısmın ise üç haneli olmasını istediğimiz için aşağıdaki 12.345678 sayısını eklemeye çalıştığımızda otomatik olarak sayı, 12.345 şeklinde yazılacaktır. 
</p>

<img src="../img/precision-ornek-1.png" width="60%">
<img src="../img/precision-ornek-2.png" width="60%">

<br>

<img src="../img/precision-fluent-api.png" width="60%">

<br>

### Unicode - IsUnicode
<p>
Kolon içerisinde unicode karakterler kullanılacaksa bu yapılandırmadan istifade edilebilir.
</p>

<img src="../img/unicode-data-annotations.png" width="60%">

<br>

<img src="../img/unicode-fluent-api.png" width="60%">

<br>

### Comment - HasComment
<p>
Ef Core üzerinden oluşturulan veri tabanı nesneleri üzerinde bir açıklama / yorum yapmak istiyorsak bu yapılandırmaları kullanabiliriz.
</p>

<img src="../img/comment-data-annotations.png" width="60%">

<br>

<img src="../img/comment-fluent-api.png" width="60%">

<br>

### InverseProperty
<p>
İki entity arasında birden fazla ilişki varsa eğer bu ilişkilerin hangi navigation property'ler üzerinde olacağını ayarlamamızı sağlayan bir konfigürasyondur.
</p>

<img src="../img/inverse-property.png" width="60%">















