# Stored Procedure
<p>
View'ler gibi komplex sorgularımızı daha basit bir şekilde tekrar kullanılabilir bir hâle getirmemizi sayğlayan veri tabanı nesnesidir.
</p>

<p>
View'ler tablo misali bir davranış sergilerken stored procedure'ler ise fonksiyonel bir davranış sergiler. Ve bu anlatılanların dışında da artıları vardır. 
</p>

<br>

## Stored Procedure Oluşturma
<p>
<b>1. Adım : </b> Boş bir migration oluşturunuz.
</p>

<p>
<b>2. Adım : </b> Migration içesindeki Up fonksiyonuna stored procedure'ın create komutlarını yazınız. Down fonksiyonuna ise Drop komutlarını yazınız.
</p>

<p>
<b>3. Adım : </b> Migrate ediniz.
</p>

<img src="../img/stored-procedure.png" width="65%">

<br>

## Stored Procedure'ı Kullanma
<p>
Stored procedure'ı kullanabilmek için bir entity'e ihtiyacımız vardır. Bu entity'nin DbSet property'si olarak context nesnesine de eklenmesi gerekmektedir. Ardından bu DbSet property'si üzerinden FromSql() fonksiyonunu kullanarak 'Exec ....' komutu eşliğinde stored procedure yapılanmasını kullanabiliriz. 
</p>

<img src="../img/stored-procedure-1.png" width="80%">

<br>

<p>
Stored Procedure için oluşturduğumuz bu 'PersonOrder' entity'sinin veri tabanına yansıtılacak bir tablo olmadığını belirtebilmek için [NotMapped] attribute'unu kullanıp OnModelCreating() fonksiyonunda da bu entity'nin bir primary key kolonunun olmayacağını bildiriyoruz.
</p>

<img src="../img/stored-procedure-2.png" width="80%">

<br>

## Geriye Değer Döndüren Stored Procedure Kullanma 

<img src="../img/stored-procedure-3.png" width="80%">

<br>

<img src="../img/stored-procedure-4.png" width="80%">

<br>

## Parametreli Stored Procedure Kullanma 

### Input ve Output Parametreli Stored Procedure Kullanma 

<img src="../img/stored-procedure-5.png" width="80%">

<br>

<img src="../img/stored-procedure-6.png" width="85%">














