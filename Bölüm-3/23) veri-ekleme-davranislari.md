## One to One İlişkisinde Veri Ekleme

### 1. Yöntem: Principal Entity Üzerinden Dependent Entity Verisi Ekleme

<img src="../img/one-to-one-veri-ekleme.png">

<br>

<p>
Person nesnesini kaydettikten sonra person_id'yi alıp Address nesnesine bu person_id'yi vermek yerine ve her ikisini de ayrı ayrı AddAsync metotları ile kaydetmek yerine direkt person nesnesini oluştururken Address bilgilerini de vererek her iki kaydı oluşturabiliriz.
</p>

<br>

### 2. Yöntem: Dependent Entity Üzerinden Principal Entity Verisi Ekleme

<img src="../img/one-to-one-veri-ekleme-1.png">

<br>

<p>
Aynı şekilde Address nesnesini oluştururken Person nesnesini de ekleyebiliriz.
</p>

<br>

<b> 
Peki bu iki yöntem arasındaki temel fark ne? 
</b> 

<p> 
Eğer ki principal entity üzerinden veri ekleme gerçekleştiriliyorsa dependent entity nesnesi verilmek zorunda değildir. Amma velakin, dependent entity üzerinden ekleme gerçekleştiriliyorsa burada principal entity'nin nesnesine ihtiyacımız vardır.
</p>

<br>

## One to Many İlişkisinde Veri Ekleme

### 1. Yöntem: Principal Entity Üzerinden Dependent Entity Verisi Ekleme

<b>
Nesne Referansı Üzerinden Ekleme
</b>

<br>

<img src="../img/one-to-many-veri-ekleme.png">

<br>

<p>
Şimdi yukarıda blog nesnesi üzerinden Posts referansına erişiyoruz fakat bu Posts referansı null'sa bu referans üzerinden herhangi bir member'a erişmeye çalışırsak NullReferenceException hatasına sebebiyet verir.
</p>

<p>
Haliyle Posts nesnesine erişirken kesinlikle Posts'un null olmadığından emin olmalıyız. İşte bundan emin olabilmek için Ef Core çalışmalarında bu koleksiyonel navigation property'leri, ilgili entity'nin constructor'ında new'liyoruz. Tıpkı aşağıda olduğu gibi...
</p>

<img src="../img/one-to-many-veri-ekleme-1.png">

<br>

<b>
Peki aklımıza şöyle bir soru gelebilir: Biz Posts'u new'lerken neden HashSet'i kullandık da List'i veya ArrayList'i kullanmadık?
</b>

<p>
Biz bunların üçünü de kullanabiliriz. Ancak burada HashSet kullanmayı tercih ediyoruz. Çünkü HashSet hem unique bir yapılanmaya sahiptir hem de List'e nazaran daha yüksek performansta çalışmaktadır.
</p>

<br>

<b>
Object Initializer Üzerinden Ekleme
</b>

<br>
<br>

<img src="../img/one-to-many-veri-ekleme-2.png">

<br>

<p>
Bu yöntemde ilgili entity'nin constructor'ında new'leme işlemini yapmamıza gerek yok çünkü verileri eklerken zaten new'leme işlemini yapıyoruz.
</p>

<br>

### 2. Yöntem: Dependent Entity Üzerinden Principal Entity Verisi Ekleme

<p>
Bu ikinci yöntemi hiçbir yerde kullanmayacağız. Ama yanlış yapabileceğimiz şeyleri de görmekte fayda olduğu için bunu da inceleyeceğiz.
</p>

<p>
Bire çok ilişki yapılanmasında dependent entity üzerinden principal entity verisini eklemek bire çok davranışına aykırıdır. O yüzden bu yöntemi kullanmamalıyız. 
</p>

<img src="../img/one-to-many-veri-ekleme-3.png">

<br>

<p>
Yukarıda da görüldüğü üzere bire çok ilişki yapılanmasında dependent entity'den (Post) başlayıp ardından principal entity'i (Blog) eklersek sadece bir tane dependent entity eklemiş oluruz. Yani sanki birebir bir ilişki kuruyormuşuz gibi bir durum ortaya çıkacaktır. Çünkü dependent entity (Post) verisinden birden fazla oluşturup bunların içerisine bir Blog verisini ekleyemeyiz. Bu nedenle de birinci yöntemi kullanmak bizim için daha sağlıklı olacaktır.
</p>

<br>

### 3. Yöntem: Foreign Key Kolonu Üzerinden Principal Entity Verisi Ekleme

<p>
Aşağıdaki gibi, kod kısmında bir foreign key property'miz varsa bu üçüncü yöntemi de kullanabiliriz.    
</p>

<img src="../img/one-to-many-veri-ekleme-4.png">

<br>

<p>
Post nesnemizi oluştururken foreign key olan BlogId property'sine 1 değerini vererek bu yöntemi uygulamış oluyoruz.
</p>

<br>

## Many to Many İlişkisinde Veri Ekleme

### 1. Yöntem:

<p>
Birinci yöntem; çoka çok ilişkinin default convention ile tasarlanması durumunda kullanılan bir yöntemdir. Yani cross table; manuel olarak kodlama kısmında oluşturulmamışsa, sadece principal entityler üzerinden çoka çok ilişki sağlanmışsa bu yöntemi kullanabiliriz.
</p>

<br>

<img src="../img/many-to-many-veri-ekleme-1.jpg">

<br>

<p>
Aşağıda da görüldüğü üzere navigation property üzerinden Authors nesnelerini ekleyebiliyoruz.
</p>

<img src="../img/many-to-many-veri-ekleme-2.png">

<br>

### 2. Yöntem:

<p>
İkinci yöntem; çoka çok ilişkinin fluent api ile tasarlanması durumunda kullanılan bir yöntemdir. Yani cross table'ın manuel olarak kod kısmında oluşturulması durumunda kullanılabilecek olan bir yöntemdir.
</p>

<img src="../img/many-to-many-veri-ekleme-3.png">

<br>

<p>
Bu yöntemde veri ekleme işlemini aşağıdaki gibi yapabiliriz. Author nesnesi içerisindeki Books property'si, 'BookAuthor' tipinde koleksiyonel bir yapılanma olduğu için Books verilerini bu şekilde ekledik.
</p>

<img src="../img/many-to-many-veri-ekleme-4.png">



