# Yaklaşımlar   
<p>
Ef Core veri tabanlarıyla iki farklı yaklaşımı baz alarak çalışmalar sergilemektedir.
</p>
<p>
Bu yaklaşımlar; Database First ve Code First olmak üzere iki tanedir.
</p>
<br>

## Yaklaşım Ne Demek?
<p>
Yaklaşım; dilden, platformdan, framework'ten her şeyden bağımsızdır. Bu bir stratejidir. Bu bir mantıktır. Sen orm yaklaşımını istediğin herhangi bir dilde, istediğin herhangi bir platformda uygulayabilirsin. Yani javada da, phpde de, pythonda da uygulayabilirsin. 
</p>
<p>
Yaklaşım bir konuyu, olguyu, yapıyı, inşayı, sorunu, çözümü ele alış bir başka deyişle ona bütünsel olarak bakış biçimidir.
</p>
<p>
Haliyle her yaklaşım bir davranışa özel subjektiftir / özneldir.
</p>
<p>
Ef Core, veri tabanı çalışmaları için veri tabanının önceden olup olmaması durumlarına göre farklı yaklaşımlar sunmaktadır. İşte bu durumlara göre farklı yaklaşımlar eşliğinde çözüm getirilmesi subjektif / öznel olmanın bir göstergesidir.
</p>
<br>

## Yaklaşımların Temel Amacı Nedir?
<p>
Önceki derslerde orm yapılanmasını ele alırken veri tabanını, oop nimetlerinden istifade ederek kod tarafında modellememizi sağlayan ve nesneler üzerinden sorgulama süreçlerini yöneterek sql'den bağımsız bir şekilde çalışmalar ortaya koyan pattern olduğundan bahsetmiştik.
</p>
<p>
İşte bu bilgiye istinaden, bir orm aracı olan ef core ile yapılacak olan çalışmalarda da hedef veri tabanının kod kısmına aktarılması gerekecektir. 
</p>
<p>
Lakin hedef veri tabanı bazen önceden oluşturulmuş bir veri tabanı olabileceği gibi bazen de daha yeni oluşturulacak bir veri tabanı da olabilmektedir.
</p>
<p>
Yani olan bir veri tabanını kod kısmında modellemek gayet gözle görülebilir bir durumken, hiç oluşturulmamış (yeni oluşturulacak olan) bir veri tabanını da kod kısmına modellemek gerekebilmektedir. 
</p>
<p>
İşte bu yaklaşımlar, veri tabanının önceden var olup olmaması durumlarına göre kod kısmında modellenme süreçlerinin hangi davranışla gerçekleştirileceğini belirleyecek olan tekniği bizlere sunmaktadır.
</p>
<br>

## Yaklaşımlar Nerede Başlar?
<p>
Geliştirilecek bir projede yaklaşımlar, o projenin veri tabanının var olup olmamasına göre şekillenmektedir demiştik.
</p>
<p>
Misal olarak, uzun zamandır devam eden ve veri tabanı doğal olarak mevcut olan bir projeye katıldığınızı varsayalım.
</p>
<p>
Ve sizlerden bu veri tabanı üzerinde Ef Core Orm aracı ile belirli işlemler yapmanızı bekliyorlar.
</p>
<p>
Böyle bir durumda projedeki veri tabanının var olmasından dolayı büyük ihtimalle Database First yaklaşımını tercih etmeniz gerekecektir. 
</p>
<p>
Lakin veri tabanı daha inşa edilmemiş bir projeye katılım gösteriyor olsaydınız bu durumda da ya Database First ya da Code First yaklaşımlarından birini tercih edebilirsiniz.
</p>
<p>
Yani buradan anlayacağınız, bir çalışmada hangi yaklaşımın kullanılacağı ve neye göre belirleneceği özünde temel birkaç hususun yanında birçok parametreyi değerlendirmeye bağlıdır.
</p>
<p>
Bunun için bu yaklaşımları tam teferruatlı bilmek ve değerlendirmek gerekir. 
</p>
<br>

## Database First Yaklaşımı
<p>
Ef Core ile çalışma yapılacak olan veri tabanı önceden oluşturulmuş ve içerisine tablolar yerleştirilerek belirli çalışmalar yapılmış ise bu veri tabanını kod kısmında modellemek için en doğru yaklaşım Database First yaklaşımıdır.
</p>
<p>
Database First, var olan veri tabanını tersine mühendislik ile analiz edip otomatik olarak kod kısmında modelleyen bir yaklaşımdır.
</p>
<p>
Yani şöyle ki, hedef veri tabanının belirli talimatlar aracılığıyla otomatik olarak kod kısmında oop nimetleri eşliğinde modellenmesidir.
</p>
<p>
Var olan veri tabanını kod tarafında modelleyebilmek için ileride Scaffold adını vereceğimiz bir talimatı vermemiz gerekecektir.
</p>
<br>

## Database First Yaklaşımının Avantajları ve Dezavantajları

### Avantajları
* <p>Hazır veri tabanlarını hızlı bir şekilde modelleyebilmemizi sağlar.</p>
* <p>Veri tabanında süreçte olan değişiklikleri de hızlıca koda aktarmamızı sağlar.</p>
* <p>Sql server, Oracle, PostgreSql vs. gibi Ef Core tarafından desteklenen tüm veri tabanlarında kullanılabilir.</p>
* <p>Veri tabanından bağımsız olarak tüm modellemeyi oop nimetleri karşılığında sağlamaktadır.</p>
<br>

### Dezavantajları
* <p>Kod veri tabanına göre şekilleneceği / modelleneceği için yönetim, veri tabanı tarafından sağlanır. Haliyle veri tabanı bilgisi gerektirir.</p>
* <p>Değişiklikler veri tabanı kısmında olacağı için geliştirici tarafından sürekli bir kontrol / güncelleme davranışı sergilenmelidir.</p>
<br>

## Database First Yaklaşımı Hangi Durumlarda Tercih Edilmelidir?
<p>
- Önceden oluşturulmuş, hali hazırda veri tabanı var olan uygulamalarda,
</p>
<p>
- Uzun süreli devam eden uygulamalarda (özellikle devlet gibi köklü kurumsal projelerin veri tabanlarını modellerken)
</p>
<p>
- Veri tabanı yönetimine, geliştirme süreçlerine ve tasarımına dair herhangi bir kararın geliştiriciler tarafından verilmediği durumlarda tercih edilmelidir.
</p>
<br><br>

## Code First Yaklaşımı
<p>
Ef Core ile çalışma yapılacak olan veri tabanı önceden oluşturulmamış ise bu veri tabanını kod kısmında modelleyerek bu modele uygun veri tabanını sunucuda oluşturan (migration) yaklaşımdır.
</p>
<p>
Bu yaklaşımda veri tabanı önce kodla tasarlanır sonra veri tabanı sunucusuna gönderilerek veri tabanı oluşturulur.
</p>
<p>
Database First yaklaşımının tam tersi davranışı gerektirir.
</p>
<p>
Kod kısmında tasarlanan veri tabanı modeli, veri tabanı sunucusuna gönderildiğinde (ki bu işleme migrate diyeceğiz) nihai olarak tasarlanan modele karşılık veri tabanı oluşturulmuş olacaktır. 
</p>
<br>

## Code First Yaklaşımının Avantajları ve Dezavantajları
### Avantajları
* <p>Kod üzerinden veri tabanını modellememizi sağlar.</p>
* <p>Veri tabanına dokunmaksızın kod üzerinden gerekli düzenlemeleri ve güncellemeleri hızlıca yapabilmemizi sağlar.</p>
* <p>Sql server, Oracle, PostgreSql vs. gibi Ef Core tarafından desteklenen tüm veri tabanlarında kullanılabilir.</p>
* <p>Veri tabanından bağımsız olarak tüm modellemeyi oop nimetleri karşılığında sağlamaktadır.</p>
* <p>Koddaki ihtiyaca dönük veri tabanı modelleneceği ve nihai olarak bu modele göre inşa edileceği için yönetim, geliştirici tarafından sağlanmaktadır. Haliyle herhangi bir veri tabanı bilgisine gerek duyulmamaktadır.</p>
* <p>Değişiklikler kod kısmından yapılacağı için geliştirici tarafından sürekli bir kontrol / güncelleme davranışı sergilenmeyecektir.</p>
* <p>Veri tabanı modeli kod üzerinden yapıldığı için istenilen sunucuda (yani Sql server, Oracle gibi veri tabanlarında) anında ilgili modeldeki veri tabanı elde edilebilir.</p>
<br>

### Dezavantajları
* <p>Üretilecek veri tabanının tasarımı ve stratejisi geliştirici sorumluluğundadır.</p>
<br>

## Code First Yaklaşımı Hangi Durumlarda Tercih Edilmelidir?
<p>
- Veri tabanı bilgisine ihtiyaç duyulmayan,
</p>
<p>
- Veri tabanı tasarımının kod üzerinden yapılarak geliştirici tarafından sorumluluğunun üstlenilebileceği
</p>
<p>
- Veri tabanı yönetiminin kod üzerinden sağlanacağı durumlarda tercih edilebilir.
</p>
<br>

## Code First & Database First Ekstra
<p>
Bu iki yaklaşımın kullanım alanlarının radikal olarak ayrıldığı tek nokta ilgili veri tabanının önceden oluşturulmuş olup olmamasıdır. Eğer önceden oluşturulmuş ise Database First yaklaşımı elzemdir.
</p>
<p>
Yok eğer önceden oluşturulmamış ise Code First yaklaşımını tecih edebilceğimiz gibi önce sunucuda veri tabanını manuel tasarlayıp sonrasında da Database First yaklaşımıyla kod kısmında inşa edebiliriz.
</p>
<p>
İşte burada bir opsiyonellik söz konusudur.
</p>
<br>

<h3> Database First --> Önce veri tabanı, sonra kod</h3>
<h3> Code First --> Önce kod, sonra veri tabanı</h3>




