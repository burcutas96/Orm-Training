# EF Core İçin İşlevsel Fonksiyonlar

## Database Property'si
<p>
Database property'si veri tabanını temsil eden Ef Core'un bazı işlevlerinin detaylarına erişmemizi sağlar.
</p>

<br>

## BeginTransaction()
<p>
Ef core, transaction yönetimini otomatik bir şekilde kendisi gerçekleştirmektedir. Eğer ki transaction yönetimini anlık olarak ele almak istiyorsak BeginTransaction() fonksiyonunu kullanabiliriz.
</p> 

<br>

<img src="../img/transaction.png" width="80%">

<br>

## CommitTransaction()
<p>
Ef core üzerinde yapılan çalışmaların commit edilebilmesi için kullanılan bir fonksiyondur. 
</p>

<br>

## RollbackTransaction()
<p>
Ef core üzerinde yapılan çalışmaların rollback edilebilmesi için kullanılan bir fonksiyondur. 
</p>

<img src="../img/transaction-1.png" width="80%">

<br>

## CanConnect()
<p>
Verilen connection string'e karşılık bağlantı kurulabilir bir veri tabanı var mı yok mu bunun bilgisini bool türde veren bir fonksiyondur.
</p>

<img src="../img/can-connect.png" width="75%">

<br>

## EnsureCreated()
<p>
Ef core'da tasarlanan veri tabanını migration kullanmadan run-time'da yani kod üzerinde veri tabanı sunucusuna inşa edebilmek için kullanılan bir fonksiyondur.
</p>

<img src="../img/ensure-created.png" width="60%">

<br>

## EnsureDeleted()
<p>
İnşa edilmiş veri tabanını run-time'da silmemizi sağlayan bir fonksiyondur.
</p>

<img src="../img/ensure-deleted.png" width="55%">

<br>

## GenerateCreateScript()
<p>
Context nesnesinde yapılmış olan veri tabanı tasarımı her neyse ona uygun bir Sql Script'ini string olarak veren bir metottur.
</p>

<p>
Yani veri tabanını entity framework core üzerinden tasarlayıp bir zamandan sonra entity framework core'u kullanmaman gerektiğini anlarsan ve başka bir araçla yola devam etmen gerekirse, bu veri tabanıyla ilgili yapmış olduğun çalışmaları script olarak elde etmek istiyorsan GenerateCreateScript() metodunu kullanabilirsin.
</p>

<img src="../img/generate-create-script.png" width="55%">

<br>

## ExecuteSql()
<p>
Veri tabanına insert, update veya delete sorgularını yazdığımız bir metottur. Bu metot işlevsel olarak alacağı parametreleri Sql Injection saldırılarına karşı korumaktadır. 
</p>

<img src="../img/execute-sql.png" width="75%">

<br>

## ExecuteSqlRaw()
<p>
Veri tabanına insert, update veya delete sorgularını yazdığımız bir metottur. Bu metotta ise sorguyu Sql Injection saldırılarına karşı koruma görevi, geliştiricinin sorumluluğundadır. 
</p>

<img src="../img/execute-sql-raw.png" width="75%">

<br>

<p>
Bu fonksiyonda string interpolation'da kullanılabilir, string ifade de. Ama her iki durumda da dışardan gelen parametre doğrudan sorguya eklenirse, SQL Injection riskine açık hle gelir. Bu yüzden geliştirici, parametrelerin güvenliğini manuel olarak sağlamalıdır.
</p>

<br>

## SqlQuery()
<p>
SqlQuery() fonksiyonu her ne kadar erişilebilir olsa da artık desteklenmemektedir. Bunun yerine DbSet property'si üzerinden erişilebilen FromSql fonksiyonu gelmiştir / kullanılmaktadır.
</p>

<br>

## SqlQueryRaw()
<p>
SqlQuery() fonksiyonu her ne kadar erişilebilir olsa da artık desteklenmemektedir. Bunun yerine DbSet property'si üzerinden erişilebilen FromSqlRaw fonksiyonu gelmiştir / kullanılmaktadır.
</p>

<br>

## GetMigrations()
<p>
Uygulamada üretilmiş olan tüm migration'ları rum-time'da programatik olarak elde etmemizi sağlayan metottur. 
</p>

<br>

## GetAppliedMigrations()
<p>
Uygulamada migrate edilmiş olan, veri tabanında uygulanan tüm migration'ları rum-time'da programatik olarak elde etmemizi sağlayan metottur. 
</p>

<br>

## GetPendingMigrations()
<p>
Uygulamada migrate edilmemiş olan, veri tabanında uygulanmayan tüm migration'ları rum-time'da programatik olarak elde etmemizi sağlayan metottur. 
</p>

<br>

## Migrate()
<p>
Migration'ları programatik olarak run-time'da migrate edebilmek için kullanılan bir fonksiyondur.
</p>

<br>

### !!! Önemli
<p>
EnsureCreated fonksiyonu migration'ları kapsamamaktadır. Bu yüzden migration'lar içerisinde yapılan çalışmalar EnsureCreated fonksiyonunda geçerli olmayacaktır. 
</p>

<br>

## OpenConnection()
<p>
Veritabanı bağlantısını manuel açar.
</p>

<br>

## CloseConnection()
<p>
Veritabanı bağlantısını manuel kapatır.
</p>

<br>

## GetConnectionString()
<p>
İlgili context nesnesinin o anda kullandığı connection string değeri neyse onu elde etmemizi sağlar. 
</p>

<br>

## GetDbConnection()
<p>
Ef core'un kullanmış olduğu Ado.NET alt yapısının kullandığı DbConnection nesnesini elde etmemizi sağlayan fonksiyondur. Yani bizi Ado.NET kanadına götürür.
</p>

<br>

## SetDbConnection()
<p>
Özelleştirilmiş connection nesnelerini ef core mimarisine dahil etmemizi sağlayan fonksiyondur.
</p>

<br>

## ProviderName Property'si
<p>
Ef core'un kullanmış olduğu provider neyse onun bilgisini bize getiren property'dir.
</p>

<img src="../img/providerName.png" width="85%">













