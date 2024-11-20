# IEntityTypeConfiguration İle Yapılandırmaları Harici Dosyalara Ayırmak

## OnModelCreating 
<p>
Entity'ler üzerinde konfigürasyonel çalışmalar yapmamızı sağlayan bir fonksiyondur. 
</p>

<br>

## IEntityTypeConfiguration&lt;T&gt; Arayüzü
<p>
Entity bazlı yapılacak olan konfigürasyonları, o entity'e özel harici bir dosya üzerinde yapmamızı sağlayan bir arayüzdür.
</p>

<p>
Harici bir dosyada konfigürasyonların yürütülmesi, merkezi bir yapılandırma noktası oluşturmamızı sağlamaktadır. Ekstra olarak; entity sayısının fazla olduğu senaryolarda yönetilebilirliği arttıracak ve yapılandırma ile ilgili geliştiricinin yükünü azaltacaktır.
</p>

<img src="../img/IEntityTypeConfiguration.png" width="60%">

<br>

## ApplyConfiguration() Metodu
<p>
Bu metot, harici konfigürasyonel sınıflarımızı Ef Core'a bildirebilmek için kullanılır. Örneğin yukarıdaki Order modeliyle ilgili olan OrderConfiguration sınıfındaki konfigürasyonları bu metot sayesinde Ef Core'a bildirmiş oluyoruz.
</p>

<img src="../img/IEntityTypeConfiguration-1.png" width="60%">

<br>

## ApplyConfigurationsFromAssembly() Metodu
<p>
Uygulama bazında oluşturulan harici konfigürasyonel sınıfların her birini OnModelCreating metodunda ApplyConfiguration ile tek tek bildirmek yerine, bu sınıfların bulunduğu Assembly'i bildirerek IEntityTypeConfiguration arayüzünden türeyen tüm sınıfları ilgili entity'e karşılık konfigürasyonel değer olarak baz almasını sağlayan bir metottur. 
</p>

<img src="../img/applyConfigurationsFromAssembly.png" width="60%">



















