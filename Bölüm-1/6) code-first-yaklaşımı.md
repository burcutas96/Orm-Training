# Code First Yaklaşımı  

<br>

## Migration ve Migrate Kavramları Nelerdir?
<p>
Migration; kod kısmında modellediğimiz veri tabanını, veri tabanı sunucusunun anlayacağı hale getiren bir c# class'ıdır.
</p>
<p>
Migration'ı veri tabanına gönderip fiziksel olarak veri tabanını oluşturma eylemine migrate etme denir.
</p>
<p>
Yani "migration oluşturuluyor" denildiğinde şunu anlamamız lazım: Projede tasarlanan kod mantığının veri tabanı sunucusuna göç ettirilebilecek modeli oluşturuluyor.
</p>
<p>
"Migrate ediliyor" denildiğinde ise bu migration'ı artık veri tabanı sunucusuna gönderip orada fiziksel olarak veri tabanındaki gerekli değişiklikler yaptırılıyor anlamına gelir. Ya da eğer veri tabanı yoksa veri tabanı orada oluşturuluyor anlamına gelir.
</p>
<br>

## Migration Oluşturmak İçin Temel Gereksinimler Nelerdir?
<p>
Migration oluşturmak için temelde Ef Core aktörleri olan DbContext ve Entity class'larını oluşturmak gerekir.
</p>
<p>
Bunları oluşturduktan sonra migration; Package Manager Console ve Dotnet Cli olmak üzere iki türlü talimatla verilebilir.
</p> 
<p>
Ancak her iki yöntemi de kullanabilmek için Microsoft.EntityFrameworkCore.Tools kütüphanesini uygulamaya yüklememiz gerekecektir.
</p> 
<br>

## Migration Oluşturma
<img src="../img/migration-oluşturma.png">

<br>
<p>
Şimdi biz pmc veya dotnet cli ile migration oluşturduğumuzda Migrations klasörünün altında migration'nın oluşturulduğunu görürüz. 
</p>
<p>
Ve bu migration class'ının içerisinde override edilmiş iki tane fonksiyon oluşturulur. Bunlardan biri Up fonksiyonu iken diğeri Down fonksiyonudur. 
</p>
<img src="../img/migration-classı.png">

<br>
<p>
Up fonksiyonu, migrate sürecinde veri tabanı sunucusuna gönderilecek olan bütün yapılanmaları, yenilikleri barındırır.
</p>
<p>
Down fonksiyonu ise veri tabanı sunucusunda yapılmış olanları, geri almamızı sağlayacak olan çalışmaları barındırır.
</p>
<p>
Mesela var olan bir tablo üzerinde bir değişiklik yapmak istediğimizde o değişikliği veri tabanı sunucusuna gönderebilmek için de bir migration oluşturmamız gerekecek ve bu süreçteki yenilikler, değişiklikler Up fonksiyonunun içerisinde olacak.
</p>
<p>
Ama tablodaki yenilikleri geri almamız gerekirse o zamanda Down fonksiyonunu kullanmamız gerekecek.
</p>
<br>

## Migration Path'ini Belirleme
<p>
Oluşturduğumuz migration'lar default olarak "Migrations" klasörü altında oluşturuluyor. Eğer biz oluşturulacak olan bu migration'ın başka bir klasör altında oluşturulmasını istiyorsak aşağıdaki komutu kullanabiliriz:
</p>
<img src="../img/migration-path.png">

<br>
<p> 
Bu komutu aşağıdaki gibi de kullanabiliriz:
</p>
<img src="../img/migration-path1.png">

<br>
<p>
Yani burada migs klasörünün altındaki ef klasörünün içinde bu migration'ı oluştur demiş oluyoruz. 
</p>
<br>

## Migration Silme
<p>
Oluşturulan migration'ı silmek için;
</p>
<img src="../img/migration-silme.png">

<br>

## Migration'ları Listeleme
<p>
Oluşturulan migration'ları listelemek için;
</p>
<img src="../img/migration-listeleme.png">

<br>

## Migration'ları Migrate Etme (Up Fonksiyonu)  
<p>
Şimdi veri tabanını modelleyip migration'a aktardıktan sonra geriye bir tek hedef veri tabanı sunucusuna bu çalışmayı göndermek yani migrate etmek kalıyor.
</p>
<img src="../img/migrate-etmek.png">

<br>

## Migration'ları Geri Alma (Down Fonksiyonu)
<p>
Migration'ları migrate ettiğimizde up fonksiyonu çalışırken geri aldığımızda down fonksiyonu çalışır.
</p>
<img src="../img/migrationları-geri-alma.png">

<br>
<p>
Peki neden migration'ları geri alırken [Migration Name] kullanılıyor? Bunun sebebi de; bir sürü migration'larımızın olduğunu düşünelim ve hangi migration'a kadar geri almak istiyorsak o migration'ın adını belirtiyoruz. 
</p>
<br>

## Kod üzerinden Migrate Operasyonu
<p>
Migration'ları tool aracılığıyla migrate edebildiğimiz gibi kod üzerinden de uygulamanın ayakta olduğu süreçte (runtime'da) veri tabanını migrate edebiliriz.
</p>
<img src="../img/kod-üzerinden-migrate.png">

<br>
<p>
Burada AppDbContext yerine kod kısmındaki DbContext sınıfımızın ismini yazıyoruz. Örneğin;
</p>

<img src="../img/kod-üzerinden-migrate1.png">

<br>
<h3>
Peki bu bizim ne işimize yarayabilir?  
</h3>
<p>
Örneğin biz bir yazılım oluşturduk ve bu oluşturduğumuz yazılım son kullanıcıya gitti. Şimdi son kullanıcı veri tabanını oluşturması gerektiği durumlarda oturup entity framework'le ilgili migration oluşturup ardından bunu migrate etmeyi mi bilecek? Yani update-database kodunu bilmesi mi gerekecek ya da dotnet cli nedir bunları bilmek zorunda mı kalacak?
</p>
<p>
İşte bunları bilemeyeceği için biz, kullanıcının uygulamayı ayağa kaldırdığı esnada veri tabanının hedef sunucuda modellenmesini isteriz. Bu işlemi de yukarıda bahsedilen kod sayesinde yapabiliriz.
</p>
<br>

## Son Uyarılar
* <p> Veri tabanı sınıfları üzerinde yapılan tüm değişiklikleri migration eşliğinde gönderiniz. Böylece her değişikliği migration ile kayıt altına almış oluruz. Bu da bize veri tabanı gelişim sürecini gösterir. Ve ihtiyaca binaen istediğimiz noktaya geri dönüş sağlayabiliriz.  
</p>

* <p>Migration'lara mümkün mertebe dokunmamak lazım. Lakin ileride ihtiyaç doğrultusunda ham sql cümlecikleri ekleyeceğimiz ve hatta Stored Procedure gibi yapıları oluşturacağımız noktalar olacaktır.
</p>





