# One to One İlişkisinde Veri Silme

<p>
Bu örneğimizde Principal entity olan Person ile Dependent entity olan Address tabloları arasında birebir bir ilişki söz konusu. 
</p>

<p>
Id'si 1 olan Person'ın, Address verisini silmek için;
</p>

<img src="../img/data-delete-1.png">

<br>
<br>

# One to Many İlişkisinde Veri Silme

<p>
Bu örneğimizde Principal entity olan Blog ile Dependent entity olan Posts tabloları arasında bire çok bir ilişki söz konusu. 
</p>

<p>
Id'si 1 olan Blog'un, 2 id'sine sahip Post verisini silmek için;
</p>

<img src="../img/data-delete-2.png">

<br>
<br>

# Many to Many İlişkisinde Veri Silme

<p>
Bu örneğimizde Principal entity'ler olan Book ve Author ile cross table olan BookAuthor tabloları arasında çoka çok bir ilişki söz konusu. 
</p>

<p>
Id'si 1 olan Book'un, 2 id'sine sahip Author verisini silmek için;
</p>

<img src="../img/data-delete-3.png">

<p>
Silme işlemini yaparken yorum satırında olan context.Authors.Remove(author); satırını kullanırsak seçtiğimiz author hem Authors tablosundan silinecek hem de cross table'da bu author verisi olan tüm satırlar silinecek.
</p>

<p>
O yüzden bu farkı bilerekten silme işlemini gerçekleştirmeliyiz.
</p>

<br>
<br>

<p>
Biz şuana kadar herhangi bir principal table'daki verinin, dependent table'daki ilişkisel verileri arasından birini silmeye çalışırken Ef core'un nasıl bir davranış sergileyeceğini gördük. 
</p>

<p>
Peki principal table'daki bir veriyi silmeye çalışırsak nolacak? Principal veri silinirse, buna bağlı dependent veriler silinecek mi? 
</p>

<p>
İşte böyle bir durumda artık davranış modeli karşımıza çıkacak. O da Cascade Delete modelidir.
</p>

<br>

# Cascade Delete Modeli

<p>
Bunu modellerken üç farklı davranış belirleyebiliriz. Bunlar cascade, setNull ve restrict davranışlarıdır.
</p>

<p>
Bu davranış modelleri Fluent API ile konfigure edilmektedir.  
</p>



## Cascade 

<p>
Esas (principal) tablodan silinen verinin, buna bağımlı olan tablodaki verilerini silmemizi sağlar. 
</p>

<img src="../img/data-delete-4.png">

<br>

## SetNull 

<p>
Esas tablodan silinen verinin, buna bağımlı olan tablodaki verilerine null değerinin atanmasını sağlar. 
</p>

<p>
One to One senaryolarda eğer ki Foreign key ve Primary key kolonları aynı ise SetNull davranışını kullanamayız! Çünkü foreign key kolonu null değer alabilirken primary key kolonu null değer alamaz. Alamadığı için de tutarsızlık olur, hata alırız. 
</p>

<img src="../img/data-delete-5.png">

<br>

## Restrict 

<p>
Esas tablodan herhangi bir veri silinmeye çalışıldığında o veriye karşılık dependent table'da ilişkisel bir veri ya da verileri varsa bu silme işlemi engellenecektir.
</p>

<img src="../img/data-delete-6.png">








