# Kalıtımsal Durumlarda Entity Framework Core Davranışları

<br>

## Kalıtımsal Durumlardan Kastedilen Nedir?
<p>
Örneğin aşağıdaki gibi bir durumda ef core nasıl bir davranış sergilicek, bunun üzerine konuşacağız.
</p>

<img src="../img/kalitimsal-durumda-ef-core.png" width="60%">

<br>

## 1) Table Per Hierarchy (TPH)
<p>
Bu davranış modelinde, kalıtımsal hiyerarşideki tüm entity'ler için tek bir tablo oluşturulmakta ve drived olan tablolar arasındaki ayrım için bir discriminator kolonu kullanılmaktadır.
</p>

<img src="../img/kalitimsal-durumda-ef-core-1.png" width="45%">

<br>  
 
<p>
Yani yukarıdaki modelleri migrate ettiğimizde, elimizde aşağıdaki gibi bir tablo olacak.
</p>

<img src="../img/kalitimsal-durumda-ef-core-2.png" width="45%">

<br>

## Table Per Type (TPT)
<p>
Bu davranış modelinde, kalıtımsal hiyerarşideki her sınıfa karşılık bir tablo oluşturulmakta ve oluşturulan bu tablolar ile bir üst sınıf arasında birebir ilişki sağlanmaktadır.
</p>

<img src="../img/kalitimsal-durumda-ef-core-1.png" width="45%">

<br>

<p>
Yani yukarıdaki modelleri migrate ettiğimizde, elimizde aşağıdaki gibi bir tablo olacak.
</p>

<img src="../img/kalitimsal-durumda-ef-core-3.png" width="45%">

<br>

## Table Per Concrete Type (TPC)
<p>
Bu davranış modelinde, kalıtımsal hiyerarşideki concrete (somut) sınıflara karşılık birer tablo oluşturulmakta ve abstract yapılanmaların member'ları bu tablolara eklemektedir.
</p> 

<img src="../img/kalitimsal-durumda-ef-core-4.png" width="45%">

<br>

<p>
Yani yukarıdaki modelleri migrate ettiğimizde, elimizde aşağıdaki gibi bir tablo olacak.
</p>

<img src="../img/kalitimsal-durumda-ef-core-5.png" width="65%">









