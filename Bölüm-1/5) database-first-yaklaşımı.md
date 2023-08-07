# Database First Yaklaşımı
<p>
Entity framework core aracında tersine mühendislik diye bir terim duyabiliriz. Bu terim database first yaklaşımında geçerlidir.
</p>
<br>

## Tersine Mühendislik (Reverse Engineering)
<p>
Tersine mühendislik, bir sunucudaki veri tabanının iskelesini / yapısını / modelini kod kısmında oluşturma sürecidir. 
</p>
<p>
Veri tabanı sunucusundan herhangi bir veriyi kod kısmında modellemeyi iki türlü gerçekleştiririz.
</p>
<p>
Bunlardan biri Package Manager Console (PMC) iken diğeri Dotnet Cli'dır. 
</p>
<br>

## 1- Package Manager Console (PMC) ile Tersine Mühendislik

<img src="../img/pmc.png">

<br>
<p>
Yukarıdaki resimdeki talimatı pmc'dan verdiğimizde, connection string'de belirtilen veri tabanındaki tüm tablo yapılanması kod kısmında modellenecektir.
</p>
<p>
Scaffold-DbContext talimatı, veri tabanının kod kısmında modellenmesini sağlar. Bunu hem pmc'da hem de dotnet cli'da bu komutu kullanabiliyoruz.
</p>
<p>
Connection string, hangi sunucudaki hangi veri tabanını çalıştıracaksak onu belirttiğimiz yer burasıdır.
</p>
<p>
Microsoft.EntityFrameworkCore.[Provider], connection string'de belirttiğimiz veri tabanı hangisiyse, bu veri tabanının kütüphanesi olacak.
Yani o provider yerine kullandığımız veri tabanının kütüphanesi gelecek.
</p>
<p>
Package manager console ile veri tabanını modelleyebilmek için aşağıdaki kütüphanelerin projeye yüklenmesi gerekmektedir: 
</p>

* <p>Microsoft.EntityFrameworkCore.Tools</p>
* <p>Database Provider (Örneğin; Microsoft.EntityFrameworkCore.SqlServer)
</p>
<br>

## 2- Dotnet CLI ile Tersine Mühendislik
<img src="../img/dotnet-cli-tersine-mühendislik.png">

<br>
<p>
Baştaki dotnet komutunu, dotnet cli'yı kullandığımızı bildirmek için kullanıyoruz.   
</p>
<p>
Resimdeki talimatı PowerShell'den veya cmd'den verdiğimiz zaman da hedefteki veri tabanı direkt kod kısmında modellenmiş olacaktır.
</p>
<p>
Dotnet CLI ile veri tabanını modelleyebilmek için aşağıdaki kütüphanelerin projeye yüklenmesi gerekmektedir: 
</p>

* <p>Microsoft.EntityFrameworkCore.Design</p>
* <p>Database Provider (Örneğin; Microsoft.EntityFrameworkCore.SqlServer)
</p>
<br><br>

## Tabloları Belirtme
<p>
Varsayılan olarak veri tabanındaki tüm tablolar modellenir. Eğer sadece istenilen tabloların modellenmesini istiyorsak aşağıdaki gibi talimatların verilmesi yeterlidir:
</p>
<img src="../img/tabloları-belirtme.png">

<br>

## DbContext Adını Belirleme
<p>
Scaffold ile modellenen veri tabanı için oluşturulacak context nesnesi adını veri tabanından alacaktır. Eğer ki context nesnesinin adını değiştirmek istiyorsanız aşağıdaki gibi çalışabilirsiniz.
</p>
<img src="../img/context-adı.png">

<br>

## Path ve Namespace Belirtme
<p>
Entity'ler ve DbContext sınıfı, default olarak direkt projenin kök dizinine modellenir ve projenin varsayılan namespace'ini kullanırlar. Eğer ki bunlara müdahale etmek istiyorsanız aşağıdaki gibi talimat verebilirsiniz.
</p>
<img src="../img/namespace-path.png">

<br>

## Model Güncelleme
<p>
Veri tabanında olan değişiklikleri kod kısmına yansıtabilmek için Scaffold talimatını tekrar vermemiz gerekecektir lakin verilen talimat neticesinde ilgili sınıfların zaten var olduğuna dair hata mesajı sizleri yüksek ihtimalle karşılayacaktır.  
</p>
<p>
Böyle bir durumda veri tabanı modeline değişiklikleri manuel olarak yansıtabileceğimiz gibi (ki tavsiye edilmez!) zorla, yeniden, en güncel haliyle modellenmesii sağlayabiliriz.
</p>
<p>
Bunun için aşağıdaki gibi Force talimatının verilmesi yeterli olacaktır.
</p>
<img src="../img/force.png">

<br>

## Modellerin Özelleştirilmesi
<p>
Database first yaklaşımında veri tabanı nesneleri otomatik olarak modellenmekte ve generate edilmektedir. Bazen bu otomatize olan süreçte manuelde olsa entitylerde yahut context nesnesinde özelleştirmeler yapmak isteyebiliriz.
</p>
<p>
Ama biliyoruz ki veri tabanında yapılan değişiklikler neticesinde Force komutu eşliğinde tüm değişiklikler kod kısmına sıfırdan yansıtılabilir ve bu da yapılan değişikliklerin ezilme riskinin söz konusu olduğu anlamına gelir.
</p>
<p>
Bu tarz özelleştirme durumlarında bizzat model sınıflarını kullanmaktansa bunların partial class'ları üzerinde çalışmak en doğrusudur.
</p>
<p>
Burayı daha iyi anlayabilmek adına serideki 7. videonun 33:55 saniyesinden itibaren izleyebilirsin. 
</p>
 







