# Temel Düzeyde Sorgulama Yapılanmaları

<br>

## SingleAsync ve SingleOrDefaultAsync Fonksiyonları
<p>
Yapılan sorguda sadece tek bir verinin gelmesi amaçlanıyorsa SingleAsync ya da SingleOrDefaultAsync fonksiyonları kullanılabilir. Aynı zamanda bunların asenkron olmayan fonksiyonları da (Single veya SingleOrDefault) kullanılabilir.
</p>

### - SingleAsync
<p>
Eğer ki sorgu neticesinde birden fazla veri geliyorsa ya da hiç gelmiyorsa her iki durumda da exception fırlatılır. Yani tek bir verinin gelmediği her durumda exception fırlatılır.
</p>
<img src="../img/singleasync.png">


### - SingleOrDefaultAsync
<p>
Eğer ki sorgu neticesinde birden fazla veri geliyorsa exception fırlatılır, hiç veri gelmiyorsa null döner.
</p>
<img src="../img/singleordefault.png">

<br><br>

## FirstAsync ve FirstOrDefaultAsync Fonksiyonları
<p>
Yapılan sorguda ilk / en üstteki verinin gelmesi amaçlanıyorsa First veya FirstOrDefault fonksiyonları kullanılabilir.
</p>

### - FirstAsync 
<p>
Hiç veri gelmezse hata fırlatır.
</p>
<img src="../img/firstasync.png">

### - FirstOrDefaultAsync 
<p>
Hiç veri gelmezse null değerini döndürür.
</p>
<img src="../img/firstordefault.png">

<br><br>

## FirstAsync, FirstOrDefaultAsync, SingleAsync ve SingleOrDefaultAsync Karşılaştırması
<img src="../img/single-vs-first.png">

<br><br>

## FindAsync Fonksiyonu
<p>
Find fonksiyonu, primary key kolonuna özel hızlı bir şekilde sorgulama yapmamızı sağlar.  
</p>
<img src="../img/findasync.png">

### - Composite Primary Key Durumu
<p>
Aşağıdaki gibi tabloların id'lerini tutarak oluşturduğumuz bir entity'de;
</p>
<img src="../img/composite.png">

<br>
<p>
Find fonksiyonunu kullanabiliriz:
</p>
<img src="../img/composite-find.png">

<br>
<p>
Yani ProductPieces tablosunda 42 ve 5 id'lerine sahip bir kayıt bulursa onu getirecek.
</p>
<br><br>

## Find ile Single, SingleOrDefault, First ve FirstOrDefault Fonksiyonlarının Karşılaştırması 
<img src="../img/find-vs-single-first.png">

<br><br>

## LastAsync ve LastOrDefaultAsync Fonksiyonları
<p>
Yapılan sorguda son / en alttaki verinin gelmesi amaçlanıyorsa Last veya LastOrDefault fonksiyonları kullanılabilir.
</p>
<p>
! Bu fonksiyonu kullanırken OrderBy fonksiyonunu da kullanmak zorundayız. Aksi taktirde run time hatası alırız.
</p>

### - LastAsync
<p>
Hiç veri gelmezse hata fırlatır.
</p>
<img src="../img/lastasync.png">

<br>
<p>
Önce productları name değerlerine göre sıralar. Daha sonrasında bu productların id'si 1011'den küçük olanlardan sonuncusunu getirir. 
</p>

### - LastOrDefaultAsync
<p>
Hiç veri gelmezse null döndürür.
</p>
<img src="../img/lastordefaultasync.png">



