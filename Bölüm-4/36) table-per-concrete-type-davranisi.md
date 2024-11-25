# Table Per Concrete Type Davranışı 
<p>
Table per concrete type davranışı; kalıtımsal ilişkiye sahip entity'lerin olduğu çalışmalarda, sadece concrete (somut) olan entity'lere karşılık bir tablo oluşturan davranış modelidir. 
</p>

<p>
Table per concrete type davranışı, table per type davranışının daha performanslı hâlidir diyebiliriz.
</p>

<br>

## Table Per Concrete Type Davranışı Nasıl Uygulanır?
<p>
Hiyerarşik düzlemde abstract olan yapılar üzerinden Entity fonksiyonuyla ilgili konfigürasyona girip UseTpcMappingStrategy fonksiyonu eşliğinde davranışın TPC olacağını belirleyebiliz.
</p>

<img src="../img/table-per-concrete-1.png" width="55%">

<br>

<img src="../img/table-per-concrete.png" width="60%">

<br>

## Table Per Concrete Type - Veri Ekleme

<img src="../img/table-per-concrete-2.png" width="85%">

<br>

## Table Per Concrete Type - Veri Silme

<img src="../img/table-per-concrete-3.png" width="85%">

<br>

## Table Per Concrete Type - Veri Güncelleme

<img src="../img/table-per-concrete-4.png" width="85%">















