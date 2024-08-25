# Chance Tracker Fonksiyonu

<br>

## Change Tracking Neydi?
<p>
Context nesnesi üzerinden gelen tüm nesneler/veriler otomatik olarak bir takip mekanizması tarafından izlenir. İşte bu taki mekanizmasına Change Tracker denir. Change Tracker ile nesneler üzerindeki değişiklikler/işlemler takip edilerek bu işlemlerin fıtratına uygun sql sorgucukları generate edilir. İşte bu işleme de Change Tracking denir.
</p>

<p>
Yani bu mekanizmanın adı Change Tracker, bu mekanizmanın yapmış olduğu işleme de Change Tracking denir.
</p>

<br>

## ChangeTracker Property'si Nedir?
<p>
Takip edilen nesnelere erişebilmemizi sağlayan ve gerektirdiği taktirde işlemler gerçekleştirebilmemizi sağlayan bir property'dir.
</p>
<p>
Context sınıfının base class'ı olan DbContext sınıfının bir member'ıdır.
</p>

<img src="../img/changeTracker.png">

<br>
<p>
Görüldüğü üzere context nesnesi üzerinden ChangeTracker property'sine ulaşılmıştır.
</p>

<br>

## DetectChanges Metodu Nedir?
<p>
Ef Core, context nesnesi tarafından izlenen tüm nesnelerdeki değişiklikleri Change Tracker sayesinde takip edebilmekte ve nesnelerde olan verisel değişiklikler yakalanarak bunların anlık görüntülerini (snapshot) oluşturabilmektedir.
</p>

<p>
Ve yapılan değişikliklerin veri tabanına gönderilmeden önce algılandığından emin olmak gerekir.
</p>

<p>
SaveChanges fonksiyonu çağırıldığı anda nesneler, Ef Core tarafından otomatik kontrol edilir. Yani SaveChanges, sadece SaveChanges işlemini yapmıyor, ilk önce bir detect ediyor. Yani burada bir maliyet var aslında. SaveChanges önce Change Tracker ile ilgili gerekli kontrolleri yapıyor ondan sonra SaveChanges işlemini yapıyor.  
</p>

<p>
Ancak yapılan operasyonlarda güncel tracking verilerinden emin olabilmek için değişikliklerin algılanmasını opsiyonel olarak gerçekleştirmek isteyebiliriz.
</p>

<p>
Yani işi, ne Ef Core'a bırakmak isteyebiliriz ne de SaveChanges'a. Bunu kendi irademizle de kontrol etmek isteyebiliriz. İşte bunun için DetectChanges fonksiyonu kullanılabilir ve her ne kadar Ef Core değişiklikleri otomatik algılıyor olsa da biz yine de irademizle kontrole zorlayabilirsiniz.
</p>

<p>
Özetle DetectChanges ile sistemde yapılan değişiklikleri iradeli bir şekilde tekrardan kontrol etmiş ve Change Tracker mekanizmasındaki state'leri buna göre güncelle demiş oluyoruz. Bu birincisi.
</p>

<p>
İkincisi SaveChanges fonksiyonunu çağırdığımızda DetectChanges metodu da otomatik tetikleniyormuş.
</p>

<img src="../img/detectChanges.png">

<br>

## AutoDetectChangesEnabled Property'si Nedir?

<p>
Bu property, DetectChanges metodunu otomatik olarak tetiklenmesinin konfigürasyonunu sağlıyor. 
</p>

<p>
Normalde SaveChanges ve Entries fonksiyonları içerisinde DetectChanges otomatik olarak tetikleniyordu. İşte AutoDetectChangesEnabled property'sine gelip de biz false değerini verirsek artık SaveChanges fonksiyonlarının içerisinde DetectChanges fonksiyonu otomatik olarak tetiklenmeyecek.
</p>

<p>
Bu da neye yarayacak? Aşırı derecede Ef Core yapılanmasında bir optimizasyon yapacaksak ve özellikle de maliyet ve performans optimizasyonu yapacaksak bu property'i kullanabiliriz.  
</p>

<br>

## Entries Metodu Nedir?

<p>
Context'deki Entry metodunun koleksiyonel versiyonudur. Yani Entry ile tek bir entity nesnesi üzerindeki state'i bizlere verirken Entries fonksiyonu ise bunun çoğuludur, koleksiyonel hâlidir. Bütün takip edilen nesnelerle ilgili state bilgisini bizlere döndürür.
</p>

<p>
Change Tracker mekanizması tarafından izlenen her entity nesnesinin bilgisini EntityEntry türünden elde etmemizi sağlar ve belirli işlemler yapabilmemize olanak tanır. 
</p>

<p>
Entries metodu çalışmadan önce DetectChanges metodunu otomatik tetikler. Niye tetikler? Entries metodu Change Tracker üzerinde takip edilen ne kadar nesne varsa hepsini elde edecek ya, elde edebilmek için son kez bir DetectChanges'la durumu tetikliyor ve ondan sonra verilerin state'lerini elde ediyor. Bu durumda tıpkı SaveChanges'da olduğu gibi bir maliyettir. Buradaki maliyetten kaçınmak için AutoDetectChangesEnabled property'sine false değeri verilebilir.  
</p>

<br>

## AcceptAllChanges Metodu Nedir?
<p>
SaveChanges() veya SaveChanges(true) metodu tetiklendiğinde Ef Core her şeyin yolunda olduğunu varsayarak track ettiği verilerin takibini keser ve yeni değişikliklerin takip edilmesini bekler. Böyle bir durumda beklenmeyen bir durum / olası bir hata söz konusu olursa eğer Ef Core takip ettiği nesneleri bırakacağı için bir düzeltme söz konusu olmayacaktır.
</p>

<p>
Haliyle bu durumda devreye SaveChanges(false) ve AcceptAllChanges metotları devreye girecektir.
</p>

<p>
SaveChanges(false) metodu, Ef Core'a gerekli veri tabanı komutlarını yürütmesini söyler ancak gerektiğinde yeniden oynatılabilmesi için değişiklikleri beklemeye/nesneleri takip etmeye devam eder. Ta ki AcceptAllChanges metodunu irademizle çağırana kadar.
</p>

<p>
SaveChanges(false) ile işlemin başarılı olduğundan emin olursak AcceptAllChanges metodu ile nesnelerden takibi kesebiliriz.
</p>

<img src="../img/acceptAllChanges.png">

<br>

## HasChanges Metodu Nedir?
<p>
Takip edilen nesneler arasında değişiklik yapılanların olup olmadığınının bilgisini verir.
</p>

<p>
Arkaplanda DetectChanges metodunu tetikler.
</p>

<img src="../img/hasChanges.png">

<br>

## OriginalValues Property'si ve GetDatabaseValues Metodu Nedir? 
<p>
Eğer nesne üzerindeki değişiklikler veri tabanına yansıtılmadan evvel veri üzerindeki güncel değerleri elde etmek istiyorsak OriginalValues property'sini veyahut GetDatabaseValues metodunu kullanabiliriz.
</p>

<img src="../img/originalValues.png">

<br>

<p>
Görüldüğü üzere UrunAdi değerini "Silgi" olarak atamama rağmen, yapılan bu değişikliği veri tabanına yansıtmadığımız için orijinal değer olan "Urun 54" verisini alıyoruz.
</p>



