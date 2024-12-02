# Indexes
<p>
Index, bir sütuna dayalı sorgulamaları daha verimli ve performanslı hâle getirmek için kullanılan yapıdır.
</p>

<br>

## Index'leme Nasıl Yapılır?
<p>
Primary key, foreign key ve alternate key kolonları; otomatik olarak indexlenir. Bunların dışında farklı kolonlara index'ler atamak istiyorsak attribute ya da fluent api olmak üzere iki farklı özellikten istifade edebiliriz. Bunlardan biri [Index] attribute'u, diğeri ise HasIndex() metodudur.
</p>

<br>

## Index Attribute'u
<img src="../img/index-attribute.png" width="55%">

<br>

## HasIndex() Metodu
<img src="../img/index-fluent-api.png" width="60%">

<br>

<p>
Yukarıdaki örneklerde artık "Name" kolonumuz index'lenmiş oldu. İndex'lendiği için de aşağıdaki gibi "Name" üzerinden yapılan tüm sorgulamalarımız; daha az maliyetli, daha yüksek performanslı ve verimli bir şekilde gerçekleştirilecektir. 
</p>

<img src="../img/index-ornek-1.png" width="60%">

<br>

## Composite Index

<img src="../img/composite-index-ornek-1.png" width="60%">

<br>

<p>
Composite index, bir veritabanında birden fazla sütun üzerinde yapılan indeksleme yöntemidir. Özellikle sorguda birden fazla sütunun sıklıkla filtreleme ya da sıralama işlemlerinde kullanıldığı durumlarda avantajlıdır.
</p>

<br>

<img src="../img/composite-index-attribute.png" width="60%">

<br>

<img src="../img/composite-index-fluent-api.png" width="60%">

<br>

## Birden Fazla Index Tanımlama
<p>
Tablolarımızda aşağıdaki görseldeki gibi birden fazla kolonu index'leyebiliriz.
</p>

<img src="../img/birden-fazla-index.png" width="60%">

<br>

<p>
Ama aklımıza şöyle bir şey gelebilir: "Veri tabanı çalışmalarımızda ne kadar kolon varsa hepsine gidip index'i ekleyelim, lazım olunca da zaten performanslı bir çalışma sergilemiş oluruz." diye düşünebiliriz. Amma velakin şunu bilmekte fayda var, her bir index veri tabanı açısından ekstra bir maliyet olacağından dolayı bir tabloda yoğun olarak sorgulama yapılan kolonlar üzerinde index'lerin oluşturulmasını tavsiye ediyoruz.  
</p>

<br>

## Index Uniqueness 
<p>
Index'leri unique hâle getirebilmekteyiz. Index'ler default hâlleriyle unique değillerdir. Eğer index'lemiş olduğumuz kolonu unique hâle getirmek istiyorsak attribute ya da fluent api'dan faydalanabiliriz.
</p>

<img src="../img/unique-index.png" width="60%">

<br>

<img src="../img/unique-index-1.png" width="60%">

<br>

## Index Sort Order - Sıralama Düzeni (EF Core 7.0) 

<p>
EF Core'da Index Sort Order, dizinlerin sıralama düzenini belirleyerek sorgu performansını artırmayı sağlar.
</p>

<h3> 
    <li>AllDescending - Attribute</li>
</h3>

<p>
Tüm index'lemelerde descending davranışının bütünsel olarak konfigürasyonunu sağlar.
</p>

<img src="../img/index-sort-order-1.png" width="60%">

<br>

<h3> 
    <li>IsDescending - Attribute</li>
</h3>

<p>
Index oluşturma sürecindeki her bir kolona göre sıralama davranışını hususi olarak ayarlamak istiyorsak IsDescending parametresi, attribute içerisinde kullanılır.
</p>

<img src="../img/index-sort-order-2.png" width="60%">

<br>

<p>
Örneğin yukarıdaki çalışmada IsDescending parametresi sayesinde 'Name' kolonu için indexleme descending olarak yapılırken 'Surname' kolonu için ascending olarak yapılır.
</p>

<br>

<h3> 
    <li>IsDescending() Metodu</li>
</h3>

<p>
Fluent api'da bu sıralama düzenini belirlemek için IsDescending metodunu kullanırız.
</p>

<img src="../img/index-sort-order-3.png" width="60%">

<br>

## Index Name
<p>
Index dediğimiz bu yapılanma özünde bir veri tabanı nesnesi, objesidir. Hâliyle her objenin bir ismi olduğu gibi index'lerimizin de bir ismi olacaktır. Dolayısıyla arkaplanda default bir şekilde verilen bu ismi aşağıdaki alternatiflerle özelleştirebiliriz.
</p>

<img src="../img/index-name-attribute.png" width="70%">

<br>

<img src="../img/index-name-fluent-api.png" width="70%">

<br>

## Index Filter
<p>
Index Filter özelliği, bir index üzerinde filtreleme yaparak sadece belirli bir koşulu karşılayan kayıtları getirmeyi sağlar. Yani tüm kayıtları index'e eklemek yerine yalnızca koşulu sağlayan kayıtlar index'e dahil edilir.
</p>

<img src="../img/index-filter.png" width="60%">

<br>

## Included Columns
<p>
Şimdi yukarıdaki Employee entity'sinden devam edecek olursak eğer biz index kolonlarımızı 'Name' ve 'Surname' olarak belirlersek ve yapacağımız sorguda Where şartından sonra Select fonksiyonunda 'Name' ve 'Surname' dışında başka kolonları da Select'e dahil edersek sorgunun performansını düşürmüş, maliyeti arttırmış oluruz.
</p>

<img src="../img/index-include-properties-1.png" width="75%">

<br>

<p>
Böyle bir durumda IncludeProperties() metoduyla, Select sürecinde eklenebilecek property'leri yani kolonları da index tablosuna ekleyebiliriz. Yani bizim yapmış olduğumuz index'in dışında ekstradan başka bir kolonu Select ile sorguda elde etmek istiyorsak ve sorgunun da performanslı olmasını istiyorsak bu kolonları IncludeProperties() metodu ile bildirebilir ve index tablosuna dahil edebiliriz.
</p>

<img src="../img/index-include-properties-2.png" width="75%">









