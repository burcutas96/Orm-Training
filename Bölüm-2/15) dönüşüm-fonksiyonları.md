# Sorgu Sonucu Dönüşüm Fonksiyonları
<p>
Bu fonksiyonlar ile sorgu neticesinde elde edilen verileri isteğimiz doğrultusunda farklı türlerde projeksiyon edebiliyoruz. 
</p>
<br>

## ToDictionaryAsync Fonksiyonu
<p>
Sorgu neticesinde gelecek olan veriyi bir dictionary olarak elde etmek / tutmak / karşılamak istiyorsak eğer bu fonksiyon kullanılabilir.
</p>
<img src="../img/todictionary.png">

<br>
<p>
ToList ile aynı amaca hizmet etmektedir. Yani ikiside oluşturulan sorguyu execute ederler. Aralarındaki fark ise;
</p>
<p>
- ToList, gelen sorgu neticesini entity türünde bir koleksiyona (List&lt;Entity&gt;) dönüştürmekteyken 
</p>
<p>
- ToDictionary, gelen sorgu neticesini Dictionary türünden bir koleksiyona dönüştürmektedir.
</p>
<br>

## ToArrayAsync Fonksiyonu
<p>
Oluşturulan sorguyu execute edip sonucu, entity dizisi olarak elde eder. 
</p>
<img src="../img/toarray.png">

<br>

## Select Fonksiyonu
<p>
Select fonksiyonunun işlevsel olarak birden fazla davranışı söz konusudur.
</p>
<p>
<strong>1.</strong> Select fonksiyonu, generate edilecek olan sorgunun çekilecek olan kolonlarını ayarlamamızı sağlamaktadır.
</p>
<p>
Yani eğer bir tablonun bütün kolonlarını değilde belirlediğimiz kolonlarını getirmek istiyorsak Select fonksiyonunu kullanabiliriz.
</p>
<p>
Eğer select fonksiyonunu aşağıdaki şekilde kullanırsak seçme işlemi bellekte yapılacağı için performanslı, düşük maliyetli bir sorgulama yapmış olmayız.
</p>
<img src="../img/select-tolistden-sonra.png">

<br>
<p>
O yüzden bunun yerine, sorgu daha oluşturulma aşamasındayken yani IQueryable'dayken Select fonksiyonunu kullanmalıyız. Daha sonra sorguyu execute etmeliyiz. 
</p>
<img src="../img/select-tolistden-önce.png">

<br>
<p>
<strong>2.</strong> Select fonksiyonu gelen verileri farklı türlerle de (T, anonim) karşılamamızı sağlarlar.
</p>
<img src="../img/select-anonim.png">

<br>
<p>
Eğer new keyword'ünün yanında herhangi bir tür belirtmezsek bu anonim türüne karşılık gelir. Yani herhangi bir türü yok aslında.
</p>
<p>
Aynı şekilde bu gelen Products verilerini oluşturduğumuz başka bir tür ile de karşılayabiliriz. Örneğin Id ve Price property'lerinin olduğu ProductDetail diye bir class oluşturulur ve gelen veriler bu türle karşılanabilir.
</p>
<br>

## SelectMany Fonksiyonu
<p>
Select ile aynı amaca hizmet eder. Lakin ilişkisel tablolar neticesinde gelen koleksiyonel verileri de tekilleştirip projeksiyon etmemizi sağlar.
</p>
<img src="../img/selectMany.png">



