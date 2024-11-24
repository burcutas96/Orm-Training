# Table Per Hierarchy (TPH) Davranışı
<p>
Kalıtımsal ilişkiye sahip entity'lerin olduğu durumlarda her bir hiyerarşiye karşılık bir tablo oluşturan davranıştır. 
</p>

## Table Per Hierarchy'e Neden İhtiyaç Duyarız?
<p>
İçerisinde benzer alanlara sahip olan entity'leri migrate ettiğimizde her entity'e karşılık bir tablo oluşturmaktansa bu entity'leri tek bir tabloda modellemek isteyebilir ve bu tablodaki kayıtları discriminator kolonu üzerinden birbirlerinden ayırabiliriz. İşte bu tarz bir tabloya göre ve bu tarz bir tabloya göre sorgulama, veri ekleme, silme vs. gibi operasyonların şekillendirilmesi için TPH davranışını kullanabiliriz. 
</p>

<img src="../img/table-per-hierarchy.png" width="60%">

<br>

## Table Per Hierarchy Nasıl Uygulanır?
<p>
Ef Core'da entity'ler arasında kalıtımsal bir ilişki söz konusuysa eğer default olarak kabul edilen davranıştır. Bu yüzden herhangi bir konfigürasyon gerektirmez.  
</p> 

<p>
Table Per Hierarchy davranışı için tek yapılması gereken; entity'ler kendi aralarında kalıtımsal bir ilişkiye sahip olmalı ve bu entity'lerin hepsi DbContext nesnesine DbSet olarak eklenmelidir.    
</p>

<img src="../img/table-per-hierarchy-1.png" width="60%">

<br>

<p>
Table per hierarchy yaklaşımını sergilediğimiz bu çalışmayı migrate edersek eğer aşağıdaki gibi bir sonuçla karşılaşmış oluruz. 
</p>

<img src="../img/table-per-hierarchy-2.png" width="60%">

<br >

<img src="../img/table-per-hierarchy-3.png" width="60%">

<br>

## Discriminator Kolonu Nedir?
<p>
Table per hierarchy yaklaşımı neticesinde kümülatif olarak inşa edilmiş tablonun, hangi entity'e karşılık veri tuttuğunu ayırt edebilmemizi sağlayan bir kolondur. Ef core tarafından otomatik olarak tabloya yerleştirilir. Default olarak içerisinde entity isimlerini tutar. Discriminator kolonunu tamamen özelleştirebiliriz.
</p>

<br>

## Discriminator Kolon Adı Nasıl Değiştirilir?
<p>
Hiyerarşinin başında hangi sınıf varsa, fluent api'da onun konfigürasyonuna gidilmeli. Ardından HasDiscriminator fonksiyonu ile özelleştirilmeli.
</p>

<img src="../img/discriminator.png" width="60%">

<br>

## Discriminator Değerleri Nasıl Değiştirilir?
<p>
Yine hiyerarşinin başındaki entity konfigürasyonuna gelip, HasDiscriminator fonksiyonu ile özelleştirmede bulunarak HasValue fonksiyonu ile hangi entity'e karşılık, hangi değerin girileceğini belirtilen türde ifade edebiliriz.
</p>

<img src="../img/hasDiscriminator-1.png" width="60%">

<br>

## Table Per Hierarchy - Veri Ekleme
<p>
Davranışların hiçbirinde veri eklerken, silerken, güncellerken vs. normal operasyonların dışında bir işlem yapılmaz! Hangi davranışı kullanıyorsak ef core ona göre arkaplanda modellemeyi gerçekleştirecektir.
</p>

<img src="../img/table-per-hierarchy-veri-ekleme.png" width="60%">

<br>

## Table Per Hierarchy - Veri Silme
<p>
Table per hierarchy davranışında veri silme operasyonu, yine entity üzerinden gerçekleştirilir. 
</p>

<img src="../img/table-per-hierarchy-veri-silme.png" width="60%">

<br>

## Table Per Hierarchy - Veri Güncelleme
<p>
Table per hierarchy davranışında veri güncelleme operasyonu, yine entity üzerinden gerçekleştirilir. 
</p>

<img src="../img/table-per-hierarchy-veri-guncelleme.png" width="60%">

<br>

## Table Per Hierarchy - Veri Sorgulama 
<p>
Veri sorgulama operasyonu, bilinen DbSet property'si üzerinden yapılan sorgulamadır. Ancak burada dikkat edilmesi gereken bir husus vardır. O da şu;
</p> 

<img src="../img/table-per-hierarchy-veri-sorgulama.png" width="60%">

<p>
Kalıtımsal ilişkiye göre yapılan sorgulamada üst sınıf, alt sınıftaki verileri de kapsamaktadır. Bu yüzden sorgulamaları yapıldığında, alt sınıfların verileri de gelicektir. Buna dikkat edilmelidir.
</p>


