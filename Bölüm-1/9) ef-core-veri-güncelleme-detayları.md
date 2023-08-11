# Ef Core ile Veri Güncelleme Detayları

<br>
<p>
Yine öncelikle hangi veri tabanı üzerinde işlem yapıcaksak o veri tabanının bir context'ini oluşturuyoruz.
</p>
<img src="../img/dbcontext-instance.png">

<br>
<p>
Veriyi güncelleyebilmek için o veriyi context üzerinden bir sorgulama neticesinde elde ediyoruz.
</p>
<img src="../img/güncellenecek-veri.png">

<br>
<p>
Daha sonrasında elde edilen bu veriyi istediğimiz gibi güncelleyerek veri tabanına SaveChanges fonksiyonuyla gönderiyoruz. 
</p>
<img src="../img/güncellenen-veriyi-kaydetme.png">

<br>
<p>
SaveChanges fonksiyonu ChangeTracker sayesinde burada yapmış olduğumuz çalışmanın bir update işlemi olduğunu anlayacağı için bizim başka bir işlem yapmamıza gerek kalmıyor.
</p>
<br>

## ChangeTracker Nedir?
<p>
ChangeTracker, context üzerinden gelen verilerin takibinden sorumlu bir mekanizmadır. Bu takip mekanizması sayesinde nesnelerin delete yahut update sorgularının oluşturulup oluşturulmayacağı anlaşılır.
</p>
<p>
Böylelikle ef Core yapılanmasında; yapılan davranışa uygun sorgu, generate edilerek veri tabanına gönderilir. 
</p>
<br>

## Takip Edilmeyen Nesneler Nasıl Güncellenir?
<p>
Eğer ki güncelleyeceğimiz veri context'den gelmediyse yani veriyi herhangi bir sorgu neticesinde context'den elde etmediysek örneğin veriyi aşağıdaki gibi elde ettiysem;
</p>
<img src="../img/update-ile-veriyi-elde-etme.png">

<br>
<p>
o zaman bu veriyi nasıl güncelleyebiliriz? 
</p>
<p>
Ef core'da; bu şekilde oluşturduğumuz nesneler direkt veri tabanından elde edilmediği için veri tabanındaki nesne ile direkt eşleştirilmez.
</p>
<p>
Aynı zamanda bu oluşturmuş olduğumuz nesne context'den gelmediği için ChangeTracker tarafından da takip edilmez. Ve takip edilmediği için direkt SaveChanges fonksiyonunu da çağıramam.
</p>
<p>
Bu sebeple, takip edilmeyen nesneyi ef core üzerinden güncellemek istiyorsak eğer Update fonksiyonunu kullanabiliriz.
</p>
<img src="../img/update-fonksiyonu.png">

<br>
<p>
Ve en nihayetinde de sorguyu oluşturup veri tabanına gönderebilmek için SaveChanges fonksiyonunu çağırıyoruz.
</p>
<p>
Not: Update fonksiyonunu kullanabilmek için kesinlikle ilgili nesnenin id değeri verilmelidir.
</p>
<br>

## EntityState Nedir?
<p>
Bir entity instance'ının durumunu ifade eden, bize onunla ilgili bilgi veren referanstır.
</p>
<p>
Bir nesnenin üzerinde herhangi bir işlem yapılmadıysa, en sade halindeyse o zaman bu nesnenin durumu "Detached"dir.  
</p>
<img src="../img/detached.png">

<br>
<p>
Eğer üzerinde bir değişiklik yaparsak eğer yaptığımız işleme göre bir değer yazdıracaktır. Örneğin bu nesneyi güncelleyeceksek eğer "Modified" durumunu ekrana yazdıracaktır. 
</p>
<img src="../img/modified.png">

<br>
<p>
SaveChanges ile veri tabanına bu veriyi gönderirsekte nesnenin durumu "Unchanged" olarak değiştirilir. Yani veri, veri tabanına gönderildi ve artık üzerinde bir değişiklik yokmuş gibi kabul edilir. 
</p>
<img src="../img/unchanged.png">

<br>

## Birden Fazla Veri Güncellenirken Nelere Dikkat Edilmelidir?
<p>
SaveChanges fonksiyonu her çağrıldığında bir transaction oluşturduğu için bu fonksiyonu, her güncelleme işleminin sonunda çağırmak yerine bütün güncelleme işlemleri bittikten sonra çağırmalıyız. Böylece daha az maliyetli bir iş çıkarmış oluruz.
</p>




