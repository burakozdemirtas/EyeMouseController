<div align="center">
<img src="https://user-images.githubusercontent.com/33163650/209447604-e6777409-d517-45a7-abc6-4a24eb620966.png" width="160" height="160">
</div>

<h1 align="center"> Eye Mouth Mouse Controller </h1>
<p align="justify">
Projemizin amacı kullanım engeli olanların mouse kullanmalarını hedeflemek. Eye Mouse Controller projesi kullanım engeli olanların fareyi kullanmasını amaçlamıştır. Bu amaç doğrultusunda yüzün bazı noktaları baz alınıp bu noktalar ile mouse kontrolü, Click eventi, DoubleClick özellikleri başarıyla yapılmıştır.
  
Our project aims to enable individuals with disabilities to use a mouse. The Eye Mouse Controller project is designed to facilitate mouse usage for those with motor impairments. In line with this objective, certain points on the face are taken into consideration to achieve successful mouse control, click events, and double-click functionality.
</p>

*  [:fire: Geliştirici / Developer](#fire-geliştirici-developer)
*  [:hash: Amaç / intended](#hash-amaç-intended)
*  [:hash: Model Mimarisine Genel Bakış / Model Architecture Overview](#hash-model-mimarisine-genel-bakış-model-architecture-overview)
*  [:hash: Çalışma Mantığı Nedir? / what is the working logic?](#hash-çalışma-mantığı-nedir-what-is-the-working-logic)
*  [:hash: Sonuç ve Tartışma / Conclusion and Discussion](#hash-sonuç-ve-tartışma-conclusion-and-discussion)
*  [:hash: Ekran Görüntüleri / Screenshots](#hash-ekran-görüntüleri-screenshots)

# :fire: Geliştirici/ Developer
| Adı Soyadı / Name Surname| 
| :--- | 
| [Burak ÖZDEMİRTAŞ](https://github.com/burakozdemirtas) |

# :hash: Amaç/ intended
<p align="justify">
Manuel kontrol gerektiren bilgisayar gibi cihazlarda, fiziksel temasta zorlanan, fiziksel engelli, Multipl Skleroz(MS), Amiyotrofik Lateral Skleroz (ALS), boyundan aşağısı felçli veya kısmı felçli hasta bireylerin fare kullanımı zordur. Bu proje bireylerin fare erişimini kolaylaştırmayı hedeflemiştir. Bu çalışmada bireylerin kafa, göz ve ağız hareketleri ile fareyi kontrol edebilecekleri bir sistem geliştirilmiştir. Sistem bireyin yüz hareketlerini kameradan almaktadır. Sağ gözün dairesel dört noktasını algılayıp, fare kontrolü sağlamaktadır. Sol gözün göz kapakları aralıklarındaki fark ile tıklama yapmaktadır. Dudaklar arasındaki fark ile çift tıklama yapmaktadır. Bu sistem manuel kontrol gerektiren cihazlarda fare erişimini kolaylaştırmıştır. Deneysel olarak tasarlanan bu sistem tatmin edici sonuçlar ortaya çıkarmıştır. 
<hr>
Individuals with physical disabilities such as Multiple Sclerosis (MS), Amyotrophic Lateral Sclerosis (ALS), paralysis below the neck, or partial paralysis often struggle with using a mouse on devices that require manual control, such as computers. This project aimed to facilitate mouse accessibility for these individuals. In this study, a system was developed that allows individuals to control the mouse using their head, eye, and mouth movements. The system captures the individual's facial movements using a camera. It detects four circular points in the right eye to enable mouse control. Clicking is achieved by detecting differences in the opening of the eyelids in the left eye, while double-clicking is performed by detecting differences between the lips. This system has significantly improved mouse accessibility on devices that require manual control. The experimental implementation of this system has yielded satisfactory results.
  </p>
</br>
</br>
<div align="center">
<img src="https://user-images.githubusercontent.com/33163650/226713833-09a210e1-22e8-4fcc-92ba-7b344ab18c0f.png" width="" height="250" >
</div>

# :hash: Model Mimarisine Genel Bakış/ Model Architecture Overview
<p align="justify">
  Yüz tanıma sistemi, bir görüntü algılama cihazı (örneğin, bir kamera) aracılığıyla bir görüntü alır. Bu görüntü, bir görüntü işleme modülü tarafından işlenir. Bu modül, görüntüdeki yüz noktalarını (gözler, ağız ve diğer noktalar) tespit eder ve bu noktalar için etiketler oluşturur. Oluşturulan etiketler, sistem tarafından önceden eğitilmiş bir yüz tanıma modeline göre oluşturulmuştur ve bu model, yüzün birçok noktalarını tespit eder. Bu noktaların verdiği değerler ile ekranın x ve y eksenlerine göre işlem yaptırılıp fare kontrol, tıklama, çift tıklama işlemleri yapılır.  
</br> </br>
Göz ile fare kontrolü, bilgisayar kullanımını engel olan insanlar için alternatif bir yöntem olabilir. Bu yöntem sayesinde, fiziksel olarak elle tutulan fare cihazı kullanılmadan da bilgisayar kontrol edilebilir. Göz ile fare kontrolü yöntemleri, genellikle görüntü işleme yöntemleri kullanılarak yapılır ve bu yöntemler sayesinde, göz hareketleri takip edilerek fare hareketleri ve tıklama işlemleri yapılabilir. Bu yöntemlerin bazıları, yüz tanıma ve nesne tespiti yöntemlerini kullanarak çalışırken, bazıları ise göz izleme teknolojisi kullanarak çalışmaktadır. Bu yöntemler arasında, "EyeTribe", "Tobii EyeX" ve "EyeControl" gibi çeşitli ürünler mevcuttur. Bu yöntemlerin etkili olduğu ve kullanımının kolay olduğu gösterilmiştir, ancak bazı kullanıcılar için bu yöntemlerin doğru çalışması için gözlerin doğru pozisyonlarda olması gerektiği de belirtilmiştir. 
</br></br>
Bu projede gözlerin doğru noktada olmasına gerek yoktur. Gözlerin çevre noktaları hedef alındığından göz konumlarının önemi yoktur.  Şaşılık (strabismus), gözlerin eşit olmayan şekilde hareket etmesi durumudur. Bu durumda, bir göz düzgün bir şekilde hedefe odaklanırken, diğer göz hedefe odaklanamayabilir veya farklı bir yöne bakabilir. Bu durum nedeniyle, gözler arasında görme bozuklukları ortaya çıkabilir ve gözler arasındaki denge bozulabilir. Projemiz bu durumda çalışmakta, gözlerin konumunu baz almamaktadır. Gözlükler, görme bozuklukları olan insanlar için kullanılan bir optik alettir. Bu aletler sayesinde, görme bozuklukları olan insanlar düzgün bir şekilde görebilirler ve görme bozukluklarının neden olduğu sıkıntılar azaltılır. Projemiz gözlük kullanılmasından etkilenmemektedir. Sonuç olarak projemiz çeşitli göz hastalıklarından etkilenmemektedir.

  </p>
  <hr>
 <p> 
  The facial recognition system receives an image through an image sensing device, such as a camera. This image is processed by an image processing module. This module detects facial landmarks (eyes, mouth, and other points) within the image and generates labels for these points. The labels are generated based on a pre-trained facial recognition model, which can detect various facial landmarks. By using the values provided by these landmarks, the system performs operations relative to the x and y axes of the screen, enabling mouse control, clicking, and double-clicking actions.
  
  Controlling a computer using eye movements can be an alternative method for individuals who have disabilities that hinder their ability to use a traditional mouse. With eye-controlled mouse methods, it is possible to control a computer without the need for a physically held mouse device. These methods are typically implemented using image processing techniques, which enable tracking of eye movements and translating them into mouse movements and clicking actions. Some of these methods utilize facial recognition and object detection techniques, while others employ eye-tracking technology. Various products such as "EyeTribe," "Tobii EyeX," and "EyeControl" exist within this field. These methods have shown to be effective and user-friendly, although it should be noted that correct eye positioning is necessary for accurate functioning, which may vary depending on the user.
  
  In this project, it is not necessary for the eyes to be in the correct position. Since the surrounding points of the eyes are targeted, the exact eye position is not crucial. Strabismus refers to the condition where the eyes move unequally. In this condition, while one eye can focus properly on the target, the other eye may not be able to focus on the target or may look in a different direction. As a result, vision impairments and imbalance between the eyes can occur. Our project is designed to work in such cases and does not rely on the specific eye position. Glasses are optical devices used by individuals with visual impairments. These devices allow people with vision impairments to see clearly and reduce the difficulties caused by visual impairments. Our project is not affected by the use of glasses. Therefore, our project is not impacted by various eye conditions.
</p>
  
  
# :hash: Çalışma Mantığı Nedir? what is the working logic?
<p align="justify">
Bu proje Python programlama dilinde yazılmıştır. Kütüphane olarak OpenCv(Open Source Computer Vision), Mediapipe, Pyautogui kütüphaneleri kullanılmıştır. 
</br>
</br>
OpenCv kütüphanesi ile Görüntü işleme yapılıp, bilgisayar kamerası tanıtılmıştır. Kameranın yansıma özelliği kaldırılmıştır. OpenCv kütüphanesi ile renkli görüntü alma, yüzdeki belirli noktaların daireler halinde çizdirilip kullanıcıya gösterimi sağlanmıştır. Projeden çıkma komutu OpenCv kütüphanesi ile yapılmıştır.
</br>
</br>
Mediapipe kütüphanesi görüntü ve ses işleme, mobil uygulamalar ve gerçek zamanlı çözümler geliştirme gibi alanlarda kullanılmaktadır. Mediapipe kütüphanesinin facemesh alanı yüz tanımlama için kullanılmıştır. Yüzün dört yüz altmış sekiz noktasını tanımlamaktadır. Mediapipe ile sol göz üst ve alt kapağı, sağ göz bebeğinin yuvarlağının x ve y ekseninde toplam dört noktası, alt ve üst dudak noktaları belirlenmiştir.
</br>
</br>
Pyautogui, Python dilinde yazılmış bir otomatik kontrol kütüphanesidir. Pyautogui, bilgisayar otomatik kontrolü sağlamak için kullanılır. Projede Pyautogui fare hızının arttırılıp azaltılması, fare hareketlendirilmesi, tıklama işlemi, çift tıklama işleminde kullanılan bir kütüphanedir.
</br>
</br>
OpenCv, Mediapipe ve Pyautogui kütüphaneleri kullanılarak, sağ gözün bebeğinin x ve y ekseninde son noktaları seçilerek, dört nokta belirlenmiştir. Bu dört nokta ile farenin x ve y eksenin de hareketlenmesi sağlanmıştır.
</br>
</br>
OpenCv, Mediapipe ve Pyautogui kütüphaneleri kullanılarak, sol gözün üst ve alt kapağı tespit edilmiştir. Tespit yapılan noktaların değerlerinin birbirlerine yaklaşımını çıkartıp, çıkan değer ile normal göz kırpmadan farklı bir aralığına ininceye kadar hesaplamalar yapılmıştır. Bu hesaplamalar sonucunda 0.005 değerine ulaşılınca tıklama işlemi başarı ile yapılmıştır.
</br>
</br>
OpenCv, Mediapipe ve Pyautogui kütüphaneleri kullanılarak, üst dudak ve alt dudak bölgeleri tespit edilmiştir. Tespit yapılan noktaların değerlerinin birbirinden uzaklaşması toplanmıştır. Çıkan değer sonucunda 0.08 değerine ulaşınca çift tıklama işlemi yapılmıştır.
  </p>
  <hr>
<p> 
This project has been written in the Python programming language. The libraries utilized include OpenCV (Open Source Computer Vision), Mediapipe, and PyAutoGUI.

In this project, the OpenCV library is used for image processing and to access the computer's camera. The camera's reflection property has been removed. With the OpenCV library, the project captures color images and draws circles around specific points on the face for visualization to the user. The exit command from the project is implemented using the OpenCV library.
 
The Mediapipe library is widely used for tasks such as image and sound processing, mobile application development, and real-time solutions. In this project, the facemesh component of the Mediapipe library is utilized for facial recognition. It identifies a total of 468 points on the face. Using Mediapipe, the project determines the following points: the upper and lower eyelids of the left eye, four points on the circular iris of the right eye in the x and y axes, and the points on the upper and lower lips.

Correct, PyAutoGUI is a Python library for automating control of the computer. It is used to provide automated control over various aspects of the computer. In the project, PyAutoGUI is utilized for tasks such as increasing or decreasing the mouse speed, moving the mouse cursor, performing mouse clicks, and executing double-click actions.
  
Using the OpenCV, Mediapipe, and PyAutoGUI libraries, the last points of the circular iris of the right eye are selected in the x and y axes, resulting in four points. These four points are then used to control the movement of the mouse cursor in the x and y axes.

Using the OpenCV, Mediapipe, and PyAutoGUI libraries, the upper and lower eyelids of the left eye are detected. By subtracting the values of the detected points from each other, calculations are performed until the resulting value reaches a different range than a normal blink. When the calculation reaches a value of 0.005, the click operation is successfully triggered.

Using the OpenCV, Mediapipe, and PyAutoGUI libraries, the upper and lower lip regions are detected. The values of the detected points are subtracted from each other to measure the distance. When the resulting value reaches 0.08, the double-click operation is performed.
</p>


  # :hash: Sonuç ve Tartışma/ Conclusion and Discussion
 <p align="justify"> 
  Proje sağ gözün x ve y ekseninden göz bebeğinin başlangıç ve bitiş kısımlarından dairesel şekilde dört nokta belirlenmiştir. Bu noktalar ile fare hareketlendirilmesi sağlanmıştır. Sol gözün üst ve alt kapağından noktalar belirlenip, bu noktaların bir birine yaklaşım değerleri ölçülmüştür. Bu değerler 0.005 değerinden küçük ise tıklama işlemi gerçekleştirilmiştir. Dudaklarımızın üst dudak ve alt dudak orta noktaları belirlenmiştir. Bu noktaların birbirinden uzaklaşma değerleri ölçülmüş, bu değerler y ekseninde birbirinden çıkarılmıştır. Çıkarılan bu değerler 0.08 değerinden büyükse çift tıklama işlemi gerçekleştirilmiştir.
  <hr>
In the project, four circular points are determined using the starting and ending points of the iris in the x and y axes of the right eye. These points are used to control the movement of the mouse cursor. Points are also identified from the upper and lower eyelids of the left eye, and the proximity values between these points are measured. If these values are less than 0.005, a click operation is performed. The middle points of the upper and lower lips are determined, and the distance between these points is measured. If the subtracted value in the y-axis exceeds 0.08, a double-click operation is performed.
    </p>

# :hash: Ekran Görüntüleri/ Screenshots
<div align="center">
 <img src="https://github.com/burakozdemirtas/EyeMouthMouseController/assets/33163650/b8ded632-166d-49da-b6c1-ad02565460b0" >
</div>
<h1> A-4 Tasarım/ A-4 Design</h1>
<div align="center">
 <img src="https://github.com/burakozdemirtas/EyeMouthMouseController/assets/33163650/81237e86-11a6-45d7-8ddb-7e7647c403a1" > 
</div>
