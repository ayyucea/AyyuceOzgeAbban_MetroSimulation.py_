# AyyuceOzgeAbban_MetroSimulation.py_
Metro Simulasyonu
# Sürücüsüz Metro Simülasyonu (Rota Optimizasyonu)

Bu proje, Akbank Python ile Yapay Zekaya Giriş Bootcamp kapsamında geliştirilmiştir. Bir metro ağında iki istasyon arasındaki *en az aktarmalı rotayı* (BFS algoritması ile) ve *en hızlı rotayı* (A* algoritması ile) bulan bir simülasyon sunar. Proje, grafik veri yapıları ve algoritmik problem çözme becerilerini geliştirmeyi amaçlar.

---

## Kullanılan Teknolojiler ve Kütüphaneler

- *Python 3*: Projenin ana programlama dili.
- *collections*: 
  - defaultdict: Metro hatlarını istasyonlarla eşleştirmek için dinamik bir sözlük yapısı sağlar.
  - deque: BFS algoritmasında kuyruk (queue) yapısını hızlı ve verimli bir şekilde implemente etmek için kullanılır.
- *heapq: A algoritmasında öncelik kuyruğu (priority queue) oluşturmak için kullanılır; en düşük maliyetli (süre) rotayı seçmeyi sağlar.
- *typing*: Kodun okunabilirliğini ve tip güvenliğini artırmak için Dict, List, Set, Tuple, Optional gibi tip tanımlamaları kullanılır.

---

## Algoritmaların Çalışma Mantığı

### 1. BFS (Breadth-First Search) Algoritması
- *Nasıl Çalışır?*
  - BFS, metro ağını bir grafik olarak ele alır ve başlangıç istasyonundan hedef istasyona genişlik öncelikli bir arama yapar.
  - deque ile bir kuyruk oluşturur ve her adımda komşu istasyonları ziyaret eder.
  - Ziyaret edilen istasyonlar bir Set ile takip edilir, böylece döngüye girmez.
  - Hedefe ulaşıldığında, en az aktarma gerektiren rota (istasyon listesi) döndürülür.
- *Neden Kullanıldı?*
  - BFS, en kısa yolun adım sayısına (aktarma sayısına) göre bulunmasını garanti eder. Metro ağında aktarma sayısını minimize etmek için idealdir.

### 2. A* Algoritması
- *Nasıl Çalışır?*
  - A*, metro ağında en hızlı rotayı bulmak için kullanılan bir sezgisel arama algoritmasıdır.
  - heapq ile bir öncelik kuyruğu oluşturur; bu kuyruk, toplam süreyi (maliyeti) öncelik olarak alır.
  - Her istasyona ulaşmanın maliyeti bir sözlükte (maliyetler) saklanır ve en düşük maliyetli rota seçilir.
  - Hedefe ulaşıldığında, rota ve toplam süre bir tuple olarak döndürülür.
- *Neden Kullanıldı?*
  - A*, süre gibi bir maliyeti optimize etmek için uygundur. Bu projede, mesafe yerine süre baz alındığından, saf bir maliyet optimizasyonu olarak implemente edildi (sezgisel fonksiyon olmadan).

### Neden Bu Algoritmalar?
- *BFS*: En az aktarmalı rota, kullanıcı konforu için önemlidir ve BFS bu problemi basit ve etkili bir şekilde çözer.
- *A: En hızlı rota, zaman tasarrufu açısından kritik bir ihtiyaçtır ve A* bu optimizasyonu sağlar.

---

## Örnek Kullanım ve Test Sonuçları

Proje, Ankara metro ağına benzer bir örnek ağ ile test edilmiştir. Aşağıda test senaryoları ve sonuçları yer alıyor:

### Test Senaryoları
1. *AŞTİ'den OSB'ye*
   - *En Az Aktarmalı Rota (BFS):* AŞTİ -> Kızılay -> Demetevler -> OSB
   - *En Hızlı Rota (A):** AŞTİ -> Kızılay -> Demetevler -> OSB (18 dakika)
2. *Batıkent'ten Keçiören'e*
   - *En Az Aktarmalı Rota (BFS):* Batıkent -> Demetevler -> Gar -> Keçiören
   - *En Hızlı Rota (A):** Batıkent -> Demetevler -> Gar -> Keçiören (21 dakika)
3. *Keçiören'den AŞTİ'ye*
   - *En Az Aktarmalı Rota (BFS):* Keçiören -> Gar -> AŞTİ
   - *En Hızlı Rota (A):** Keçiören -> Gar -> AŞTİ (11 dakika)

### Kullanım
1. Kodu çalıştırın: python AdSoyad_MetroSimulation.py
2. Test senaryolarının çıktıları konsolda görüntülenecektir.

---

## Projeyi Geliştirme Fikirleri

1. *Görselleştirme:*
   - networkx ve matplotlib ile metro ağını grafik olarak görselleştirme eklenebilir.
2. *Sezgisel Fonksiyon (A):**
   - A* algoritmasına istasyonlar arası tahmini mesafeye dayalı bir heuristic fonksiyon eklenebilir.
3. *Gerçek Veri:*
   - İstanbul veya başka bir şehir metrosuna ait gerçek verilerle ağ genişletilebilir.
4. *Kullanıcı Arayüzü:*
   - Tkinter veya Flask ile kullanıcıdan başlangıç/hedef istasyonlarını girmesini isteyen bir arayüz eklenebilir.
5. *Hata Mesajları:*
   - Rota bulunamadığında daha açıklayıcı hata mesajları döndürülebilir.
6. *Ek Özellikler:*
   - Aktarma sürelerine ek olarak bekleme süreleri veya hat yoğunluğu gibi parametreler eklenebilir.

---

