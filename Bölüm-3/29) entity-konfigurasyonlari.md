# Özelleştirici Entity Konfigürasyonları - 2

### Composite Key
<p>
Tablolarda birden fazla kolonu kümülatif olarak primary key yapmak istiyorsak buna composite key denir.   
</p>

<img src="../img/composite-key.png" width="60%">

<br>

<p>
Yukarıda da görüldüğü üzere HasKey() metodu ile hem 'Id' kolonunu hem de 'Id2' kolonunu aynı anda primary key yapabiliyoruz.  
</p>

<br>

### HasDefaultSchema
<p>
Ef Core üzerinden inşa edilen herhangi bir veri tabanı nesnesi default olarak dbo şemasına sahiptir. Bunu özelleştirebilmek / ezebilmek için kullanılan bir yapılanmadır.
</p>

<img src="../img/hasDefaultSchema.png" width="60%">

<br>

### Property

* <b>HasDefaultValue:</b> Tablodaki herhangi bir kolona değer gönderilmediği taktirde default olarak hangi değeri alacağını belirlediğimiz yapılanmadır. 

<img src="../img/hasDefaultValue.png" width="60%">

<br>

* <b>HasDefaultValueSql:</b> Tablodaki herhangi bir kolona değer gönderilmediği taktirde default olarak hangi sql cümleciğinden değeri alacağını belirlediğimiz yapılanmadır. 

<img src="../img/hasDefaultValueSql.png" width="60%">

<br>

### HasComputedColumnSql
<p>
Tablolarda birden fazla kolondaki verileri işleyerek değerini oluşturan kolonlara Computed Column denmektedir. Ef core üzerinden 
</p>

<img src="../img/hasComputedColumnSql.png" width="60%">

<br>

<p>
Örneğin yukarıdaki çalışmada HasComputedColumnSql() metodu kullanılarak X ve Y kolonlarıdaki int değerler toplanarak Computed isimli kolona yazdırılacaktır.
</p>

<br>

### HasConstraintName
<p>
Ef Core üzerinden oluşturulan constraint'lere default isim vermek yerine özelleştirilmiş bir isim vermek istiyorsak bu yapılandırmadan istifade edebiliriz.
</p>

<img src="../img/hasConstraintName.png" width="60%">

<br>

### HasData
<p>
Sonraki derslerde 'Seed Data' isimli bir konuyu inceleyeceğiz. Bu konuda, migrate sürecinde veri tabanını inşa ederken bir yandan da yazılım üzerinden hazır veriler oluşturmanın yöntemini inceliyor olacağız.
</p>

<p>
İşte HasData konfigürasyonu bu operasyonun yapılandırm ayağıdır.
</p>

<img src="../img/hasData-fluent-api.png" width="60%">

<br>

<p>
HasData() ile migrate sürecinde oluşturulacak olan verilerin primary key olan id kolonlarına, iradeli bir şekilde değerlerin girilmesi gerekir.
</p>

<br>

### HasDiscriminator
<p>
İleride entity'ler arasında kalıtımsal ilişkilerin olduğu 'Table Per Type' ve 'Table Per Hierarchy' isminde konuları inceliyor olucaz. İşte bu konularla ilgili yapılandırmalarımız HasDiscriminator() ve HasValue() fonksiyonları olucak. 
</p>

<p>
HasDiscriminator() fonksiyonu, default olarak oluşturulan 'Discriminator' kolonunu farklı bir isimle özelleştirmemize olanak tanır. Bu sayede ilgili kolonu, ihtiyaçlarımıza ve projedeki isimlendirme standartlarına uygun bir şekilde yeniden adlandırabiliriz."
</p>

<img src="../img/hasDiscriminator.png" width="60%">

<br>

<img src="../img/hasDiscriminator-string.png" width="60%">

<br>

<p>
Yukarıdaki çalışmayla 'Discriminator' kolonunu 'Ayirici' ismiyle adlandırmış olduk.
</p>

<img src="../img/hasDiscriminator-ornek.png" width="60%">

<br>

<p>
Eğer 'Discriminator' kolonunda, modelin sınıf isimleri yerine kendi belirlediğimiz integer değerleri kullanmak istiyorsak, aşağıdaki örnekte olduğu gibi HasValue() fonksiyonunu kullanarak her türe özel bir değer atayabiliriz. Bu yapılandırma sayesinde; A, B ve Entity gibi sınıflara ayrı ayrı ayırt edici değerler vererek, her bir sınıfın veri tabanındaki temsilini belirlemiş oluruz.
</p>

<img src="../img/hasDiscriminator-int.png" width="60%">

<br>

### HasField
<p>
Backing Field özelliğini kullanmamızı sağlayan bir yapılandırmadır.
</p>
 
<p>
HasField() metodu, bir entity’nin doğrudan erişilemeyen (private veya protected) alanlarını (public'de olabilir) (backing fields) yapılandırmak için kullanılır. Bu metot sayesinde, bir property'nin verisini tutan ancak doğrudan dışarıya açılmayan bir alan (backing field) ile çalışabiliriz.
</p>

<p>
Genelde encapsulation için kullanılan bu alanlar, yalnızca belirli bir mantık içerisinde erişilmesini istediğimiz property'lerin verisini tutar. HasField() metodu, Entity Framework'e bu alanın hangi field (alan) ile ilişkilendirildiğini belirtmemizi sağlar.
</p>

<img src="../img/hasField.png" width="60%">

<br>

### HasNoKey
<p>
Normal şartlarda Ef Core'da tüm entity'lerin bir primary key kolonu olmak zorundadır. Eğer ki entity'de primary key kolonu olmayacaksa bunun bildirilmesi gerekir. İşte bu bildirim için kullanılan fonksiyondur.
</p>

<img src="../img/hasNoKey.png" width="60%">

<br>

### HasIndex
<p>
Sonraki konularda Ef Core üzerinden Index yapılanmasını detaylıca inceliyor olucaz. Bu yapılanmaya dair konfigürasyonlarımız HasIndex ve Index attribute'u olacaktır.
</p>

<img src="../img/hasIndex-fluent-api.png" width="60%">

<br>

### HasQueryFilter
<p>
İlerde göreceğimiz 'Global Query Filter' başlıklı dersimizin yapılandırmasıdır. Temeldeki görevi bir entity'e karşılık uygulama bazında global olarak bir filtre koymaktır.  
</p>

<img src="../img/hasQueryFilter.png" width="60%">

<br>

<p>
HasQueryFilter metodu sayesinde, Person entity'sine ait veriler sorgulanırken arka planda tanımlanan CreatedDate yılına göre bir filtre otomatik olarak eklenir. Bu da Person tablosundaki verileri; yalnızca oluşturulma yılı, güncel yılla (DateTime.Now.Year) aynı olan kayıtlarla sınırlandırır. Böylece her seferinde bu filtreyi manuel olarak eklememize gerek kalmadan, yıl bazlı bir filtreleme default olarak uygulanmış olur.
</p>
















