# Entity Framework Core Nedir?

* <p> Entity framework core, orm yaklaşımını benimsemiş bir araçtır.</p>
<p>
Şimdi orm bir yaklaşımdır, kılavuzdur, yol göstericidir. Yani bir fikri savunur. İşte bu fikri, kılavuzu somutlaştıran bir araçtır. 
</p>
<p>
Dolayısıyla bu açıdan baktığımızda entity framework tek başına değildir. Yani orm araçlarından bir tanesidir. Mesela Nhibernate, dapper, entity framework vardır.
</p>

* <p>Ve aslında bütün orm araçlarının amaçları; kod içerisinde oop nimetlerinden istifade ederek sql sorguları oluşturmamızı sağlamaktır.
</p>

* <p> Açık Kaynaktır. </p>
* <p> Esnektir, geliştirilebilir.</p>
* <p> Kod içerisinde ihtiyaca binaen geliştirilmiş olan tekrarlı sql sorgularından bizleri kurtarmaktadır.</p>
* <p>Code First ve Database First yaklaşımları eşliğinde veri tabanı ile yazılım arasındaki koordinasyonu sağlamaktadır.</p>
* <p>Kod üzerinden; veri tabanı, tablo, constraint, sequence, ilişkili sorgular, view, stored procedure, function, temporal table gibi veri tabanı nesneleri oluşturmamızı ve kullanmamızı sağlamaktadır.</p>
* <p>Query için Linq sorgularını desteklemektedir.</p>
<br>

## Orm olarak neden Ef Core seçilmelidir? 
<p>
- Ef Core, her ne kadar hızlı ve performanslı bir yapıya sahip olsa da piyasadaki en hızlı orm aracıdır diyemeyiz.
</p>
<p>
Misal olarak; minimal özelliklere sahip olan Dapper, Raw (ham) sorgular kullandığından dolayı kelimenin tam anlamıyla Ef Core'dan çok daha hızlıdır.
</p>
<p>
- Lakin her bir güncellemesinde performansının arttığı gözlemlenen Ef Core'un ise birçok özelliği mevcuttur.
</p>
<p>
- Oop nimetlerinden istifade etmemizi sağlayan Ef Core ile class oluşturma, nesne değişikliklerini izleme, (Change Tracker) mapping vs. gibi türlü işlemler gerçekleştirebiliriz. 
</p>
<p>
Ancak sırf yukarıdaki özellik için de ef core tercih edilmez. Çünkü bunu nhibernate'de yapabiliyor.
</p>
<p>
Bu yüzden yukarıdaki ilk iki özelliğe göre entity framework core'u seçebiliriz. Ya da ef core'u sevdiğimiz için de seçebiliriz. 
</p>
<br>

## Ef Core nasıl yüklenir? 
<p>
İleride Ef Core ile migration yapılanmalarına vs. değiniyor olacağız. İşte bu yapılanmaları sağlayabilmek ve işlevleri yürütebilmek için belirli araçları yüklememiz gerekmektedir.
</p>
<p>
Yüklenmesi gereken araçlar;
</p>

* <p>.Net Core command-line interface (CLI) tools</p>
* <p>Package Manager Console (PMC) tools</p>
<p>
olmak üzere iki farklı kümede değerlendirilebilir.
</p>
<p>
Aslında ikiside farklı yerlerde aynı işlemleri yapıyor.
</p>
<br>

## .Net Core command-line interface (CLI) tools
<p>
.Net cli üzerinden entity framework core ile ilgili bir çalışma yapacaksam eğer .net cli'yı kurmam gerekiyor. 
</p>
<p>
dotnet-ef ile başlayan cli komutlarını ilgili pc'de aktif olarak kullanabilmemizi sağlayan tool'dur.
</p>
<img src="../img/.net-cli.png">
<p>
Microsoft.EntityFrameworkCore.Design paketi ne işe yarıyor peki? Eğer ki biz cli dediğimiz tool'u kullanarak entity framework'ün bir yaklaşımına istinaden migration yapılanmalarıyla vesaire çalışmalar sergileyebilmek istiyorsak ilgili projede bu paketin yüklü olması gerekiyor.
</p>
<br>

## Package Manager Console (PMC) tools
<p>
Visual Studio, Package Manager Console üzerinden talimatlar vermemizi sağlayan bir tool'dur.
</p>
<img src="../img/package-manager-console.png">






