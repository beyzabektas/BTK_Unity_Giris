# BTK | Unity İle Dijital Oyun Geliştirmeye Giriş
<div align="left">
<img src="https://github.com/beyzabektas/BTK_Unity_Giris/assets/91256847/abd91db7-5cf3-4e8c-baa5-a231db19da63"  width="400" height="200" />
<img src="https://github.com/beyzabektas/BTK_Unity_Giris/assets/91256847/dd4a26c2-f46b-4446-b51f-df9714c6063f"  width="400" height="200" />
</div>

# UNITY DERS NOTLARI
SampleScene* yanında çıkan yıldız sahnemde kaydedilmemiş değişiklikler olduğunun habercisidir.

## PREFABS KULLANIMI

Unity oyun motoru üzerinde sürekliliği olan objelerinizi Prefabs özelliği sayesinde hazır yapılar, şablonlar haline getirebiliriz. 
Prefabs haline getirdiğimiz objemizi istediğimiz gibi düzenleyerek oyunumuzun istediğimiz sahnesinde çağırarak kullanılabilir.

“Örneğin sürekli varyasyonları yapılan bir zombi oyununuzun olduğunu düşünün. Genelde bu tarz oyunlarda belirli tiplerde zombiler vardır ve sürekli olarak oyunun belirli bölümlerinde karşınıza çıkar. Siz her zombi için yeniden yapılandırarak kullanmanın ne kadar zor olduğunu düşünün. Bunun yerine prefabs ile bir hazır yapı oluşturup her ihtiyacınız olduğunda kolayca kullanabilirsiniz.”

“Project” menüsünde “Assets” klasörünün altına “Prefabs” isminde bir klasör oluşturuyoruz. Yazılı olmayan kurallara uymak için ilk harf büyük.Ve istediğimiz objeyi içerisine atıyoruz.

Objeyi prefab yaptığımızda sembolü mavi oluyor bu da prefabdan türediği anlamına geliyor.
Prefabta bir değişiklik yapıldığında üretilen tüm objelerde değişiklik olur.
Objeyi prefabtan çıkarmak için sağ tıkla unpack prefab diyerek ayırabiliriz.


## SPRITE EDITOR

Slice elimizdeki sprite'ı dilimlere böler.

Automatic = transparan ise
Type			Grid by cell size = hücre boyutuna göre dilimleme
Grid by cell count = hücre sayısına göre

Pixel size = x ve y'deki genişliğini pixel adedi ile belirler.

Offset = Hücrelerin x ve y düzlemindeki pixel adedinde kaydırılarak başlatılmasını sağlar.

Padding = Hücreler arasında bırakılacak mesafeyi ayarlar.


## RIGIDBODY 2D

Karakterimize fizik eklemek için Add Component diyerek Rigidbody 2D’yi seçiyoruz.

Body Type = karakterin nasıl bir davranış sergileyeceğini belirler.
o	Dynamic -> tüm fiziksel etkilere açıktır.
o	Kinematic -> dış kuvvetlere ve yer çekimine kapalıdır.Fakat hızı direk değiştirilerek hareket ettirilebilir.
o	Static -> asla hareket etmez.

Material = Fizik materyalleri konularak zıplama ve sürtünme özellikleri eklenebilir.

Simulated = fizik etkisi olup olmamasını belirler.

Use Auto Mass = fizik objesinin ağırlığını otomatik belirler.

Mass = ağırlığını belirler.

Linear Drag = Objenin hızının ortam sürtünmesinden azalmasını sağlar (örneğin suda ilerleyen bir kurşun gibi düşünebiliriz).Ne kadar yüksekse o kadar çabuk duracaktır.

Angular Drag = Dönmesini durdurur veya yavaşlatır.

Gravity Scale = Yer çekiminden ne kadar etkileneceğini belirler.

Collision Detection = Objelerin çakışması birbirinin içine geçmeye çalışmas durumunda izlenecek stratejiyi belirler.

Sleeping Mode = Uyku modunu düzenleyerek işlemden tasarruf sağlar.

Interpolate = Hareketinin ne kadar yumuşak geçişli olmasını belirler.

Constraints = Karakterin engellerde devrilmemesi için freze rotation seçilir.


## BOX COLLIDER

Platform görsel yani katı bir varlık olmadığı için karakter yerçekimine karşı düşer.Bunu katı yapmak için Box Collider 2D komponentini ekleyelim.

NOT:Oyun çalışırken değiştirilen ayarlar oyun bittiğinde eski haline döner.
Is Trigger işaretlendiğinde artık nesne katı cisim davranışı sergilemez.


## FRAME NEDİR?

Bir patlama videosunu ele alalım.Bu videoda aslında kareler bir araya gelerek aynı pozisyonda sırasıyla gösterildiklerinde akıcı bir görüntü ortaya çıkmaktadır.Birim zamanda gösterilen kare yani frame sayısı ne kadar yüksekse görüntü akışkanlığı da o kadar yüksektir.
Birim sürede frame sayısı düştükçe görüntünün akıcılığı da azalır.
Saniyede gösterilen kare sayısına FPS (Frame Per Second) denir.Dijital oyunlarda akıcı bir şekilde görebilmek için 60 FPS'in altına düşmemek gerekir.FPS değeri sabit bir değer değildir.
Oyunun oynatıldığı cihazın grafik kartının (ekran kartı) kalitesine ve oynatılan oyundaki grafiksel hesaplamaların zorluğuna göre anlık olarak değişkenlik gösterir. 

 
## METOTLAR

Update metodu (Güncelleme)
Oyunun başlamasından itibaren her bir frame için bir defa çalışır.
Görsel yenilemelerde kullanılır.Çünkü FPS saniyede 50'den yüksek olabilir daha akıcı göstermek isteyebiliriz.

Fix Update(Sabit Güncelleme)
Frame odaklı değil zaman odaklı çalışır.Her 1 saniyede 50 defa çalışır.
Fizik hesaplamalarında kullanılır çünkü FPS değişkenlik gösterir.
“Örneğin bir arabayı 1 metre ileri taşımak istendiğinde fixed update ile saniyede 50 defa çalıştırılarak 50 m gider.Update’de ise FPS'e göre ilerler.Arabanın nerde olacağını bilmemiz mümkün değildir.”

Start 
Script’in aktifleştirilmesinden itibaren çalışacak ilk Update metodundan önce çalıştırılır.

Awake (Uyanmak)
Nerdeyse Start ile aynıdır.Tek farkı script aktif olsun ya da olmasın sahnede oluştuğu anda çalıştırılmasıdır.Şartlar aynı olduğunda Awake ilk çalışır.

