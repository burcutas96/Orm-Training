# Relationships (İlişkiler) Terimleri

<br>

## Principal Entity (Asıl Varlık) Nedir?

<p>
Kendi başına var olabilen tabloyu modelleyen entity'e denir.
</p>

<img src="../img/principal-entity.png">

<br>

<p>
Örneğin yukarıdaki ilişkide principal entity, Departmanlar tablosunu modelleyen 'Departman' entity'sidir.
</p>

<p>
Çünkü Departmanlar herhangi bir Çalışan olmasa da var olabiliyor mu? Olabiliyor. Ama Çalışanlar, Departman olmadan var olamıyor. 
</p>

<br>

## Dependent Entity (Bağımlı Varlık) Nedir?

<p>
Kendi başına var olamayan, bir başka tabloya ilişkisel olarak bağımlı olan tabloyu modelleyen entity'e denir.
</p>

<p>
Örneğin yukarıdaki ilişkide dependent entity, Calisanlar tablosunu modelleyen 'Calisan' entity'sidir.
</p>

<br>

## Foreign Key Nedir?

<p>
Principal Entity ile Dependent Entity arasındaki ilişkiyi sağlayan key'dir. 
</p>

<p>
Dependent Entity'de tanımlanır. Principal Entity'deki Principal Key'i tutar.
</p>

<img src="../img/foreign-key.png">

<br>

## Principal Key Nedir?

<p>
Principal Entity'deki id'nin ta kendisidir. Başka bir deyişle Principal Entity'nin kimliği olan kolonu ifade eden property'dir.
</p>

<p>
Yani Departman modelindeki 'Id' property'si, principal key'dir.
</p>

<br>

## Navigation Property Nedir?

<p>
İlişkisel tablolar arasındaki fiziksel erişimi entity class'ları üzerinden sağlayan property'lerdir.
</p>

<img src="../img/navigation-property.png">

<br>

* Bir property'nin navigation property olabilmesi için kesinlikle entity türünden olması gerekiyor.


* Navigation property'ler entity'lerdeki tanımlarına göre n'e n yahut 1'e n şeklinde ilişki türlerini ifade etmektedirler.  
 
<br>

## İlişki Türleri

### One to One İlişkisi

<p>
Çalışan ile adresi arasındaki ilişki, karı koca arasındaki ilişki one to one ilişkisine örnek olarak verilebilir.
</p>

### One to Many İlişkisi

<p>
Çalışan ile departman arasındaki ilişki, anne ve çocukları arasındaki ilişki one to many ilişkisine örnek olarak verilebilir.
</p>

### Many to Many İlişkisi

<p>
Çalışanlar ile projeler arasındaki ilişki, kardeşler arasındaki ilişki many to many ilişkisine örnek olarak verilebilir.
</p>

<br>


## Entity Framework Core'da İlişki Yapılandırma Yöntemleri

### Default Conventions
<p>
Varsayılan entity kurallarını kullanarak yapılan ilişki yapılandırma yöntemleridir.
</p>

<p>
Navigation property'lerini kullanarak ilişki şablonlarını çıkarmaktadır.
</p>

<br>

### Data Annotations Attributes
<p>
Entity'nin niteliklerine göre ince ayarlar yapmamızı sağlayan attribute'lardır. [Key], [Foreign Key] gibi...
</p>

<br>

### Fluent Api
<p>
Entity modellerindeki ilişkileri yapılandırırken daha detaylı çalışmamızı sağlayan yöntemdir.
</p>


* <b>HasOne:</b> İlgili entity'nin ilişkisel entity'e birebir ya da bire çok  olacak şekilde ilişkisini yapılandırmaya başlayan metottur.


* <b>HasMany:</b> İlgili entity'nin ilişkisel entity'e çoka bir ya da çoka çok olacak şekilde ilişkisini yapılandırmaya başlayan metottur.

* <b>WithOne:</b> HasOne ya da HasMany'den sonra birebir ya da çoka bir olacak şekilde ilişki yapılandırmasını tamamlayan metottur.

* <b>WithMany:</b> HasOne ya da HasMany'den sonra bire çok ya da çoka çok olacak şekilde ilişki yapılandırmasını tamamlayan metottur.
 










