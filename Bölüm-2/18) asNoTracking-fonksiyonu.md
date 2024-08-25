# AsNoTracking Fonksiyonu

<br>

<p>
Context üzerinden gelen tüm datalar Change Tracker mekanizması tarafından takip edilmektedir. Change Tracker takip ettiği nesnelerin sayısıyla doğru orantılı bir şekilde bir maliyete sahiptir.
</p>

<p>
Bu yüzden üzerinde işlem yapılmayacak verilerin takip edilmesi bizlere lüzumsuz yere bir maliyet ortaya çıkaracaktır.
</p>

<p>
AsNoTracking metodu; context üzerinden sorgu neticesinde gelen verilerin, Change Tracker tarafından takip edilmesini engeller.
</p>

<p>
Context üzerinden yapmış olduğumuz sorgulama neticesinde gelecek olan bütün dataların takip edilmesini istemiyorsak, bu datalar üzerinde herhangi bir değişiklik yapmayacaksak AsNoTracking ile buradaki takip mekanizmasını koparabiliriz. 
</p>

<p>
AsNoTracking metodu ile ChangeTracker'ın ihtiyaç olmayan verilerdeki maliyetini törpülemiş oluruz.
</p>

<p>
AsNoTracking fonksiyonu ile yapılan sorgulamalarda verileri elde edebilir, bu verileri istenilen noktalarda kullanabilir lakin veriler üzerinde herhangi bir değişiklik / update işlemi yapamayız.
</p>

<br>

## AsNoTrackingWithIdentityResolution Fonksiyonu 
<p>
Change Tracker mekanizması sayesinde yinelelen datalar aynı instance'ları kullanırlar.
</p>

<img src="../img/asNoTrackingWithIdentityResolution.png">

<br>

<p>
Ancak AsNoTracking metodu ile yapılan sorgularda farklı instance'larla karşılanırlar.
</p>

<img src="../img/asNoTrackingWithIdentityResolution-1.png">

<br>

<p>
Yani Change Tracker mekanizması yinelenen verileri tekil instance olarak getirir. Burada ekstradan bir performans kazancı söz konusudur. Bizler yaptığımız sorgularda AsNoTracking metodu ile takip mekanizmasının maliyetini kırmak isterken bazen daha büyük maliyetlere sebebiyet verebiliriz. (Özellikle ilişkisel tabloları sorgularken bu duruma dikkat etmemiz gerekiyor.)
</p>

<p>
AsNoTracking ile elde edilen veriler takip edilmeyeceği için yinelenen verilerin ayrı instance'larda olmasına sebebiyet veriyoruz. Çünkü Change Tracker mekanizması; takip ettiği nesneden bellekte varsa eğer aynı nesneden bir daha oluşturma gereği duymadan, ayrı noktalardaki ihtiyacı aynı instance üzerinden gidermektedir. 
</p>

<p>
Böyle bir durumda hem takip mekanizmasının maliyetini ortadan kaldırmak hem de yinelenen dataları tek bir instance üzerinde karşılamak için AsNoTrackingWithIdentityResolution fonksiyonunu kullanabiliriz.
</p>

<img src="../img/asNoTrackingWithIdentityResolution-2.png">

<br>

<p>
AsNoTrackingWithIdentityResolution fonksiyonu AsNoTracking fonksiyonuna nazaran yavaştır / maliyetlidir ancak Change Tracker mekanizmasına göre de daha performanslı ve az maliyetlidir.
</p>

<br>

## AsTracking Fonksiyonu
<p>
Context üzerinden gelen dataların Change Tracker tarafından takip edilmesini iradeli bir şekilde ifade etmek için kullandığımız fonksiyondur.
</p>

<p>
Peki Change Tracker zaten sorgularda default olarak çağırılıyorsa biz bu fonksiyonu nerelerde, neden kullanıcaz?
</p>

<p>
Bir sonraki inceleyeceğimiz UseQueryTrackingBehavior metodunun davranışı gereği uygulama seviyesinde Change Tracker'ın default olarak devrede olup olmamasını ayarlıyor olacağız. Eğer ki default olarak pasif hâle getirilirse böyle bir durumda takip mekanizmasının ihtiyaç olduğu sorgularda AsTracking fonksiyonunu kullanabiliriz. Böylece takip mekanizmasını iradeli bir şekilde devreye sokmuş oluruz.       
</p>

<br>

## UseQueryTrackingBehavior Fonksiyonu
<p>
Ef Core / uygulama seviyesinde ilgili context'ten gelen verilerin üzerinde Change Tracker mekanizmasının davranışını temel seviyede belirlememizi sağlayan fonksiyondur. Yani konfigürasyon fonksiyonudur.
</p>

<img src="../img/useQueryTrackingBehavior.png">

<br>

<p>
DbContext class'ı içerisindeki OnConfiguring metodunda bu davranışın konfigürasyonunu sağlamış oluyoruz. 
</p>

<p>
Eğer 'NoTracking' parametresini seçersek context üzerinden gelen hiçbir nesne takip edilmeyecektir.
</p>

<p>
'NoTrackingWithIdentityResolution' parametresini seçersek nesneler takip edilmeyecek ama yinelenen dataların ayrı instance'larda olmasını engelleyecektir.
</p>

<p>
'TrackAll' parametresini seçersek de nesnelerin takip edilmesini söyleyecektir. Ve bu default hâlidir.
</p>

