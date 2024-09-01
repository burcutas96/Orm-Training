# One to One Relationship

## Default Convention 
<p>
Bu ilişkide default convention kullanılacaksa eğer, her iki entity'de Navigation Property ile birbirlerini tekil olarak referans ederek fiziksel bir ilişkinin olacağı ifade edilir.
</p>

<img src="../img/one-to-one-1.png">

<br>

## Data Annotations
<p>
Navigation property'ler tanımlanmalıdır.
</p>

<p>
Foreign key kolonunun ismi default convension dışında bir kolon olacaksa eğer [ForeingKey] attribute'u ile bunu bildirebiliriz.
</p>

<p>
Amma velakin bu Foreign Key kolonu oluşturulmak zorunda değildir. 
</p>

<img src="../img/one-to-one-2.png">

<br>

<p>
Birebir ilişkide ekstradan foreign key kolonuna ihtiyaç olmayacağından dolayı dependent entity'deki 'Id' kolonunu hem foreign key hem de primary key olarak kullanmayı tercih ediyoruz. 
</p>

<img src="../img/one-to-one-3.png">

<br>

<p>
Calisanlar tablosuyla CalisanAdresleri tablosu arasında birebir ilişkiyi 'Id' kolonu üzerinden kurduğumuz için buradaki hatayı primary key constraint veriyor. Çünkü primary key gereği 'Id' kolonu unique olmak zorunda. 2 Id'sine sahip bir tane daha veri oluşturamayız. Böylece birebir ilişkinin bir ayağının garantisini almış oluyoruz.
</p>

<img src="../img/one-to-one-4.png">

<br>

<p>
Burada da foreign key hata veriyor. Çünkü Id kolonuna verdiğimiz değerler kesinlikle Calisanlar'daki Id değerleri olmak zorunda. 4 değeri Calisanlar tablosunda olmadığı için foreign key'de hata alıyoruz.
</p>

<p>
Böylece ekstradan foreign key kolonuna karşılık verisel fazladan bir alan tahsis etmemiş oluyoruz hem de index, constraint gibi maliyetleri minimize etmiş oluyoruz.
</p>

<br>

## Fluent Api
<p>
Navigation property'ler tanımlanmalıdır.
</p>

<p>
Bu yöntemde entity'ler arasındaki ilişkiyi context sınıfı içerisinde OnModelCreating fonksiyonunu override ederek metotlar aracılığıyla tasarlarız. Yani tüm sorumluluk bu fonksiyon içerisindeki çalışmalardadır.
</p>

<img src="../img/one-to-one-5.png">

<br>

<p>
Model'ların (entity) veri tabanında generate edilecek yapıları, OnModelCreating fonksiyonu içerisinde konfigüre ederiz.
</p>








