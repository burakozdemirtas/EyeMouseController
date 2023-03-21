# Bu alan güncellenmeye devam etmektedir.
<br>
<div align="center">
<img src="https://user-images.githubusercontent.com/33163650/209447604-e6777409-d517-45a7-abc6-4a24eb620966.png" width="160" height="160">
</div>

<h1 align="center"> Eye Mouse Controller </h1>
<p align="justify">
Projemizin amacı kullanım engeli olanların mouse kullanmalarını hedeflemek. Eye Mouse Controller projesi kullanım engeli olanların fareyi kullanmasını amaçlamıştır. Bu amaç doğrultusunda yüzün bazı noktaları baz alınıp bu noktalar ile mouse kontrolü, Click eventi, DoubleClick özellikleri başarıyla yapılmıştır.
</p>

* [:fire: Geliştiriciler](#fire-geliştiriciler)
* :hash: Çalışma Mantığı Nedir?

# :fire: Geliştirici
| Adı Soyadı | 
| :--- | 
| [Burak ÖZDEMİRTAŞ](https://github.com/burakozdemirtas) |

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
