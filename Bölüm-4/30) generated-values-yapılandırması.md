# Generate Values Yapılandırması 

<br>

## Generated Value Nedir? 
<p>
Ef Core'da üretilen değerlerle ilgili çeşitli modellerin ayrıntılarını yapılandırmamızı sağlayan bir özelliktir. 
</p>

<br>

## Default Values 
<p>
Ef Core herhangi bir tablonun, herhangi bir kolonuna yazılım tarafından bir değer gönderilmediği taktirde bu kolona hangi değerin (default value) üretilip yazdırılacağını belirleyen yapılanmadır.
</p>

<br>

## HasDefaultValue()
<p>
Static veri veriyor.
</p>

<img src="../img/hasDefaultValue-1.png" width="60%">

<br>

## HasDefaultValueSql()
<p>
Sql cümleciği veriyor.
</p>

<img src="../img/hasDefaultValueSql-1.png" width="60%">

<br>

## Computed Columns  
<p>
Tablo içerisindeki kolonlar üzerinde yapılan aritmetik işlemler neticesinde üretilen kolondur.
</p>

<img src="../img/hasComputedColumnSql-1.png" width="60%">

<br>

## Value Generation

### Primary Key
<p>
Herhangi bir tablodaki satırı kimlik vari bir şekilde tanımlayan, tekil (unique) olan sütun veya sütunlardır. 
</p>  

<br>

### Identity
<p>
Identity, yanlızca otomatik artan bir sütundur. Bir sütun primary key olmadan da identity olarak tanımlanabilir.
</p>

<br>

<p>
    <b>
    !!! Primary key, kimlik vari bir özellik gösterip benzersiz bir sütun oluştururken; identity, ardışık özellik gösteren bir sütundur. Bu iki özellik genellikle birlikte kullanılır. Bu yüzden ef core primary key olan bir kolonu otomatik olarak identity olacak şekilde yapılandırmaktadır.
    </b>
</p>

<br>

<p>
    <b>
    Ancak böyle olması için bir zorunluluk yoktur. Yani biz bir kolonu sadece primary key olarak da ayarlayabiliriz, identity olarak da. Burda tek dikkat etmemiz gereken nokta şu: Identity bir tabloda sadece bir tane olabilir.
    </b>
</p>

<br>

<p>
    <b>
    Yani biz bir tabloda birden fazla sütunu primary key olarak tanımlayabiliyorken (Bu duruma composite primary key denir.) identity kolonunu sadece bir sütunda ayarlayabiliyoruz.
    </b>
</p>

<br>

## DatabaseGenerated

<br>

### DatabaseGeneratedOption.None - ValueGeneratedNever
<p>
Bir kolonda değer üretilmeyecekse eğer None ile işaretlenir. Ef Core'un default olarak primary key kolonlarına getirdiği identity özelliğini kaldırmak istiyorsak eğer None'ı kullanabiliriz. 
</p>

<img src="../img/databaseGeneratedOption-None.png" width="60%">

<br>

<img src="../img/valueGeneratedNever.png" width="60%">

<br>

### DatabaseGeneratedOption.Identity - ValueGeneratedOnAdd
<p>
Herhangi bir kolona Identity özelliğini vermemizi sağlayan konfigürasyondur.
</p>

<b>Sayısal Türlerde :</b>
<p>
Eğer ki Identity özelliği bir tabloda sayısal olan bir kolonda kullanılacaksa, bu durumda ilgili tablodaki primary key kolonundan iradeli bir şekilde identity özelliğinin kaldırılması gerekmektedir.
</p>

<br>

<b>Sayısal Olmayan Türlerde :</b>
<p>
Eğer ki Identity özelliği bir tabloda sayısal olmayan bir kolonda kullanılacaksa, bu durumda ilgili tablodaki primary key kolonunun identity özelliğinin kaldırılmasına gerek yoktur. Bu kaldırma işlemini arkaplanda Ef Core kendisi yapacaktır.
</p>

<img src="../img/databaseGeneratedOption-identity.png" width="60%">

<br>

<img src="../img/valueGeneratedOnAdd.png" width="60%">

<br>

### DatabaseGeneratedOption.Computed - ValueGeneratedOnAddOrUpdate
<p>
Ef Core üzerinde bir kolon Computed column ise ister Computed olarak belirleyebilirsiniz isterseniz de belirlemeden kullanmaya devam edebilirsiniz.
</p>

<img src="../img/databaseGeneratedOption-computed.png" width="60%">

<br>

<img src="../img/valueGeneratedOnAddOrUpdate.png" width="60%">








