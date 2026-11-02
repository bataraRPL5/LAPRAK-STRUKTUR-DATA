# <h1 align="center">Laporan Praktikum Modul 3 - ABSTRACT DATA TYPE (ADT) </h1>
<p align="center">Batara Raditya Wijaya - 109082500084</p>

## Dasar Teori
isi dengan penjelasan dasar teori disertai referensi jurnal (gunakan kurung siku [] untuk pernyataan yang mengambil refernsi dari jurnal).
contoh :
Linked list atau yang disebut juga senarai berantai adalah Salah satu bentuk struktur data yang berisi kumpulan data yang tersusun secara sekuensial, saling bersambungan, dinamis, dan terbatas[1]. Linked list terdiri dari sejumlah node atau simpul yang dihubungkan secara linier dengan bantuan pointer.

### A. ...<br/>
...
#### 1. ...
#### 2. ...
#### 3. ...

### B. ...<br/>
...
#### 1. ...
#### 2. ...
#### 3. ...

## Guided 

### 1. Modul 3 ADT Guided

```Mahasiswa.cpp
#include <iostream>
#include "mahasiswa.h"

using namespace std;

void inputMhs(mahasiswa &m) {
    cout << "input nim = ";
    cin >> (m).nim;
    cout << "input nilai1 = ";
    cin >> (m).nilai1;
    cout << "input nilai2 = ";
    cin >> (m).nilai2;
}

float rata2(mahasiswa m) {
    return float(m.nilai1+m.nilai2)/2;
}



```Mahasiswa.h
#ifndef MAHASISWA_H_INCLUDED
#define MAHASISWA_H_INCLUDED

struct mahasiswa{
   char nim[10];
   int nilai1, nilai2; 
};

void inputMhs (mahasiswa &m) ;
float rata2 (mahasiswa m) ;
#endif



```main.cpp
#include <iostream>
#include "mahasiswa.h"
using namespace std;

int main()
{
    mahasiswa mhs;
    inputMhs (mhs) ;
    cout << "rata-rata = " << rata2 (mhs) ;
    return 0;
}
```
penjelasan singkat guided 1
ADT adalah TYPE dan sekumpulan PRIMITIF (operasi dasar) terhadap TYPE tersebut. Selain itu, dalam sebuah ADT yang lengkap, disertakan pula definisi invarian dari TYPE dan aksioma yang berlaku. ADT merupakan definisi STATIK. 

## Unguided 

### 1. Buat program yang dapat menyimpan data mahasiswa (max. 10) ke dalam sebuah array dengan field nama, nim, uts, uas, tugas, dan nilai akhir. Nilai akhir diperoleh dari FUNGSI dengan rumus 0.3*uts+0.4*uas+0.3*tugas. 

```C++
source code unguided 1
#include <iostream>
#include <string>
using namespace std;

const int MAX = 10;

struct mahasiswa {
    string nama;
    string nim;
    float uts, uas, tugas;
    float nilaiAkhir;
};
float hitungNilaiAkhir(float uts, float uas, float tugas) {
    return 0.3 * uts + 0.4 * uas + 0.3 * tugas;
}
void inputMhs(mahasiswa &m) {
    cout << "Nama  : ";
    getline(cin, m.nama);
    cout << "NIM   : ";
    getline(cin, m.nim);
    cout << "UTS   : ";
    cin >> m.uts;
    cout << "UAS   : ";
    cin >> m.uas;
    cout << "Tugas : ";
    cin >> m.tugas;
    cin.ignore();
    m.nilaiAkhir = hitungNilaiAkhir(m.uts, m.uas, m.tugas);
}
void tampilMhs(mahasiswa data[], int n) {
    cout << "\n=== DATA MAHASISWA ===\n";
    for (int i = 0; i < n; i++) {
        cout << "Mahasiswa ke-" << i + 1 << endl;
        cout << "Nama        : " << data[i].nama << endl;
        cout << "NIM         : " << data[i].nim << endl;
        cout << "UTS         : " << data[i].uts << endl;
        cout << "UAS         : " << data[i].uas << endl;
        cout << "Tugas       : " << data[i].tugas << endl;
        cout << "Nilai Akhir : " << data[i].nilaiAkhir << endl;
        cout << "----------------------" << endl;
    }
}
int main() {
    mahasiswa data[MAX];
    int n;

    do {
        cout << "Jumlah mahasiswa (1-" << MAX << ") : ";
        cin >> n;
    } while (n < 1 || n > MAX);
    cin.ignore();

    for (int i = 0; i < n; i++) {
        cout << "\nInput data mahasiswa ke-" << i + 1 << endl;
        inputMhs(data[i]);
    }
    tampilMhs(data, n);
    return 0;
}
```
### Output Unguided 1 : https://github.com/bataraRPL5/LAPRAK-STRUKTUR-DATA/blob/main/Output%20soal1%20unguided3.jpg

penjelasan unguided 1 
Program ini menyimpan data maksimal 10 mahasiswa dalam sebuah array. Setiap mahasiswa diwakili satu struct yang berisi nama, nim, uts, uas, tugas, dan nilai akhir, sehingga array data[MAX] berisi 10 struct tersebut. Nilai akhir dihitung oleh fungsi hitungNilaiAkhir dengan rumus 0.3*uts + 0.4*uas + 0.3*tugas. Prosedur inputMhs memakai parameter referensi (&m) supaya data yang diisi tersimpan di variabel aslinya, bukan di salinan. Selain itu, getline dipakai agar nama yang mengandung spasi terbaca utuh, dan cin.ignore() dipakai untuk membuang sisa Enter di buffer.

### 2. Buatlah ADT pelajaran sebagai berikut di dalam file “pelajaran.h”:,  Buatlah implementasi ADT pelajaran pada file “pelajaran.cpp”,  Cobalah hasil implementasi ADT pada file “main.cpp”

```C++
source code pelajaran.h
#ifndef PELAJARAN_H_INCLUDED
#define PELAJARAN_H_INCLUDED

#include <string>
using namespace std;

struct pelajaran {
    string namaMapel;
    string kodeMapel;
};

pelajaran create_pelajaran(string namapel, string kodepel);

void tampil_pelajaran(pelajaran pel);

#endif

source code pelajaran.cpp
#include <iostream>
#include "pelajaran.h"
using namespace std;

pelajaran create_pelajaran(string namapel, string kodepel) {
    pelajaran p;
    p.namaMapel = namapel;
    p.kodeMapel = kodepel;
    return p;
}

void tampil_pelajaran(pelajaran pel) {
    cout << "nama pelajaran : " << pel.namaMapel << endl;
    cout << "nilai : " << pel.kodeMapel << endl;
}
source code main.cpp
#include <iostream>
#include "pelajaran.h"
using namespace std;

int main() {
    string namapel = "Struktur Data";
    string kodepel = "STD";
    pelajaran pel = create_pelajaran(namapel, kodepel);
    tampil_pelajaran(pel);

    return 0;
}
```
### Output Unguided 2 : https://github.com/bataraRPL5/LAPRAK-STRUKTUR-DATA/blob/main/Output%20soal2%20unguided3.jpg

penjelasan unguided 2
Soal ini menerapkan konsep ADT, yaitu type dan primitifnya dipisah dari program utama ke dalam tiga file. pelajaran.h berisi spesifikasi type dan deklarasi fungsi, pelajaran.cpp berisi realisasinya, dan main.cpp adalah program yang memakainya. Fungsi create_pelajaran berperan sebagai konstruktor yang membentuk nilai bertype pelajaran, sedangkan tampil_pelajaran menampilkan isinya. Include guard (#ifndef ... #endif) di header mencegah file ter-include dua kali dan menimbulkan error redefinisi. Program utama hanya perlu meng-include header, karena isi fungsinya digabung saat compile.

### 3.Buatlah program dengan ketentuan : - 2 buah array 2D integer berukuran 3x3 dan 2 buah pointer integer - fungsi/prosedur yang menampilkan isi sebuah array integer 2D - fungsi/prosedur yang akan menukarkan isi dari 2 array integer 2D pada posisi tertentu - fungsi/prosedur yang akan menukarkan isi dari variabel yang ditunjuk oleh 2 buah pointer 
```C++
source code unguided 3
#include <iostream>
using namespace std;

const int N = 3;

void tampilArray(int arr[N][N]) {
    for (int i = 0; i < N; i++) {
        for (int j = 0; j < N; j++) {
            cout << arr[i][j] << "\t";
        }
        cout << endl;
    }
}
void tukarArray(int a[N][N], int b[N][N], int baris, int kolom) {
    int temp = a[baris][kolom];
    a[baris][kolom] = b[baris][kolom];
    b[baris][kolom] = temp;
}
void tukarPointer(int *p1, int *p2) {
    int temp = *p1;
    *p1 = *p2;
    *p2 = temp;
}
int main() {
    int A[N][N] = {{1, 2, 3},
                   {4, 5, 6},
                   {7, 8, 9}};
    int B[N][N] = {{10, 20, 30},
                   {40, 50, 60},
                   {70, 80, 90}};

    int x = 100, y = 200;
    int *ptr1 = &x;
    int *ptr2 = &y;

    cout << "=== Array A ===" << endl;
    tampilArray(A);
    cout << "\n=== Array B ===" << endl;
    tampilArray(B);

    int baris, kolom;
    cout << "\nTukar isi A dan B pada posisi" << endl;
    cout << "Baris (0-" << N - 1 << ") : ";
    cin >> baris;
    cout << "Kolom (0-" << N - 1 << ") : ";
    cin >> kolom;

    if (baris >= 0 && baris < N && kolom >= 0 && kolom < N) {
        tukarArray(A, B, baris, kolom);
        cout << "\n=== Setelah ditukar ===" << endl;
        cout << "Array A:" << endl;
        tampilArray(A);
        cout << "Array B:" << endl;
        tampilArray(B);
    } else {
        cout << "Posisi tidak valid!" << endl;
    }
    cout << "\n=== Pointer ===" << endl;
    cout << "Sebelum : *ptr1 = " << *ptr1 << ", *ptr2 = " << *ptr2 << endl;
    tukarPointer(ptr1, ptr2);
    cout << "Sesudah : *ptr1 = " << *ptr1 << ", *ptr2 = " << *ptr2 << endl;

    return 0;
}

##### Output 1
https://github.com/bataraRPL5/LAPRAK-STRUKTUR-DATA/blob/main/Output%20soal3%20unguided3.jpg

penjelasan unguided 3
Soal ini melatih array 2D dan pointer. Fungsi tampil mencetak isi array 3x3 dengan dua perulangan bersarang, yaitu baris di luar dan kolom di dalam. Fungsi tukar menukar elemen pada posisi tertentu di dua array lewat variabel temp. Array tidak perlu diberi & karena array otomatis dikirim sebagai alamat, jadi perubahan langsung berlaku pada array aslinya. Untuk pointer, p = &x berarti p menyimpan alamat x, dan *p adalah nilai di alamat itu. Karena tukarPtr mengubah nilai lewat *p dan *q, isi x dan y di main ikut bertukar.

## Kesimpulan
ADT adalah tipe data beserta operasi dasarnya yang didefinisikan dalam satu kesatuan. Pada praktikum ini, `struct` digunakan untuk menggabungkan beberapa data menjadi satu tipe, dan pemisahan file .h, .cpp, serta main.cpp membuat program lebih terstruktur dan mudah dipakai ulang. Selain itu, penggunaan array 2D dan pointer menunjukkan bahwa data dapat diubah langsung lewat alamat memorinya.

## Referensi
[1] Triase. (2020). Diktat Edisi Revisi : STRUKTUR DATA. Medan: UNIVERSTAS ISLAM NEGERI SUMATERA UTARA MEDAN. 
<br>[2] Indahyati, Uce., Rahmawati Yunianita. (2020). "BUKU AJAR ALGORITMA DAN PEMROGRAMAN DALAM BAHASA C++". Sidoarjo: Umsida Press. Diakses pada 10 Maret 2024 melalui https://doi.org/10.21070/2020/978-623-6833-67-4.
<br>...
