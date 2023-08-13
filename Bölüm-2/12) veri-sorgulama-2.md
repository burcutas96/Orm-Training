# Temel Düzeyde Sorgulama Yapılanmaları

<br>

## ToListAsync Fonksiyonu
<p>
üretilen sorguyu execute ettirmemizi sağlayan fonksiyondur. Yani IQueryable'dan IEnumerable'a geçiş yapmamızı sağlıyor. 
</p>

### Method Syntax
<img src="../img/tolistasync.png">

### Query Syntax
<p>
Bu sorguyu iki farklı şekilde oluşturabiliriz.
</p>
<img src="../img/tolistasyncquery.png">

<br><br>


## Where Fonksiyonu
<p>
Oluşturulan sorguya where şartı eklememizi sağlayan fonksiyondur.
</p>

### Method Syntax
<img src="../img/where.png">

### Query Syntax
<p>
Yine her iki yöntemle de sorgumuzu oluşturabiliriz.
</p>
<img src="../img/where-query.png">

<br><br>


## OrderBy Fonksiyonu
<p>
İlgili sorguya sıralama operasyonu gerçekleştirmiş oluruz. Default olarak ascending davranışı gösterir. Yani küçükten büyüğe doğru bir sıralama yapar. Bu davranışın tam tersi olan descending'de ise büyükten küçüğe doğru bir sıralama yapar.
</p>

### Method Syntax - Ascending
<img src="../img/orderby-method.png">

### Query Syntax - Ascending
<img src="../img/orderby-asc.png">

<br>

### Method Syntax - Descending
<img src="../img/orderby-desc-method.png">

### Query Syntax - Descending
<img src="../img/orderby-des.png">
 
<br><br>


## ThenBy Fonksiyonu
<p>
Sıralama işlemlerinde kullanılan bir fonksiyondur. OrderBy fonksiyonu ile birinci sıralamayı yaptıktan sonra kullanılır. 
</p>
<p>
Birden fazla ThenBy fonksiyonu kullanarak da çoklu seviyeli sıralama yapabiliriz.
</p>
<p>
Bu fonksiyonu da OrderBy'daki gibi ascending ve descending davranışlarıyla kullanabiliriz.
</p>

### Method Syntax
<img src="../img/thenby.png">


### Query Syntax
<img src="../img/thenby-query.png">

<br>
<p>
Yukarıdaki çalışmada ikinci sorguda thenBy kullanılmıyor. Dolayısıyla sıralama işlemlerini virgüllerle ayırarak veyahut tekrar orderby keyword'ünü kullanarak yapabiliriz.
</p>





