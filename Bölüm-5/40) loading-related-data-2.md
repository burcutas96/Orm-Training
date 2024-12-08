# Loading Related Data 

<br>

## Explicit Loading 
<p>
Oluşturulan sorguya eklenecek verilerin, şartlara bağlı bir şekilde ya da ihtiyaca istinaden yüklenmesini sağlayan bir yaklaşımdır. 
</p>

<img src="../img/explicit-loading.png" width="75%">

<br>

<p>
Örneğin yukarıdaki çalışmada öncelikle ilgili Employee verisini getiriyoruz daha sonrasında yazmış olduğumuz koşulun sağlanması durumunda ilişkili Orders verilerini listelemiş oluyoruz. 
</p>

<br>

## Reference()
<p>
Explicit loading sürecinde ilişkisel olarak sorguya eklenmek istenen tablonun navigation property'si tekil bir türdeyse bu tabloyu Reference() ile sorguya ekleyebiliriz.
</p>

<img src="../img/reference.png" width="75%">

<br>

## Collection()
<p>
Explicit loading sürecinde ilişkisel olarak sorguya eklenmek istenen tablonun navigation property'si çoğul yani koleksiyonel bir türdeyse bu tabloyu Collection() ile sorguya ekleyebiliriz.
</p>

<img src="../img/collection.png" width="75%">

<br>

## Collection'larda Aggregate Operatör Uygulamak
<img src="../img/collection-1.png" width="75%">

<br>

## Collection'larda Filtreleme Gerçekleştirmek
<img src="../img/collection-2.png" width="75%">











