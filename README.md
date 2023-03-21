# Bu alan güncellenmeye devam etmektedir.
<br>
<div align="center">
<img src="https://user-images.githubusercontent.com/33163650/209447604-e6777409-d517-45a7-abc6-4a24eb620966.png" width="160" height="160">
</div>

<h1 align="center"> Eye Mouth Mouse Controller </h1>
<p align="justify">
Projemizin amacı kullanım engeli olanların mouse kullanmalarını hedeflemek. Eye Mouse Controller projesi kullanım engeli olanların fareyi kullanmasını amaçlamıştır. Bu amaç doğrultusunda yüzün bazı noktaları baz alınıp bu noktalar ile mouse kontrolü, Click eventi, DoubleClick özellikleri başarıyla yapılmıştır.
</p>

*  [:fire: Geliştirici](#fire-geliştirici)
*  [:hash: Amaç](#hash-amaç)
*  [:hash: Model Mimarisine Genel Bakış](#hash-model-mimarisine-genel-bakış)
*  [:hash: Çalışma Mantığı Nedir?](#hash-çalışma-mantığı-nedir)
*  [:hash: Sonuç ve Tartışma](#hash-sonuç-ve-tartışma)

# :fire: Geliştirici
| Adı Soyadı | 
| :--- | 
| [Burak ÖZDEMİRTAŞ](https://github.com/burakozdemirtas) |

# :hash: Amaç
<p align="justify">
Manuel kontrol gerektiren bilgisayar gibi cihazlarda, fiziksel temasta zorlanan, fiziksel engelli, Multipl Skleroz(MS), Amiyotrofik Lateral Skleroz (ALS), boyundan aşağısı felçli veya kısmı felçli hasta bireylerin fare kullanımı zordur. Bu proje bireylerin fare erişimini kolaylaştırmayı hedeflemiştir. Bu çalışmada bireylerin kafa, göz ve ağız hareketleri ile fareyi kontrol edebilecekleri bir sistem geliştirilmiştir. Sistem bireyin yüz hareketlerini kameradan almaktadır. Sağ gözün dairesel dört noktasını algılayıp, fare kontrolü sağlamaktadır. Sol gözün göz kapakları aralıklarındaki fark ile tıklama yapmaktadır. Dudaklar arasındaki fark ile çift tıklama yapmaktadır. Bu sistem manuel kontrol gerektiren cihazlarda fare erişimini kolaylaştırmıştır. Deneysel olarak tasarlanan bu sistem tatmin edici sonuçlar ortaya çıkarmıştır. 
  </p>
</br>
</br>
<div align="center">
<img src="https://user-images.githubusercontent.com/33163650/226713833-09a210e1-22e8-4fcc-92ba-7b344ab18c0f.png" width="" height="250" >
</div>

# :hash: Model Mimarisine Genel Bakış
<p align="justify">
  Yüz tanıma sistemi, bir görüntü algılama cihazı (örneğin, bir kamera) aracılığıyla bir görüntü alır. Bu görüntü, bir görüntü işleme modülü tarafından işlenir. Bu modül, görüntüdeki yüz noktalarını (gözler, ağız ve diğer noktalar) tespit eder ve bu noktalar için etiketler oluşturur. Oluşturulan etiketler, sistem tarafından önceden eğitilmiş bir yüz tanıma modeline göre oluşturulmuştur ve bu model, yüzün birçok noktalarını tespit eder. Bu noktaların verdiği değerler ile ekranın x ve y eksenlerine göre işlem yaptırılıp fare kontrol, tıklama, çift tıklama işlemleri yapılır.  
</br> </br>
Göz ile fare kontrolü, bilgisayar kullanımını engel olan insanlar için alternatif bir yöntem olabilir. Bu yöntem sayesinde, fiziksel olarak elle tutulan fare cihazı kullanılmadan da bilgisayar kontrol edilebilir. Göz ile fare kontrolü yöntemleri, genellikle görüntü işleme yöntemleri kullanılarak yapılır ve bu yöntemler sayesinde, göz hareketleri takip edilerek fare hareketleri ve tıklama işlemleri yapılabilir. Bu yöntemlerin bazıları, yüz tanıma ve nesne tespiti yöntemlerini kullanarak çalışırken, bazıları ise göz izleme teknolojisi kullanarak çalışmaktadır. Bu yöntemler arasında, "EyeTribe", "Tobii EyeX" ve "EyeControl" gibi çeşitli ürünler mevcuttur. Bu yöntemlerin etkili olduğu ve kullanımının kolay olduğu gösterilmiştir, ancak bazı kullanıcılar için bu yöntemlerin doğru çalışması için gözlerin doğru pozisyonlarda olması gerektiği de belirtilmiştir. 
</br></br>
Bu projede gözlerin doğru noktada olmasına gerek yoktur. Gözlerin çevre noktaları hedef alındığından göz konumlarının önemi yoktur.  Şaşılık (strabismus), gözlerin eşit olmayan şekilde hareket etmesi durumudur. Bu durumda, bir göz düzgün bir şekilde hedefe odaklanırken, diğer göz hedefe odaklanamayabilir veya farklı bir yöne bakabilir. Bu durum nedeniyle, gözler arasında görme bozuklukları ortaya çıkabilir ve gözler arasındaki denge bozulabilir. Projemiz bu durumda çalışmakta, gözlerin konumunu baz almamaktadır. Gözlükler, görme bozuklukları olan insanlar için kullanılan bir optik alettir. Bu aletler sayesinde, görme bozuklukları olan insanlar düzgün bir şekilde görebilirler ve görme bozukluklarının neden olduğu sıkıntılar azaltılır. Projemiz gözlük kullanılmasından etkilenmemektedir. Sonuç olarak projemiz çeşitli göz hastalıklarından etkilenmemektedir.

  </p>
  
  
# :hash: Çalışma Mantığı Nedir?
<p align="justify">
Bu proje Python programlama dilinde yazılmıştır. Kütüphane olarak OpenCv(Open Source Computer Vision), Mediapipe[4], Pyautogui kütüphaneleri kullanılmıştır. 
OpenCv kütüphanesi ile Görüntü işleme yapılıp, bilgisayar kamerası tanıtılmıştır. Kameranın yansıma özelliği kaldırılmıştır. OpenCv kütüphanesi ile renkli görüntü alma, yüzdeki belirli noktaların daireler halinde çizdirilip kullanıcıya gösterimi sağlanmıştır. Projeden çıkma komutu OpenCv kütüphanesi ile yapılmıştır.
Mediapipe[4]  kütüphanesi[4] görüntü ve ses işleme, mobil uygulamalar ve gerçek zamanlı çözümler geliştirme gibi alanlarda kullanılmaktadır. Mediapipe kütüphanesinin facemesh alanı yüz tanımlama için kullanılmıştır. Yüzün dört yüz altmış sekiz noktasını tanımlamaktadır. Mediapipe ile sol göz üst ve alt kapağı, sağ göz bebeğinin yuvarlağının x ve y ekseninde toplam dört noktası, alt ve üst dudak noktaları belirlenmiştir.
Pyautogui, Python dilinde yazılmış bir otomatik kontrol kütüphanesidir. Pyautogui, bilgisayar otomatik kontrolü sağlamak için kullanılır. Projede Pyautogui fare hızının arttırılıp azaltılması, fare hareketlendirilmesi, tıklama işlemi, çift tıklama işleminde kullanılan bir kütüphanedir.
OpenCv, Mediapipe ve Pyautogui kütüphaneleri kullanılarak, sağ gözün bebeğinin x ve y ekseninde son noktaları seçilerek, dört nokta belirlenmiştir. Bu dört nokta ile farenin x ve y eksenin de hareketlenmesi sağlanmıştır.
OpenCv, Mediapipe ve Pyautogui kütüphaneleri kullanılarak, sol gözün üst ve alt kapağı tespit edilmiştir. Tespit yapılan noktaların değerlerinin birbirlerine yaklaşımını çıkartıp, çıkan değer ile normal göz kırpmadan farklı bir aralığına ininceye kadar hesaplamalar yapılmıştır. Bu hesaplamalar sonucunda 0.005 değerine ulaşılınca tıklama işlemi başarı ile yapılmıştır.
OpenCv, Mediapipe ve Pyautogui kütüphaneleri kullanılarak, üst dudak ve alt dudak bölgeleri tespit edilmiştir. Tespit yapılan noktaların değerlerinin birbirinden uzaklaşması toplanmıştır. Çıkan değer sonucunda 0.08 değerine ulaşınca çift tıklama işlemi yapılmıştır.
  </p>


  # :hash: Sonuç ve Tartışma
 <p align="justify"> 
  Proje sağ gözün x ve y ekseninden göz bebeğinin başlangıç ve bitiş kısımlarından dairesel şekilde dört nokta belirlenmiştir. Bu noktalar ile fare hareketlendirilmesi sağlanmıştır. Sol gözün üst ve alt kapağından noktalar belirlenip, bu noktaların bir birine yaklaşım değerleri ölçülmüştür. Bu değerler 0.005 değerinden küçük ise tıklama işlemi gerçekleştirilmiştir. Dudaklarımızın üst dudak ve alt dudak orta noktaları belirlenmiştir. Bu noktaların birbirinden uzaklaşma değerleri ölçülmüş, bu değerler y ekseninde birbirinden çıkarılmıştır. Çıkarılan bu değerler 0.08 değerinden büyükse çift tıklama işlemi gerçekleştirilmiştir.
    </p>
