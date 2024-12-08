# Loading Related Data

<br>

## Lazy Loading Nedir?
<p>
Navigation property'ler üzerinde bir işlem yapılmaya çalışıldığı taktirde ilgili property'nin temsil ettiği tabloya özel bir sorgu oluşturup execute edilmesi ve verilerin yüklenmesini sağlayan bir yaklaşımdır.
</p>

<img src="../img/lazy-loading.png" width="60%">

<br>

<p>
Yukarıdaki çalışmada 2 id'sine sahip Employee verisini çağırırken ilişkili olduğu Region verisini sorguya eklemediğimiz için hâliye Region verisi null gelicek ve biz 'Name' değerine ulaşmak istersek hata alıcaz. 
</p>

<p>
Ama biz Region üzerinde Lazy Loading işlemini uygularsak eğer, ne zaman ki Employee'dan Region nesnesi çağrılırsa o zaman daha 'Name' verisini çağırmadan evvel gerekli sql sorgusu oluşturulup Region nesnesiyle birlikte Employee verisi getirilir ve en sonunda da 'Name' değerine hatasız bir şekilde ulaşılır.  
</p>

<br>

## Proxy'lerle Lazy Loading
<p>
Öncelikle proxy yapılanmasını kullanabilmek için "Microsoft.EntityFrameworkCore.Proxies" kütüphanesini kullanmamız gerekiyor.
</p>

<p>
Şimdi proxy üzerinden Lazy Loading yapacaksak eğer, OnConfiguring() metodu içerisinde aşağıdaki gibi her iki çalışmayı da yapabiliriz. 
</p>

<img src="../img/lazy-loading-1.png" width="60%">

<br>

<p>
Yukarıdaki çalışmalardan herhangi birini yaptığımız taktirde uygulamamızda Lazy Loading yaklaşımı enable hâle gelmiş olacaktır.
</p>

<br>

## Property'lerin Virtual Olması
<p>
Eğer ki proxy'ler üzerinden lazy loading yaklaşımını gerçekleştireceksek navigation property'lerin virtual ile işaretlenmiş olması gerekmektedir. Aksi taktirde patlama meydana gelecektir.  
</p>

<img src="../img/lazy-loading-2.png" width="60%">

<br>

<img src="../img/lazy-loading-3.png" width="60%">

<br>

### Önemli Nokta!
<p>
Eğer ki biz herhangi bir yaklaşımlar lazy loading kullanırsak debug süreçlerinde şöyle bir yanılma söz konusu olabilir.
</p>

<img src="../img/lazy-loading-5.png" width="60%">

<br>

<p>
Örneğin, yukarıdaki sorguyu çalıştırdığımızda debug modundayken employee değişkenine gelen verileri gözlemleyecek olursak eğer aşağıdaki gibi Orders ve Region verilerinin de geldiğini görmüş olucaz.
</p>

<img src="../img/lazy-loading-4.png" width="60%">

<br>

<p>
Böyle bir durumda şöyle düşünebiliriz: "Demek ki biz sorgulamayı yaptığımız da navigation property üzerinden Orders veya Region verilerine herhangi bir talepte bulunmasak dahi bu veriler yükleniyor." diye zannedebiliriz.
</p>

<p>
Ki bu, yanlış bir düşüncedir. Çünkü biz burada debug yaparken ilgili objenin içerisindeki property'lere bakarken aslında Orders ve Region property'lerini tetiklemiş oluyoruz. Hâliyle bunlar tetiklendiği için Orders ve Region ile ilgili sorgular arkaplanda oluşturulmuş oluyor. Ve bu durumun esas sebebi virtual ile ilgilidir. Buna run time'da karar verilip tetikleniyor.
</p>

<p>
<b>Bunu daha detaylı şöyle açıklayabiliriz:</b> 
</p>

<p>
Şimdi uygulamayı tekrar debug modda çalıştırdığımızda öncelikle Employee ile ilgili sorgulamanın yapıldığını aşağıdaki gibi görücez. 
</p>

<img src="../img/lazy-loading-6.png" width="95%">

<br>

<p>
Ama 'employee' değişkenine tıklayıp değerlerini açtığımız anda sql server profiler'da Orders ve Region verilerinin de sorgulandığını görmüş olucaz.
</p>

<img src="../img/lazy-loading-7.png" width="95%">

<br>

<img src="../img/lazy-loading-8.png" width="45%" style="margin-right:45px">
<img src="../img/lazy-loading-9.png" width="45%">

<br>

<p>
Yani aslında lazy loading'de tüm veriler top yekün belleğe yüklenmiyor. Biz navigation property'leri tetikledikçe, oradaki ihtiyacı belirttikçe veriler; belleğe yüklenmiş olacaktır.
</p>

<br>

## Proxy Olmaksızın Lazy Loading 
<p>
Proxy'ler tüm platformlarda desteklenmeyebilir. Böyle bir durumda manuel bir şekilde Lazy Loading'i kullanmak mecburiyetinde kalabiliriz.
</p>

<br>

## ILazyLoader Inteface'i İle Lazy Loading
<p>
Öncelikle ILazyLoader operasyonunu, interface'ini uygulayabilmek için Microsoft.EntityFrameworkCore.Abstractions kütüphanesini uygulamamıza yüklememiz gerekiyor. 
</p>

<p>
Daha sonrasında aşağıdaki gibi bir çalışmayla Employee nesnesinin ilişkili olduğu Region verileri için lazy loading işlemini manuel bir şekilde gerçekleştirmiş oluyoruz. Hem Employee class'ının içerisinde hem de Region class'ı içerisinde bu çalışmayı yapıyoruz.
</p>

<img src="../img/lazy-loading-10.png" width="45%" style="margin-right:60px">
<img src="../img/lazy-loading-11.png" width="45%">

<br>

<p>
Manuel yapılan lazy loading operasyonlarında Navigation Property'lerin 'virtual' keyword'ü ile işaretlenmesine gerek yoktur!
</p>

<br>

## Delegate İle Lazy Loading
<img src="../img/lazy-loading-12.png" width="55%">

<br>

<p>
Şimdi yukarıdaki Action nesnesi için _lazyLoader içinde tanımlanmış bir Load() metodu olmadığı için aşağıda olduğu gibi extension bir metot hazırlıyoruz.
</p>

<img src="../img/lazy-loading-13.png" width="80%">

<br>

## N+1 Problemi
<p>
Şimdi bizler lazy loading operasyonunu hangi yöntemle uygularsak uygulayalım bu N+1 problemi meydana çıkabiliyor.
</p>

<p>
Lazy loading kullanım açısından oldukça maliyetli ve performans düşürücü bir etkiye sahiptir. O yüzden kullanırken mümkün mertebe dikkatli olmalı ve özellikle navigation property'lerin döngüsel tetiklenme durumlarında lazy loading'i tercih etmemeliyiz. Aksi taktirde lazy loading, her bir tetiklemeye karşılık aynı sorguları üretip execute edecektir. Bu problemi de N+1 olarak nitelendirmekteyiz.
</p>

<p>
Özetle mümkün mertebe ilişkisel verileri eklerken Lazy Loading kullanmamaya özen göstermeliyiz. 
</p>









