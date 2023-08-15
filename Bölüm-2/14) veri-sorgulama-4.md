# Temel Düzeyde Sorgulama Yapılanmaları

<br>

## CountAsync Fonksiyonu
<p>
Oluşturulan sorgunun execute edilmesi neticesinde kaç adet kaydın elde edileceğini sayısal olarak (int) bizlere bildiren fonksiyondur.
</p>
<p>
Peki bu fonksiyonu nasıl kullanabiliriz? Eğer aşağıdaki gibi kullanırsak bu çok maliyetli olur. Çünkü bu yöntemde verilerin count'u bellekte hesaplanıyor. 
</p>
<img src="../img/count.png">

<br>
<p>
Ve nihayetinde bütün ürünleri belleğe çekip orada saymak yerine direkt veri tabanı kısmında bu hesaplamayı yapmak daha az maliyetlidir. Yani şöyle ki;
</p>
<img src="../img/countasync.png">

<br>

## LongCountAsync Fonksiyonu
<p>
Oluşturulan sorgunun execute edilmesi neticesinde kaç adet kaydın elde edileceğini sayısal olarak (long) bizlere bildiren fonksiyondur.
</p>
<img src="../img/longcount.png">

<br>
<p>
NOT : Ayrıca hem count hem de longCount fonksiyonunda şartlı bir sorgu oluşturabiliriz. Örneğin fiyatı 500'den büyük olan ürünlerin sayısını hesapla gibi bir sorgu oluşturabiliriz.
</p>
<img src="../img/longcount-query.png">

<br>

## AnyAsync Fonksiyonu
<p>
Sorgu neticesinde verinin gelip gelmediğini bool türüyle bize bildiren fonksiyondur.
</p>
<p>
Count fonksiyonunda olduğu gibi any fonksiyonunda da şarta göre bir sorgulama yapabiliriz.
</p>
<img src="../img/anyasync.png">

<br>

## MaxAsync Fonksiyonu
<p>
Verilen kolondaki maximum değeri getirir.
</p>
<img src="../img/maxasync.png">

<br>

## MinAsync Fonksiyonu
<p>
Verilen kolondaki minimum değeri getirir.
</p>
<img src="../img/minasync.png">

<br>

## Distinct Fonksiyonu
<p>
Sorguda mükerrer kayıtlar varsa bunları tekilleştiren fonksiyondur.
</p>
<p>
Distinct fonksiyonu, IQueryable döndüğü için ekstradan ToList fonksiyonunu da sorgunun sonuna ekliyoruz.
</p>
<img src="../img/distinct.png">

<br>

## AllAsync Fonksiyonu
<p>
Sorgu neticesinde gelen verilerin, verilen şarta uyup uymadığını kontrol eder. Eğer ki tüm veriler şarta uyuyorsa true, uymuyorsa false değerini döndürür.
</p>
<img src="../img/allasync.png">

<br>

## SumAsync Fonksiyonu
<p>
Verilen kolondaki sayısal değerileri toplar.
</p>
<img src="../img/sum.png">

<br>

## Average Fonksiyonu
<p>
Verilen kolondaki sayısal değerlerin ortalamasını alır.
</p>
<img src="../img/average.png">

<br>

## Contains Fonksiyonu
<p>
Contains fonksiyonunu aşağıdaki gibi iki şekilde kullanabiliriz.
</p>
<img src="../img/contains.png">

<br>
<p>
Eğer Contains metodunu 1. şekilde kullanırsak Products tablosunun içerisinde verilen product nesnesinin bulunup bulunmadığını kontrol eder. 
</p>
<p>
Bu kontrol, veri tabanında tam olarak aynı product nesnesinin olup olmadığını kontrol eder. Yani Name, Price ve Quantity özelliklerinin tümü aynı olmalıdır. 
</p>
<p>
Eğer böyle bir ürün veri tabanında bulunursa, product1 değeri true olur, aksi takdirde false olur.
</p>
<p>
2. şekilde kullanırsak da veri tabanındaki Products tablosundan, Name özelliği içerisinde "a" harfini içeren ürünler de kontrol yapar. Bu sorgu, adında "a" harfi bulunan tüm ürünleri döndürür. 
</p>
<br>

## StartsWith Fonksiyonu
<p>
Like (....%) sorgusu oluşturmamızı sağlar.
</p>
<img src="../img/startswith.png">

<br>

## EndsWith Fonksiyonu 
<p>
Like (%....) sorgusu oluşturmamızı sağlar.
</p>
<img src="../img/endswith.png">




