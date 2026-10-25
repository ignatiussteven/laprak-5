# <h1 align="center">Laporan Praktikum Modul 5 - SinglyList Bagian 2</h1>
<p align="center">ignatius steven M. - 109082500089</p>

## Dasar Teori
Singly Linked List adalah struktur data linear berupa sekumpulan node yang saling terhubung menggunakan pointer, di mana setiap nodenya terdiri dari komponen info untuk menyimpan data dan next untuk menunjuk ke elemen berikutnya, serta dikelola menggunakan penunjuk utama bernama First.



## Unguided 

### 1. Menampilkan Singly Linked List

#ifndef SINGLYLIST_H
#define SINGLYLIST_H

#include <iostream>

using namespace std;

#define Nil NULL

typedef int infotype;
typedef struct ElmList *address;

struct ElmList {
    infotype info;
    address next;
};

struct List {
    address First;
};

bool ListEmpty(List L);
void createList(List &L);
address alokasi(infotype x);
void dealokasi(address &P);
void printInfo(List L);
void insertFirst(List &L, address P);

address findElm(List L, infotype x);
int sumInfo(List L);

#endif 

##### Output 1
![Screenshot Output Unguided 1_1] https://github.com/ignatiussteven/laprak-5/blob/main/Screenshot%202026-10-25%20221311.png

File header Singlylist.h berfungsi untuk mendefinisikan struktur data node dan list sekaligus menyimpan daftar prototipe fungsi serta prosedur yang akan digunakan dalam program.


### 2. Mencari Elemen Bernilai 8

#include "Singlylist.h"

bool ListEmpty(List L) {
    return (L.First == Nil);
}

void createList(List &L) {
    L.First = Nil;
}

address alokasi(infotype x) {
    address P = new ElmList;
    if (P != Nil) {
        P->info = x;
        P->next = Nil;
    }
    return P;
}

void dealokasi(address &P) {
    delete P;
    P = Nil;
}

void printInfo(List L) {
    address P = L.First;
    while (P != Nil) {
        cout << P->info;
        P = P->next;
    }
    cout << endl;
}

void insertFirst(List &L, address P) {
    P->next = L.First;
    L.First = P;
}

address findElm(List L, infotype x) {
    address P = L.First;
    while (P != Nil) {
        if (P->info == x) {
            return P;
        }
        P = P->next;
    }
    return Nil;
}

int sumInfo(List L) {
    address P = L.First;
    int total = 0;
    while (P != Nil) {
        total += P->info;
        P = P->next;
    }
    return total;
}

##### Output 2
![Screenshot Output Unguided 2_1] https://github.com/ignatiussteven/laprak-5/blob/main/Screenshot%202026-10-25%20221311.png

File implementasi Singlylist.cpp berisi penjabaran logika lengkap dari seluruh fungsi dan prosedur, mulai dari createList untuk menginisialisasi list kosong, alokasi untuk memesan memori node baru, insertFirst untuk menyisipkan elemen di posisi awal, printInfo untuk menampilkan isi list, findElm untuk mencari data tertentu, hingga sumInfo untuk menjumlahkan keseluruhan nilai elemen.

### 3. Menghitung Total Nilai Semua Elemen

#include <iostream>
#include "Singlylist.h"

using namespace std;

int main() {
    List L;
    address P1, P2, P3, P4, P5;
    
    createList(L);
    
    P1 = alokasi(2);
    insertFirst(L, P1);
    
    P2 = alokasi(0);
    insertFirst(L, P2);
    
    P3 = alokasi(8);
    insertFirst(L, P3);
    
    P4 = alokasi(12);
    insertFirst(L, P4);
    
    P5 = alokasi(9);
    insertFirst(L, P5);
    
    printInfo(L);
    
    infotype target = 8;
    address found = findElm(L, target);
    if (found != Nil) {
        cout << target << " ditemukan dalam list" << endl;
    } else {
        cout << target << " tidak ditemukan dalam list" << endl;
    }
    
    int total = sumInfo(L);
    cout << "Total info dari kelima elemen adalah " << total << endl;
    
    return 0;
}

##### Output 3
![Screenshot Output Unguided 3_1] https://github.com/ignatiussteven/laprak-5/blob/main/Screenshot%202026-10-25%20221311.png

File utama main.cpp bertindak sebagai titik eksekusi program untuk memanggil prosedur pembuatan list, memasukkan data secara berurutan, mengeksekusi pencarian elemen, dan menghitung total nilai data yang kemudian ditampilkan ke layar.

## Kesimpulan
Kesimpulannya, pengoperasian Singly Linked List ini memanfaatkan konsep pointer secara dinamis untuk mengelola elemen data, di mana file header bertindak sebagai kerangka, file implementasi memuat aturan kerja setiap fungsinya, dan file utama menjalankan seluruh alur program mulai dari input data hingga menampilkan hasil pencarian serta penjumlahan total nilai.

## Referensi
[1] Triase. (2020). Diktat Edisi Revisi : STRUKTUR DATA. Medan: UNIVERSTAS ISLAM NEGERI SUMATERA UTARA MEDAN. 
<br>[2] Indahyati, Uce., Rahmawati Yunianita. (2020). "BUKU AJAR ALGORITMA DAN PEMROGRAMAN DALAM BAHASA C++". Sidoarjo: Umsida Press. Diakses pada 10 Maret 2024 melalui https://doi.org/10.21070/2020/978-623-6833-67-4.

