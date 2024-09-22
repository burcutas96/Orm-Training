# One to One İlişkisinde Veri Güncelleme

### 1. Durum: Esas tablodaki veriye bağımlı veriyi güncelleme

<img src="../img/data-update-1.png">

<br>

<p>
FirstOrDefault() metodu ile ilgili person nesnesini elde ediyoruz. Ve bu Person nesnesinin Address verisini silebilmek için Include() metodu ile Address verisine ulaşıyoruz.
</p>

<p>
Ulaştığımız bu Address verisini direkt olarak Update() metoduyla güncelleyemiyoruz. Çünkü aşağıda da görüldüğü üzere 'Id' kolonu hem foreign key hem de primary key görevi görüyor. Primary key görevi gördüğü için bu alanı güncellememiz mümkün değil.
</p>

<img src="../img/data-update-2.png">

<br>

<p>
Bu yüzden öncelikle Remove() metoduyla person'ın Address'ini siliyoruz. Daha sonrasında change tracker mekanizmasıyla takip edilen person nesnesine yeni Address verisini ekleyip SaveChanges() ile yapılan değişiklikleri veri tabanına yansıtıyoruz.
</p>

<br>

### 2. Durum: Bağımlı verinin ilişkisel olduğu ana veriyi güncelleme

<p>
Yine yukarıdaki mantıkta olduğu gibi biz Address tablosundaki 'Id' kolonunu direkt olarak güncelleyemediğimiz için öncelikle bağımlı olan veriyi silip daha sonra istediğimiz veri ile ilişkilendirebiliyoruz.
</p>

<img src="../img/data-update-3.png">

<br>
<br>

# One to Many İlişkisinde Veri Güncelleme

### 1. Durum: Esas tablodaki veriye bağımlı veriyi güncelleme

<p>
Her şeyden önce hedef veriyi (Blog) ve buna bağlı olan Posts'ları elde ediyoruz. Daha sonrasında Remove() metoduyla istediğimiz verileri silip yine ekleme işlemini gerçekleştirerek güncelleme işlemini tamamlamış oluyoruz.  
</p>

<img src="../img/data-update-4.png">

<br>

<p>
Aşağıda da görüldüğü üzere güncelleme yapmak için direkt Update() metodunu kullanamadığımız için önce ilgili verileri silip daha sonrasında ekleme işlemi yaparak verileri güncellemiş oluyoruz.
</p>

<img src="../img/data-update-6.png">

<br>

<p>
Bu arada eğer Posts verilerini Include() etmemiş olsaydık, hata alırdık. Çünkü Posts, koleksiyonel bir yapılanma. Şimdi koleksiyonel yapılanmada bir veriyi Add fonksiyonuyla ekleyebilmek için bu koleksiyonel yapılanmanın null gelmemesi gerekiyor. İşte bunun null olarak gelmemesi için aşağıda da görüldüğü üzere Blog constructor'ında Posts'un new'lenmiş olması gerekiyor. 
</p>

<img src="../img/data-update-5.png">

<br>

<p>
Ama zaten biz bu işlemi yapsak dahi veri tabanındaki ilgili Posts'ları silebilmek için Include() etmemiz gerektiği için bu işlemi yapmamıza gerek yok.
</p>

<br>

### 2. Durum: Bağımlı verilerin ilişkisel olduğu ana veriyi güncelleme

<p>
Bağımlı veriyi (Post) elde ediyoruz. Akabinde bu Post'a yeni Blog verisini atıyoruz.  
</p>

<p>
Yeni bir Blog oluşturup da atayabiliriz;
</p>

<img src="../img/data-update-7.png">

<br>

<p>
Var olan bir Blog'u da atayabiliriz;
</p>

<img src="../img/data-update-8.png">

<br>

# Many to Many İlişkisinde Veri Güncelleme

<p>
Elimizde aşağıdaki gibi many to many ilişkisine sahip tablolarımız ve verileri olduğunu düşünelim.
</p>

<img src="../img/data-update-9.png">

<br>

### 1. Örnek:

<p>
İlk örneğimizde 1. Kitap'ı 3. Yazar'la ilişkilendirerek 1. Kitap'ın verilerini güncellemiş olalım.
</p>

<img src="../img/data-update-10.png">

<br>

### 2. Örnek:

<p>
İkinci örneğimizde ise 3. Yazar'ın sadece 1 id'sine sahip olan kitapla ilişkisi olsun diğerleriyle ilişkisini koparalım.
</p>

<img src="../img/data-update-11.png">



