# Ef Core ile Veri Silme Detayları

<br>
<p>
Yine öncelikle hangi veri tabanı üzerinde işlem yapıcaksak o veri tabanının bir context'ini oluşturuyoruz.
</p>
<img src="../img/dbcontext-instance.png">

<br>
<p>
Veriyi silmek için de o veriyi context üzerinden bir sorgulama neticesinde elde ediyoruz.
</p>
<img src="../img/güncellenecek-veri.png">

<br>
<p>
Daha sonrasında elde edilen bu veriyi Remove fonksiyonuyla silip, SaveChanges fonksiyonuyla da sorguyu oluşturup veri tabanına gönderiyoruz. 
</p>
<img src="../img/remove.png">

<br>

## Takip Edilmeyen Nesneler Nasıl Silinir?
<p>
Eğer ki sileceğimiz veri context'den gelmediyse yani veriyi herhangi bir sorgu neticesinde context'den elde etmediysek örneğin aşağıdaki gibi elde ettiysem;
</p>
<img src="../img/update-ile-veriyi-elde-etme.png">

<br>
<p>
o zaman bu veriyi nasıl silebiliriz? 
</p>
<p>
Ef core'da; bu şekilde oluşturduğumuz nesneler direkt veri tabanından elde edilmediği için veri tabanındaki nesne ile direkt eşleştirilmez.
</p>
<p>
Aynı zamanda bu oluşturmuş olduğumuz nesne context'den gelmediği için ChangeTracker tarafından da takip edilmez. Ve takip edilmediği için direkt SaveChanges fonksiyonunu da çağıramam.
</p>
<p>
Bu sebeple, takip edilmeyen nesneyi ef core üzerinden silmek istiyorsak Remove fonksiyonunu kullanabiliriz.
</p>
<img src="../img/remove-fonksiyonu.png">

<br>

## EntityState ile Silme İşlemi
<p>
Verinin durumunu değiştirerek de silme işlemini gerçekleştirebiliriz.
</p>
<img src="../img/entity-state.png">

<br>
<p>
Hem context'ten aldığımız verinin hem de kendi oluşturduğumuz verinin state'ini değiştirerek veriyi database'den silebiliriz. 
</p>
<br>

## Birden Fazla Veri Silinirken Nelere Dikkat Edilmelidir?
<p>
Şimdi SaveChanges, her tetiklendiğinde yapılan işlemleri bir transaction eşliğinde veri tabanına gönderir ve orada execute eder. 
</p>
<p>
Yani ben SaveChanges'ı ne kadar çağırırsam o kadar transaction oluşturulmuş olacak. Ve ben birden fazla veri siliyorsam, her silmeden sonra da SaveChanges'ı çağırırsam bu çok maliyetli olur.
</p>
<p>
Bu yüzden her seferinde SaveChanges'ı çağırmaktansa bütün silme işlemlerim bittikten sonra SaveChanges'ı çağırmalıyım.
</p>
<br>

## RemoveRange Nedir?
<p>
Elimizde birden fazla veri varsa ve bunları tek tek silmek yerine ya da bunların state'lerini deleted olarak değiştirmek yerine bu verileri bir dizi olarak alıp silme işlemini yapan bir fonksiyondur.
</p>
<img src="../img/remove-range.png">

<br>
<p>
İstersek yukarıdaki gibi RemoveRange fonksiyonuna bir dizi de verebiliriz ya da silinecek olan verileri virgüllerle ayırarak tek tek de verebiliriz. 
</p>
<br>







