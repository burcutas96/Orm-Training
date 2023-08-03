# Orm Nedir?

<p>
Yazılım uygulamalarında veriler, fiziksel olarak veri tabanlarında tutulmaktadır.
</p>
<p>
Haliyle yazılım ve veri tabanı arasında sürekli bir bağlantı üzerinden iletişim sağlanmaktadır ki yazılım dış dünyadan elde ettiği verileri veri tabanına işleyebilsin ya da veri tabanındaki verileri istediği zaman elde edebilsin.
</p>
<p>
İşte böyle bir durumda yazılım ile veri tabanı arasında biraz önce bahsedildiği üzere bir bağlantı kurularak tüm verisel grafik gerçekleştirilmektedir.
</p>
<p>
Yazılım bu bağlantı üzerinden veri tabanına anlayacağı dilden sorgular gönderir ve veri tabanı da bu sorgulara istinaden gerekli verisel işlemleri gerçekleştirir.
</p>
<p>
Bu sorgular genellikle sql dilindedir.
</p>
<p>
İşte bizleri Orm denen şeye götüren süreç tam da burada başlamaktadır. 
</p>
<br>

<img src="../img/sql-cumlecigi.png"/>
<p>
Dikkat ederseniz yukarıdaki kod içerisinde sql sorguları yazılmaktadır. Peki bu durum nelere sebep olmaktadır?
</p>
<p>
- Kodun içerisinde sql sorguları ve sql ile ilgili farklı cümleciklerin olması genel anlamda kodun kirlenmesine sebep olmaktadır.
</p>
<p>
Peki kodun kirlenmesinden kasıt nedir? Bir kod, metinsel ifadelere çok fazla boğuluyorsa ister istemez zaten kirlenmektedir. 
</p>
<p>
Bunun dışında yazdığımız metinsel ifadeler farklı bir dilin, yapının, servisin ya da veri tabanı gibi sunucuların anlayacağı bir semantikteyse, bu kod daha da kirlenmiş demektir.  
</p>
<p>
Çünkü yazdığımız kodda Employess ilerde bir gün Personeller olabilir. Bu yüzden bu kirli kod durmadan bir bağlayıcılığa sebep olacaktır. 
</p>
<br>
<p>
- Bunun dışında geliştiricinin sql hakkında olan bilgisinin endişe verici olmaması gerekmektedir. 
</p>
<p>
Çünkü bu yazılımda ilgili veri tabanıyla iletişim kurabilmem için kullanılan veri tabanının gramerine, cümlesine, semantiğine tam olarak hakim olmam gerekmektedir.
</p>
<p>
Çünkü bu veri tabanının anlayacağı semantiği manuel oluşturmam gerekiyor. 
</p>
<br>
<p>
- Ayrıca veri tabanına gönderilen sql neticesinde gelen datalar manuel parse edilmek zorunda bu da kodun sql'e olan bağımlılığını arttırdığı gibi yönetilebilirliğini de oldukça kısıtlamaktadır. Nasıl kısıtlamaktadır?
</p>
<p>
Örnek 1, yine yukarıdaki kodda yapılan sorgu neticesinde hangi kolonların geldiğini bilemeyebilirim. 
</p>
<p>
Örnek 2, gelen kolonların içerisinde FirstName ya da sadece Name gibi bir isimlendirme ile kolonun geldiğini bilemem. Yani kolonların isimlerini bilemem.
</p>
<p> 
Örnek 3, biz employee'de herhangi bir kolonu değiştirdiğimizde ve eğer bu değişen kolon, kodun içerisinde kullanılıyorsa gidip kodun içerisinde de o kolonla ilgili değişikliği yapmak zorundayım. Aksi taktirde run time da hata alırız. 
</p>
<br>
<p>
Yani uzun lafın kısası kodun içerisinde sql cümleleri yazmanın ve veri tabanından gelen sonuçların manuel bir şekilde parse edilmesinin büyük projelerde büyük problemler doğurabileceği aşikardır.
</p>
<br>

## Kod içerisinde sql yazmanın dezavantajları 
* <p>Kodun kirlenmesine sebep olacaktır.</p>
* <p>Geliştirme ve bakım maliyeti yüksek kod inşasına sebep olur.</p>
* <p>Veri tabanı bağımlılığı yaratır.</p>
* <p>Komplex sorguların manuel bir şekilde oluşturulması gerekir.</p>
* <p>Geliştirici açısından sql sorumluluğu beklenir. Sorgu sürecinde tablo, kolon vs. gibi bağımlılıklar olduğu gibi gelen datalarda da aynı bağımlılıklar söz konusu olacaktır.</p>
* <p>Veri tabanında olan değişikliklere uygun bir şekilde kodunda review edilmesi gerekmektedir.</p>
<p>
Örneğin; bir kolon adı ya da bir kolonun herhangi bir kuralı (constraint, validation vs.) değiştiğinde bu durumdan kodun da haberdar olması gerekmektedir. Bilinçli bir şekilde review yapılmalıdır. 
</p>

* <p>Kodu aşırı derecede veri tabanı seviyesine indirger. Bu durum tüm gelişmelerin veri tabanıyla uyumlu bir şekilde seyretmesi zorundalığını doğurur.</p>
* <p>Geliştirilen yazılım sürecinde tüm veri tabanı işlemleri, o an kullanılan programlama dili ve oop'nin nimetlerinden istifade etmeksizin icra edilir.</p>
* <p>Gün gelir veri tabanını değiştirmemiz gerekebilir. İşte böyle bir durumda tüm sql kodlarını yeni veri tabanına göre refactoring etmemiz gerekecektir.</p>
<br>

## Peki bu dezavantajlı durumdan nasıl kurtulabiliriz?
<p>Orm ile kurtulabiliriz. Peki Orm nedir?</p>
<p>Orm; yazılım ve veri tabanı arasındaki bağlantı üzerinden sorgular eşliğinde veri transferini oop nimetlerinden istifade ederek sağlayabileceği ve böylece kodun da, geliştiricinin de sql'e bağımlılığı olmaksızın hızlı ve kolayca operasyonları gerçekleştirebileceği bir yaklaşımdır.</p>
<p>Orm, Object Relational Mapping yani Nesne İlişkisel Eşleme şeklinde bir açılıma sahiptir.</p>
<p>
Orm; geliştirilen yazılım içerisinde oop yapısına uygun olmayan katı ve kompleks veri tabanı sorguları yerine veri tabanı objelerinin bir oop nesnesi gibi düşünülerek yazılım tarafından kullanılabilmesine olanak sağlayan bir yaklaşımdır.
</p>
<p>Bu yaklaşıma göre veri tabanı, yazılım tarafında birer nesneye karşılık gelmektedir. Böylece tüm veri tabanı süreçlerini kavramlarıyla rahatlıkla yönetebilir ve kodu sql'den arındırabiliriz.</p>
<img src="../img/orm-simulasyonu.png">

<br>

## Orm Avantajları

* <p>Veri tabanı bağımsızlığı sağlar.</p>
<p>Yani bundan sonra veri tabanında sorgulama yaparken veri tabanına uygun bir şekilde sql cümleciği yazmak zorunda değiliz. Çünkü orm, biz hangi veri tabanını kullanıyorsak o veri tabanına uygun bir şekilde sql cümleciğini, sorgusunu oluşturur.</p>

* <p>Kullanılan veri tabanına göre uygun sorgu oluşturulur. </p>
* <p>Oop nimetlerinden faydalanarak sql mantığı işlememizi sağlıyor.</p>
* <p>Geliştiricinin kullanılan veri tabanına dair sql yeteneklerinin olması beklenmez.</p>
* <p>Sorgular otomatik generate edileceğinden dolayı kodu sql bağımlılığından soyutlar.</p> 
<br>

<img src="../img/orm-karsilastirma.png">

<br>

## Neden Orm Kullanmalıyız?
<p>
Koda gömülü sorgular, veri tabanı değiştiğinde inanılmaz derecede maliyet getirir.
</p>
<p>
Eğer ki orm kullanırsak veri tabanından bağımsız veri tabanı işlemleri yapabiliriz. Bundan dolayı orm kullanmalıyız.
</p>
<p>
Orm; ileriye dönük, dönüştürülebilir, veri tabanı değişikliğine açık, bu değişikliği karşılayabilecek bir proje oluşturmamızı sağlar.
</p>
<p>
Yani yazılımı mümkün mertebe kullandığımız veri tabanından bağımsız bir şekilde inşa etmemiz gerekecektir. Bunun içinde orm yaklaşımını benimsememiz gerekecektir.
</p>
















