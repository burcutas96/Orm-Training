# Complex Query Operators

<br>

## Inner Join

### Query Syntax
<img src="../img/inner-join.png" width="60%">

<br>

### Method Syntax
<img src="../img/inner-join-1.png" width="55%">

<br>




## Multiple Columns Join
<p>
iki veya daha fazla tabloyu birden fazla sütun üzerinden birleştirme işlemidir. Genellikle, tablolar arasında birden fazla sütun üzerinden ilişki kurulduğunda ya da karmaşık bir veri modeliniz olduğunda kullanılır.
</p>

### Query Syntax
<p>
Örneğin aşağıdaki çalışmada Photos tablosuyla Persons tablosu arasında PersonId ve Url sütunları üzerinden eşleşme sağlanmıştır. Tabi bizim Person tablomuzda 'Url' diye bir kolonumuz olmadığı için bu eşleşmeyi 'Name' kolonu üzerinden sağlıyoruz ama asıl, gerçek senaryolarda kolon isimlerinin birebir aynı olması gerekiyor!
</p>

<img src="../img/multiple-columns-join.png" width="80%">

<br>

### Method Syntax

<img src="../img/multiple-columns-join-1.png" width="50%">

<br>




## 2'den Fazla Tabloyla Join

### Query Syntax

<img src="../img/multiple-join.png" width="60%">

<br>

### Method Syntax

<img src="../img/multiple-join-1.png" width="60%">

<br>




## Group Join - GroupBy Değil!
<p>
Group Join'den kastedilen GroupBy değildir.
</p>

### Query Syntax
<p>
Person'lara karşılık gelen Order'ları gruplamak istiyorsak aşağıdaki gibi bir çalışma yapabiliriz.
</p>

<img src="../img/group-join.png" width="70%">

<br>




## Left Join
<p>
Entity framework core'da left ya da right join'i kullanabilmek için sadece query syntax yöntemini kullanabiliriz. Method syntax yöntemi kullanılamıyor.
</p>

### Query Syntax
<img src="../img/left-join.png" width="70%">

<br>

### DefaultIfEmpty() Metodu
<p>
Sorgulama sürecinde ilişkisel olarak karşılığı olmayan verilere default değerini yazdıran yani LEFT JOIN sorgusunu oluşturtan bir fonksiyondur. 
</p>

<br>




## Right Join

### Query Syntax
<img src="../img/right-join.png" width="70%">

<br>




## Full Join
<p>
Ef Core'da full join yapmak da mümkün değil. Yani ne query syntax ile ne method syntax ile yazılamıyor. Ama yine de full join yapmak istiyorsak bir mantık uyguluyoruz. Öncelikle left join daha sonrasında right join yapıyoruz. Ardından da bu iki sorguyu birleştirip full join işlemini gerçekleştirmiş oluyoruz.
</p>

### Query Syntax
<img src="../img/full-join.png" width="70%">

<br>




## Cross Join

### Query Syntax
<img src="../img/cross-join.png" width="60%">

<br>




## Collection Selector'da Where Kullanma Durumu
<p>
Aşağıdaki işlemin sorgusunda aslında bir inner join yapılmış oluyor.
</p>

### Query Syntax
<img src="../img/collection-selector.png" width="70%">

<br>



## Cross Apply
<p>
Inner Join'e benziyor.
</p>

### Query Syntax
<img src="../img/cross-apply.png" width="70%">

<br>





## Outer Apply
<p>
Left Join'e benziyor.
</p>

### Query Syntax
<img src="../img/outer-apply.png" width="70%">

<br>




