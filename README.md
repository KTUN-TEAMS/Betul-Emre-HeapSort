# Heap Sort Algoritması
<p align="center">
  <img src="https://raw.githubusercontent.com/emreoztemiz-ai-ml/heapsortprojesi/975b9a6f291ea68f7030426ece9f84840f426be7/heapsort-team.svg" alt="HeapSihirbazi SVG" width="1100" height="650">
</p>


##  Genel Bakış
Heap Sort, karşılaştırmaya dayalı bir sıralama algoritmasıdır ve binary heap veri yapısını kullanır. Özellikle büyük veri kümelerinde etkilidir.

## Algoritma Yapısı
- **Veri Yapısı:** Binary Heap (Max-Heap veya Min-Heap)
- **Tür:** Karşılaştırmalı Sıralamadır.
- **Kategori:** Yerinde Sıralama yapar. (In-place)

##  Zaman Karmaşıklığı
| Durum          | Karmaşıklık |
|----------------|-------------|
| En Kötü Durum  | O(n log n)  |
| Ortalama Durum | O(n log n)  |
| En İyi Durum   | O(n log n)  |

##  Uzay Karmaşıklığı
- **O(1)**  Yerinde sıralama yapar.

##  Temel Özellikler
- **Kararlı Değil** (Stable sort değil)
- **Divide and Conquer** yaklaşımı kullanır.
- **Recursive** veya **iterative** olarak implemente edilebilir.

##  Çalışma Prensibi
1. **Max-Heap Oluşturma:** Dizi max-heap yapısına dönüştürülür.
2. **Sıralama:** Kök eleman (en büyük) sürekli olarak dizinin sonuna yerleştirilir ve heap yeniden düzenlenir.

##  Kullanım Alanları
- Büyük veri setlerinin sıralanması 
- Öncelik kuyruğu (priority queue) implementasyonları
- Dijkstra ve Prim gibi algoritmalarda kullanılır.

## Avantajları
- Her durumda O(n log n) zaman karmaşıklığındadır.
- Ek bellek gerektirmez. (in-place)
- Büyük veriler için uygundur.

## Dezavantajları
- Küçük veri setlerinde verimsizdir.
- Önbellek dostu değildir .(cache-unfriendly)
- Kararlı sıralama değildir.

## Performans Karşılaştırması
|Algoritma  |En Kötü Durum| En İyi Durum | Yer karmaşıklığı|
|-----------|-------------|--------------|-----------------------|
|Heap Sort	|O(nlogn)     |O(nlogn)      |O(1)
|Quick Sort	|O(n²)	      |O(nlogn)      |O(log n)
|Merge Sort	|O(nlogn)     |O(nlogn)      |O(n)

##  Örnek Kod (C++)
```cpp
#include <iostream>
#include <vector>
using namespace std;

// Heap oluşturmak için yardımcı fonksiyonlarımız
// (arr:Düzenlenecek dizimiz, n:Dizinin boyutu, i:Kök düğüm indeksi)
void heapify(vector<int>& arr, int n, int i) {
    int largest = i; // En büyük elemanı kök olarak ayarlarız
    int left = 2 * i + 1; // Sol çocuk indeksimiz
    int right = 2 * i + 2; // Sağ çocuk indeksimiz

    // Sol çocuk kökten büyük ise
    if (left < n && arr[left] > arr[largest])
        largest = left;

    // Sağ çocuk şu anki en büyükten büyük ise
    if (right < n && arr[right] > arr[largest])
        largest = right;

    // En büyük eleman kök değil ise
    if (largest != i) {
        swap(arr[i], arr[largest]); // Elemanları değiştirip
        
        // Etkilenen alt ağacı tekrar düzenleriz
        heapify(arr, n, largest);
    }
}

// Heap Sort ana fonksiyonumuz
void heapSort(vector<int>& arr) {
    int n = arr.size();

    // Max heap oluştur (diziyi heap yapısına çevirir)
    // Son yaprak olmayan düğümden başlayarak geriye gideriz
    for (int i = n / 2 - 1; i >= 0; i--)
        heapify(arr, n, i);

    // Heap'ten elemanları tek tek çıkarırız
    for (int i = n - 1; i > 0; i--) {
        // Kök (en büyük eleman) ile son elemanı değiştiririz
        swap(arr[0], arr[i]);
        
        // Azaltılmış heap'i tekrar düzenleriz
        heapify(arr, i, 0);
    }
}

int main() {
    vector<int> arr;
    int n, num;

    // Kullanıcıdan eleman sayısını alırız
    cout << "Kac eleman gireceksiniz? ";
    cin >> n;

    // Kullanıcıdan elemanları alırız
    cout << n << " tane sayi giriniz:\n";
    for (int i = 0; i < n; i++) {
        cin >> num;
        arr.push_back(num);
    }

    // Sıralama öncesi diziyi gösteririz
    cout << "\nSiralama oncesi dizi: ";
    for (int num : arr) {
        cout << num << " ";
    }

    // Heap Sort uygulaması
    heapSort(arr);

    // Sıralama sonrası diziyi gösterir
    cout << "\nSiralama sonrasi dizi: ";
    for (int num : arr) {
        cout << num << " ";
    }

    return 0;
}
```

## Örnek Kod Çıktısı
*  Kac eleman gireceksiniz? 5
* 5 tane sayi giriniz:
* 12 5 8 3 10

* Siralama oncesi dizi: 12 5 8 3 10 
* Siralama sonrası dizi: 3 5 8 10 12

## TEST İÇİN CANLI SERVER
🔗 **Uygulama canlı hali ile test etmek için:**  
👉 [cpp-web-deneme.onrender.com](https://cpp-web-deneme.onrender.com)
    [Server Kurulum](https://github.com/emreoztemiz-ai-ml/cpp-web-deneme)
    

  ## Animasyon

[![HEAP SORT Animasyonu](https://img.youtube.com/vi/i7xGwTRarl0/0.jpg)](https://www.youtube.com/watch?v=i7xGwTRarl0)


