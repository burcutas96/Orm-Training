# GroupBy ve Foreach Fonksiyonları

<br>

## GroupBy Fonksiyonu

<p>
Gruplama yapmamızı sağlayan fonksiyondur.
</p>
<p>
Örneğin "Aynı fiyat bilgisine sahip kaç tane ürün var" bunu öğrenmek istiyorsam GroupBy fonksiyonunu kullanmalıyım.
</p>
<p>
Eğer bu sorguyu mssql'de oluşturmam gerekseydi, aşağıdaki sorguyu yazmamız gerekecekti.
</p>
<img src="../img/mssql-groupby.png">

<br>
<p>
Ancak yukarıdaki sorguyu ef core ile oluşturmamız gerekirse aşağıdaki çalışmayı yapmamız gerekecek.
</p>
<img src="../img/groupBy.png">

<br>
<p>
Yukarıdaki çalışmada gruplanacak olan kolonu GroupBy fonksiyonuna parametre olarak veriyoruz. Ve GroupBy, bu verileri fiyat kolonuna göre gruplayıp buna karşılık kaç tane veri varsa onu getirecek.
</p>
<p>
Select'de bizim oluşturduğumuz group parametresi, gruplama işleminin yapıldığı her bir veri grubunu ve buna karşılık gelen toplam veri sayısını temsil ediyor. Ve bu her bir veri grubunun toplam sayısına ulaşabilmek için Count fonksiyonunu, bu gruplamanın yapıldığı tablo kolonuna ulaşabilmek için ise Key property'sini kullanıyoruz.
</p>
<p>
Böylece bu sorgu sonucunda üretilen çıktı ile mssql'de üretilen çıktı aynı olacaktır.
</p>
<img src="../img/groupby-output.png">

<br>
<p>
Peki bu method syntax'a karşılık gelen query syntax nasıl oluşturulmalı? Onu da aşağıdaki gibi yapabiliriz:
</p>
<img src="../img/groupby-query-syntax.png">

<br>

## Foreach Fonksiyonu
<p>
Bir sorgulama fonksiyonu değildir. Foreach döngüsünün metot halidir.
</p>
<p>
Sorgulama neticesinde elde edilen koleksiyonel veriler üzerinde iterasyonel olarak dönmemizi ve verileri teker teker elde edip işlemler yapabilmemizi sağlayan fonksiyondur. 
</p>
<p>
Örneğin yukarıdaki çalışmada elde ettiğimiz products listesini foreach fonksiyonu ile aşağıdaki gibi dönebiliriz. 
</p>
<img src="../img/foreach-fonksiyonu.png">


