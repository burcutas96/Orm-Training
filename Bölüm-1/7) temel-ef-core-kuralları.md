## OnConfiguring Fonksiyonu
<p>
Ef Core tool'unu yapılandırmak için kullandığımız bir metottur.
</p>
<p>
Context nesnesinde override edilerek kullanılmaktadır.
</p>
<br>

## Basit Düzeyde Entity Tanımlama Kuralları
<p>
Ef Core, her tablonun default olarak bir primary key kolonu olması gerektiğini kabul eder.
</p>
<p>
Haliyle bu kolonu temsil eden bir property tanımlamadığımız taktirde uygulama hata verecektir. 
</p>
<p>
Peki bizim bu primary key'e karşılık gelen property'leri nasıl tanımlamamız gerekiyor?
</p>
<p>
Aşağıda belirtilen property'ler gibi primary key kolonlarımızı oluşturabiliriz.
</p>
<img src="../img/primary-key.png">

<br>
<p>
Ama tabi ilerki konularda farklı isimlendirmelerdeki property'leri primary key olarak seçebileceğiz.
</p>



