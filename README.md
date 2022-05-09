# Notasi Algoritmik CheatSheet

Daftar isi:

* [Notasi Algoritmik Umum](#notasi-algoritmik-umum)
  * [Struktur Umum](#struktur-umum)
  * [Tipe Data Umum](#tipe-data-umum)
  * [Operator](#operator)
  * [Tipe Data Bentukan](#tipe-data-bentukan)
  * [Ekspresi](#ekspresi)
  * [Nama Variabel dan Konstanta](#nama-variabel-dan-konstanta)
  * [Array](#array)
* [Analisis Kasus](#analisis-kasus)
* [Fungsi dan Prosedur](#fungsi-dan-prosedur)
  * [Fungsi](#fungsi)
  * [Prosedur](#prosedur)
* [Loop](#loop)
  * [Repeat N Times](#repeat-n-times)
  * [Repeat-Until](#repeat-until)
  * [While](#while)
  * [Iterate-Stop](#iterate-stop)
  * [For/Traversal](#fortraversal)

## Notasi Algoritmik Umum

### Struktur Umum

```
Program NamaProgram
{ Spesifikasi Program: Tuliskan di sini }

KAMUS
{ Deklarasi variabel }
    a, b: integer
    c : integer >= 0
{ Deklarasi konstanta }
    constant PI : real = 3.14
{ Deklarasi tipe bentukan }
    type Matriks : array [1..3] of array [1..3] of integer

ALGORITMA
    input(a)
    input(b)
    a ← a + b
    output(a)
```

### Tipe Data Umum

* `integer`
* `real`
* `character`
* `boolean`
* `array [firstElmt..lastElmt] of datatype`

### Operator

* Tambah: `+`
* Kurang: `-`
* Kali: `*`
* Bagi: `/`
* Hasil bagi: `div`
* Modulo: `mod`
* Lebih besar dari: `>`
* Lebih kecil dari: `<`
* Tidak sama dengan: `!=` atau `≠` (U+2260)
* Tidak kurang dari: `>=` atau `≥` (U+2265)
* Tidak lebih dari: `<=` atau `≤` (U+2264)
* Sama dengan: `=`
* Boolean and: `and`
* Boolean or: `or`
* Boolean not: `not`
* Boolean xor: `xor`
* Assignment: `←` (U+2190) atau `<-`
* Return: `→`(U+2192) atau `->`
* Input: `input()`
* Output: `output()`

Catatan

* `div` hanya berlaku untuk dua operan integer
* Output bisa mengandung new line atau tidak, suka-suka aja
* Return dan `not` operator adalah operator uner
* Bedakan antara `x < -2` dengan `x <- 2`

### Tipe Data Bentukan

```
type Struct:    < data1: integer,					{ integer dibolehkan }
                  data2: integer[0..69],			{ integer dengan range 0..69 }
                  data3: real,						{ tipe data real juga dibolehkan }
                  data4: array[0..9] of character >	{ karakter/string juga dibolehkan }
```

Cara akses variabel: `varName.data1`, `varName.data2[3]`, dsb.

Contoh:

```
type Time:    < hours: integer[0..23], 		{ 0 ≤ hours ≤ 23 }
                minutes: integer[0..59], 	{ 0 ≤ minutes ≤ 59 }
                seconds: integer[0..59] > 	{ 0 ≤ seconds ≤ 59 }
```
Note : biasanya didefinisikan di KAMUS

### Ekspresi

Sekumpulan rumus perhitungan dari operan dan operator.

Contoh: `2 + 8 * (x mod 4)`

### Nama Variabel dan Konstanta

Berikut ini adalah nama variabel/konstanta yang dibolehkan

* `varName`
* `VarName`
* `varname`
* `Var1`
* `PI` (khusus konstanta, contoh: `IDX_UNDEF`, `VAL_UNDEF`)

Nama variabel yang tidak dibolehkan

* `1cak`
* `*GWS`
* `kereta-api`

### Array

```
NamaArray : array [idMin..idMax] of datatype
```

Keterangan:
* `NamaArray` bisa apa saja
* `idMin` biasanya adalah `0`, `idMax` terserah
* `idMin` dan `idMax` harus merupakan tipe integer
* `datatype` bebas, bisa data bentukan/struct

Contoh:
```
arrayInt : array[0..8] of integer
arrayJam : array[0..59] of Jam
```
Cara akses: `NamaArray[idx]` dengan `idx` harus di dalam range definisi array tersebut

```
{ Array yang terisi sebagian }
constant NMax : integer = 100 {NMax biar gampang ubahnya}
type TabInt : <Tab : array [1..NMax] of integer,
                Neff : integer {1 <= Neff <= NMax} >
T1 : TabInt {T1.Tab[i] untuk akses elemen ke-i dari T1.Tab, T1.Neff untuk akses nilai efektif}
```
Cara akses : untuk akses array `T1` yang merupakan array sebagian dari TabInt, `T1.Tab[i]` akses elemen ke-i dari `T1.Tab`, `T1.Neff` akses nilai efektif

## Analisis Kasus

* Dua Kasus Komplementer
```
if (<kondisi>) then
    <aksi-1>
else { kondisi=false }
    <aksi-2>
```

* Banyak Kasus
```
depend on (<var1>,...)
    <kondisi-1> : <aksi-1>
    <kondisi-2> : <aksi-2>
    ...
else { <kondisi-n> }
    <aksi-n>
```

## Fungsi dan Prosedur

### Fungsi

Struktur umum
```
function NamaFungsi(input param1: type1, input param2: type2, input parametc: typeetc) → output typehasil
{ Mengembalikan fafifu dari wasweswos }

KAMUS LOKAL
{ Nama variabel lokal : tipe data }

ALGORITMA
{ Deretan instruksi }
    
    → hasil
```

Pemanggilan
```
NamaFungsi(param1, param2, parametc)
```

Catatan: jumlah parameter bebas, bisa juga tanpa parameter

### Prosedur

Struktur Umum
```
procedure NamaProsedur(<input/output> param1: type1, <input/output> param2: type2, <input/output> parametc: typeetc)
{ Spek prosedur }
{ I.S. Initial State }
{ F.S. Final State }

KAMUS LOKAL
{ Nama variabel : type variabel }

ALGORITMA
{ Sederet instruksi, bebas mau apa aja }
```

Pemanggilan
```
NamaProsedur(param1, param2, parametc)
```

Catatan: 
* Jumlah parameter bebas, bisa juga tanpa parameter
* Setiap parameter bisa dijadikan input, output, atau keduanya (input/output)
    * input : parameter sudah terdefinisi sebelum prosedur dipanggil
    * output : parameter akan terdefinisi dalam prosedur
    * input/output : sudah terdefinisi sebelum prosedur dipanggil, tetapi nilainya bisa berubah di dalam prosedur

## Loop

### Repeat N Times

Pengulangan berdasarkan banyak pengulangan
```
repeat n times
    { n bilangan bulat terdefinisi }
    <aksi>
```

### Repeat-Until

Pengulangan sampai kondisi berhenti, cek kondisi di akhir
```
repeat
    <aksi>
until <kondisi-berhenti>
```

### While

Pengulangan sampai kondisi berhenti, cek kondisi di awal
```
while <kondisi-loop> do
    <aksi>
```

### Iterate-Stop

Gabungan bentuk repeat-until dan while do, cek kondisi di tengah (di bagian stop)
```
iterate
    <aksi-1>
stop <kondisi-berhenti>
    <aksi-2>
```

### For/Traversal

```
<pencacah> traversal [valMin..valMax]
    <instruksi>
```

Note: pencacah biasanya diisi nama i, j, k, atau lainnya.

Contoh:

```
i traversal [0..8]
    output(i)
```


# SKEMA STANDAR

Daftar Isi :
* [Bag. 1](#bagian-1--validasi-pengulangan-pemrosesan-sekuensial)
    * [Skema Validasi 1](#skema-validasi-1)
    * [Skema Pengulangan](#skema-pengulangan)
    * [Skema Pemrosesan Sekuensial](#skema-pemrosesan-sekuensial)
    * [Skema Validasi 2](#skema-validasi-2)
* [Bag. 2](#bagian-2--skema-traversal-pencarian-nilai-ekstrim-dan-searching-pada-array)
    * [Skema Pemrosesan Sekuensial pada array](#skema-pemrosesan-sekuensial-pada-array)
    * [Skema Pengisian array](#skema-pengisian-array)
    * [Skema Pencarian Nilai Ekstrim](#skema-pencarian-nilai-ekstrim-pada-array)
    * [Skema Sekuensial *Search* pada array](#skema-sekuensial-search-pada-array)
* [Bag. 3](#bagian-3--skema-sorting-pada-array)
    * [Counting Sort](#counting-sort)
    * [Selection Sort](#selection-sort)
    * [Insertion Sort](#insertion-sort)
    * [Bubble Sort](#bubble-sort)
* [Bag. 4](#bagian-4--pemrosesan-file-sekuensial)
    * [Primitif Pemrosesan File Sekuensial](#primitif-pemrosesan-file)
    * [Proses File Sekuensial](#proses-file-secara-sekuensial)
    * [Skema Konsolidasi File](#skema-konsolidasi-file)
    * [Skema Merging 2 File](#skema-merging-2-file)

## Bagian 1 : Validasi, Pengulangan, Pemrosesan Sekuensial

### Skema Validasi 1

```
SKEMA PROSES_VALIDASI
{ Skema program yang menerima input data, hanya melakukan proses jika data valid }

KAMUS
{ deklarasi data_input }

ALGORITMA
    input(<data>)
    if (<data_valid>) then
        <proses>
    else
        output(<pesan_kesalahan>)
```

### Skema Pengulangan

1. Berdasarkan jumlah pengulangan:
    * Diketahui secara persis berapa kali aksi harus dilakukan
        ```
        repeat n times
            <aksi>
        ```

2. Berdasarkan kondisi berhenti:
    * Aksi minimum dilakukan 1x (karena kondisi berhenti dicek setalah aksi dieksekusi)
        ```
        repeat
            <aksi>
        until <kondisi-berhenti>
        ```

3. Berdasarkan kondisi mengulang:
    * Dimungkinkan aksi tidak pernah dilakukan (karena kondisi mengulang dicek sebelum aksi dilakukan)
        ```
        while <kondisi-loop> do
            <aksi>
        ```

4. Berdasarkan dua aksi:
    * merupakan gabungan dari repeat-until dan while-do
    * aksi-1 minimum dilakukan 1x dan aksi-2 bisa tidak dilakukan sama sekali
        ```
        iterate
            <aksi-1>
        stop <kondisi-berhenti>
            <aksi-2>
        ```

5. Berdasarkan pencacah:
    * Pencacah harus bertype ordinal (integer)
    * Diketahui dengan pasti nilai awal dan akhir pencacah
        ```
        { mencacah maju }
        <pencacah> traversal [<min>..<max>]
            <aksi>
        { mencacah mundur }
        <pencacah> traversal [<max>..<min>]
            <aksi>
        ```


### Skema Pemrosesan Sekuensial

Note : 
* First_Elmt : Elemen pertama
* Current_ELmt : Elemen yang siap diproses
* Next_Elmt : Elemen yang diakses setelah Current_Elmt
* EOP : Tanda akhir proses, Bernilai True jika,

    * Dengan Mark : elemen terakhir adalah elemen fiktif (bukan anggota elemen yang diproses)
    ex :
        ```
        SKEMA PEMROSESAN SEKUENSIAL DENGAN MARK
        { Tanpa penanganan kasus kosong }
        SKEMA
            Inisialisasi
            First_Elmt
            while not (EOP) do
                proses_Current_ELmt
                Next_Elmt
            {EOP}
            Terminasi
        ``` 
        ```
        SKEMA PEMROSESAN SEKUENSIAL DENGAN MARK
        { Dengan penanganan kasus kosong }
        SKEMA
            First_Elmt
            if (EOP) then
                proses_Kasus_Kosong
            else
                Inisialisasi
                repeat
                    proses_Current_Elmt
                    Next_Elmt
                until (EOP)
                Terminasi
        ```

    * Tanpa Mark : elemen terakhir bagian dari elemen yang diproses (tidak mungkin ada kasus kosong)
    ex :
        ```
        SKEMA PEMROSESAN SEKUENSIAL TANPA MARK
        { Tanpa penanganan kasus kosong }
        { Dengan iterate-stop }
        SKEMA
            Inisialisasi
            First_Elmt
            iterate
                proses_Current_Elmt
            stop (EOP)
                Next_Elmt
            Terminasi
        ```
        ```
        SKEMA PEMROSESAN SEKUENSIAL TANPA MARK
        { Tanpa penanganan kasus kosong }
        { Dengan repeat-until }
        SKEMA
            Inisialisasi
            First_Elmt
            repeat
                proses_Current_Elmt
                Next_Elmt
            until (EOP)
            Terminasi
        ```

### Skema Validasi 2
* dengan pesan kesalahan
    ```
    SKEMA VALIDASI MASUKAN
    { Data masukan duvalidasi shg didapatkan data yang valid }
    { Proses tanpa mark, dengan iterate-stop }
    { Jika data tidak valid, diberikan pesan kesalahan }
    SKEMA
        iterate
            input(<data>)
        stop(<data_valid>)
            <pesan_kesalahan>
    <proses_data_valid>
    ```
* tanpa pesan kesalahan
    ```
    SKEMA VALIDASI MASUKAN
    { Data masukan duvalidasi shg didapatkan data yang valid }
    { Proses tanpa mark, dengan repeat-until }
    { Jika data tidak valid, diberikan pesan kesalahan }
    SKEMA
        repeat
            input(<data>)
        until (<data_valid>)
    <proses_data_valid>
    ```


## Bagian 2 : Skema Traversal, Pencarian Nilai Ekstrim, dan Searching pada Array    

### Skema Pemrosesan Sekuensial pada Array
Note : Digunakan model akses sekuensial tanpa mark.
* Proses Maju
    ```
    KAMUS UMUM PEMROSESAN ARRAY
        constant NMin : integer = 1
        constant NMax : integer = 100
        type 
            Eltype : ... {type terdefinisi}
        {Variabel}
            i : integer{NMin..NMax}
            T : array[NMin..NMax] of Eltype
        { Deklarasi Prosedur }
            procedure Inisialisasi {Persiapan sebelum pemrosesan}
            procedure Proses (input X : Eltype) {Proses current_elmt}
            procedure Terminasi {Penutupan setelah pemrosesan selesai}
    ```
    ```
    { SKEMA PEMROSESAN ARRAY T untuk indekse [NMin..NMax] }
    { dengan iterate-stop }
        Inisialisasi
        iterate
            Proses(T[i])
        stop (i = NMax)
            i <- i + 1
        Terminasi
    ```
    ```
    { SKEMA PEMROSESAN ARRAY T untuk indekse [NMin..NMax] }
    { dengan traversal }
        i traversal[NMin..NMax]
            Proses(T[i])
        Terminasi

* Contoh Proses Mundur
    ```
    Program TulisTABELMundur
    {Menuliskan isi tabel dari indeks terbesar ke terkecil}

    KAMUS
        constant NMin : integer = 1
        constant NMax : integer = 100

        T : array[NMin..NMax] of integer
        i : integer[NMin..NMax]
        N : integer {ukuran efektif tabel yang terisi 1..N}

    ALGORITMA
        {Anggap T[NMin..N] sudah terisi}
        i traversal [N..NMin]
            output (T[i])
    ```

### Skema Pengisian Array
* Jumlah Elemen diketahui
    ```
    KAMUS
        constant NMax : integer  = 1
        constant NMin : integer  = 100

        i : integer[NMin..NMax]
        T : array[NMin..NMax] of integer
        N : integer

    ALGORITMA
        {inisialisasi}
        repeat
            input(N)
        until (N >= 1) and (N <= 100)
        i traversal (NMin..N)
            input(T[i])
    ```

* Jumlah Elemen tidak diketahui
    ```
    KAMUS
        constant NMin : integer = 1
        constant NMax : integer = 100

        i : integer[NMin..NMax]
        T : array[NMin..NMax] of integer
        N : integer
        x : integer {nilai penyimpanan sementara}

    ALGORITMA
        i <- NMin
        input (x)

        while (x != 9999) and (i <= NMax) do
            T[i] <- x
            i <- i + 1
            input (x)

        if (i > NMax) then
            output ("Tabel sudah penuh")
        N <- i-1
    ```

### Skema Pencarian Nilai Ekstrim pada Array

    ```
    KAMUS UMUM
        constant NMax : integer = 100
        type TabInt : array [1..NMax] of integer

        T : TabInt
        N : integer
    ```

* Mengembalikan nilai maksimum
    ```
    procedure MAX (input T : TabInt, input N : integer, output MAX : integer)
    { I.S. array T tidak kosong, N > 0} 
    { F.S. Menghasilkan nilai maksimum dari array T }

    KAMUS LOKAL
        i : integer

    ALGORITMA
        MAX <- T[1]
        i <- 2
        while (i <= N) do
            if (MAX < T[i]) then
                MAX <- T[i]
            i <- i + 1  
        Terminasi
    ```

* Mengembalikan indeks nilai maksimum
    ```
    procedure IMAX (input T : TabInt, input N : integer, output IMax : integer)
    { I.S. array T tidak kosong, N > 0} 
    { F.S. Menghasilkan nilai maksimum dari array T }

    KAMUS LOKAL
        i : integer

    ALGORITMA
        IMax <- 1
        i <- 2
        while (i <= N) do
            if (T[IMax] < T[i]) then
                IMax <- i
            i <- i+1
        Terminasi
    ```

### Skema Sekuensial *Search* pada Array
    ```
    KASUS UMUM
        constant NMax : integer = 100
        type TabInt : array [1..NMax] of integer
        
        T : TabInt
        N : integer
    ```

* *Searching* tanpa Boolean
    ```
    procedure SEQSearch (input T : TabInt, input N : Integer, input X : integer, output IX : integer)
    { I.S. T tidak boleh kosong, N > 0, biar T[i] tidak error }

    KAMUS LOKAL
        i : integer

    ALGORITMA
    i <- 1
    while (i < N) and (T[i] != X) do
        i <- i + 1
    if (T[i] = X) then
        IX <- i
    else
        IX <- 0
    ```

* Searching dengan Boolean
    ```
    procedure SEQSearchX (input T : TabInt, input N : integer, input X : integer, output IX : integer)
    { I.S. T boleh kosong karena tidak ada pemeriksaan terhadap T[i]}

    KAMUS LOKAL
        i : integer
        Found : boolean

    ALGORITMA
        Found <- false
        i <- 1
        while (i <= N) and (not Found) do
            if (T[i] = X) then
                Found <- true
            else
                i <- i+1
        if (Found) then
            IX <- i
        else   
            IX <- 0
    ```

* Searching pada array terurut
    ```
    procedure SEQSearchSorted (input T : TabInt, input N : integer, input X : integer, output IX : integer)

    KAMUS LOKAL
        i : integer

    ALGORITMA
        while (i < N) and (T[i] < X)
            i <- 1
        if (T[i] = X) then
            IX <- i
        else
            IX <- 0
    ```

* Searching dengan sentinel (Note : sentinel adalah elemen fiktif yang sengaja dipasang pada akhir array)
    ```
    procedure SEQSearchwithSent (input T : TabInt, input N : integer, input X : integer, output IX : integer)

    KAMUS LOKAL
        i : integer[1..N+1]

    ALGORITMA
        T[N+1] = X
        while (T[i] != X) do
            i <- i + 1
        if i < N+1 then
            IX <- i
        else
            IX <- 0
    ```


## Bagian 3 : Skema Sorting pada Array
    ```
    KAMUS UMUM
        constant NMax : integer = 100
        type TabInt : array [1..NMax] of integer

        N : integer
        T : TabInt
    ```

### Counting Sort
Note : dipakai jika diketahui nilai minmum dan maksimum dari array
```
procedure CountSORT (input/output T : TabInt, input N : integer)

KAMUS LOKAL
    TabCount : array [ValMin..ValMax] of integer
    i, j : integer
    K : integer

ALGORITMA
    if (N > 1) then
        { inisialisasi TabCount }
        i traversal [ValMin..ValMax]
            TabCount[i] <- 0
        { Counting }
        i traversal [1..N]
            TabCount[T[i]] <- TabCount[T[i]] + 1
        { pengisian kembali }
        K <- 0
        i traversal [ValMin..ValMax]
            if (TabCount != 0) then
                j traversal [1..TabCount[i]]
                    K <- K+1
                    T[K] <- i
```

### Selection Sort
Note : mengurutkan array [1..N] terurut mengecil degan maksmimum suksesif
```
    procedure (input/output T : TabInt, input N : integer)

    KAMUS LOKAL
        i : integer 
        Pass : integer
        Temp : integer {memorisasi untuk penukaran T[pass] dan T[IMax]}
        IMax : integer {indeks maks untuk T[Pass..N]}

    ALGORITMA
        if (N>1) then
            Pass traversal (i..N-1)
                {Tentukan nilai maksmimum dari T[Pass..N]}
                IMax <- Pass
                i traversal [Pass+1..N]
                    if T[IMax] < T[i] then
                        IMax <- i
                { Tukar nilai T[IMax] dengan T[Pass] }
                Temp <- T[IMax]
                T[IMax] <- T[Pass]
                T[Pass] <- Temp
```

### Insertion Sort
```
procedure InsertionSORT (input/output T : TabInt, input N : integer)
{ mengurutkan tabel degan terurut membesar }

KAMUS LOKAL
    i : integer
    Pass : integer
    Temp : integer

ALGORITMA
    if (N>1) then
        {T[1] adalah elemen yang sudah terurut}
        Pass traversal [2..N]
            Temp <- T[Pass]
            {bandingkan nilai Temp dengan elemen sebelumnya}
            i <- Pass-1
            while (Temp < T[i]) and (i > 1) do
                T[i+1] <- T[i] {geser}
                i <- i-1
            if (Temp >= T[i]) then
                T[i+1] <- Temp
            else
                T[i+1] <- T[i]
                T[i] <- Temp
```

### Bubble Sort
* Versi Asli
    ```
    procedure BubbleShort

    KAMUS LOKAL
        i, K : integer
        Pass : integer
        Temp : integer

    ALGORITMA
        if (N > 1 ) then
            Pass traversal [1..N-1]
                K traversal [N..Pass+1]
                    if (T[K] < T[K-1]) then
                        Temp <- T[K]
                        T[K] <- T[K-1]
                        T[K-1] <- Temp
    ```

* Versi Optimum : akan berhenti jika sudah terurut/tidak terjadi penuakaran sama sekali
    ```
    procedure BubbleSortPlus (input/ouput T : TabInt, input N : integer)

    KAMUS LOKAL
        i : integer
        Pass : integer
        Temp : integer
        Tukar : boolean

    ALGORITMA
        if (N > 1) then
            Pass <- 1
            Tukar <- true
            while (Pass <= N-1) and (Tukar) do
                Tukar <- false
                K traversal [N..Pass+1]
                    if (T[k] < T[K-1]) then
                        Temp <- T[K]
                        T[K] <- T[K-1]
                        T[K-1] <- Temp
                        Tukar <- true
                Pass <- Pass + 1
    ```



## Bagian 4 : Pemrosesan File Sekuensial

### Primitif Pemrosesan File
* Kamus
    ```
    type rekaman : < var1 : datatype
                     var2 : datatype
                     ... >
    NamaArsip : SEQFILE of
        (*) nama_rek : rekaman
        (1) mark

    ```

* Assign Nama Fisik (nama file di harddisk) ke nama lojik (variabel dalam program)
    ```
    assign(namaArsip,namaFisik)
    ```

* Membuka File
    * `open(namaArsip, nama_rek)` : mempersiapkan file untuk dibaca (read-only)
    * `rewrite(namaArsip)` : mempersiapkan file untuk ditulis

* Membaca File
    ```
    read(namaArsip,nama_rek)
    ```

* Menulis File
    ```
    write(namaArsip, nama_rek_baru)
    ```

* Menutup File : harus berpasangan dengan open/rewrite
    ```
    close(namaArsip)
    ```

* EOP : tercapainya mark

### Proses File secara Sekuensial
* Skema Pembacaan File
    ```
    KAMUS UMUM
        f : SEQFILE of
            (*) cc : character
            (1) '.'
    ```
    * Repeat-Until
        ```
        ALGORITMA
            assign(f, "dataku.txt")
            open(f,cc) {First_ELmt}
            if (cc = '.') then
                output ("File kosong")
            else
                repeat
                    output(CC) {proses_Current_Elmt}
                    read(f,cc) {Next_Elmt}
                until (cc = '.')
            close (f)
        ```
    * while-do
        ```
        ALGORITMA
            assign(f, "dataku.txt")
            open(f,cc) 
            while (cc != '.') do
                output (cc)
                read (f,cc)
            close (f)
        ```

* Skema Penulisan File
    ```
    KAMUS UMUM
        f : SEQFILE of
            (*) x : integer
            (1) 9999
    ```
    * While-Do
        ```
        ALGORITMA
            assign(f,x)
            rewrite(f)
            input(x) {First_ELmt}
            while (x != 9999) do
                write(f,x) {Proses_Current_ELmt}
                input(x) {Next_elmt}
            write (f, 9999) 
            close (f)
        ```
    * Repeat-Until
        ```
        ALGORITMA
            assign(f,x)
            rewrite(f)
            input(x)
            if (x = 9999) then
                ouput("File kosong")
            else
                repeat
                    write(f,x)
                    input(x)
                until (x = 9999)
            write(f,9999)
            close(f)
        ```

Contoh : 
* Menghitung nilai rata-rata
    ```
    Program NilaiRataRata
    { Membaca data dalam MHS.dat da menghasilkan nilai rata-rata dari semua mahasiswa }

    KAMUS
        type rekamanMHS : <NIM : string, nilai : integer>
        ArsipMhs : SEQFILE of
            (*) RekMhs : rekamanMHS
            (1) <"99999999", 99>
        SumNil : integer
        JumMHS : integer

    ALGORITMA
        assign(Arsip,"MHS.dat")
        open(ArsipMHS,RekMHS)
        if (RekMHS.NIM = "99999999") and (RekMHS.nilai = 99) then
            output("Arsip kosong")
        else
            SumNil <- 0
            JumMHS <- 0
            repeat
                SumNil <- SumNil + RekMHS.Nilai
                JumMHS <- JumMHS + 1
                read(ArsipMHS, RekMHS)
            until (RekMHS.NIM = "99999999") and (RekMHS.nilai = 99)
            output ("Rata-rata = " (SumNil/JumMHS))
        close (ArsipMHS)
    ```

* Menyalin isi file ke array
    ```
    Program SalinKeArray

    KAMUS
        type rekamanMHS : <NIM : string, nilai : integer>
        ArsipMHS : SEQFILE of
            (*) RekMHS : rekamanMHS
            (1) <"99999999", 99>
        TabelMHS : array [1..100] of rekamanMHS
        JumMHS : integer
    
    ALGORITMA
        assign(ArsipMHS, MHS.dat)
        open(ArsipMHS, RekMHS)
        if (RekMHS.NIM = "99999999") and (RekMHS.nilai = 99) then
            output("Arsip kosong")
        else
            JumMHS <- 1 
            repeat
                TabelMHS[JumMHS].NIM <- RekMHS.NIM
                TabelMHS[JumMHS].nilai <- RekMHS.nilai
                JumMHS <- JumMHS + 1
                read(ArsipMHS, rekMHS)
            until (RekMHS.NIM = "99999999") and (RekMHS.nilai = 99)
            JumMHS <- JumMHS - 1 {penyesuaian JumMHS}
        close (ArsipMHS)
    ```

* Menyalin isi Array ke File
    * Repeat-Until
        ```
        Program SalinKeFile

        KAMUS
            type rekamanMHS : <NIM : string, nilai : integer>
            ArsipMHS : SEQFILE of
                (*) RekMHS : rekamanMHS
                (1) <"99999999", 99>
            TabelMHS : array [1..100] of rekamanMHS
            JumMHS : integer

        ALGORITMA
            { diasumsikan sudah ada bagian program yang mengisi TabelMHS dan JumMHS}
            assign(ArsipMHS, MHS.dat)
            rewrite(ArsipMHS)
            if (JumMHS = 0) then
                output ("Tabel Kosong")
            else
                i <- 1
                repeat
                    RekMHS.NIM <- TabelMHS[i].NIM
                    RekMHS.nilai <- TabelMHS[i].nilai
                    write(ArsipMHS, RekMHS)
                    i <- i + 1
                until (i > JumMHS)
            write (ArsipMHS, markMHS)
            close (ArsipMHS)
        ```
    * While-Do
        ```
        ...
        i <- 1
        while (i <= JumMHS) do
            RekMHS.NIM <- TabelMHS[i].NIM
            RekMHS.nilai <- TabelMHS[i].nilai
            write(ArsipMHS, RekMHS)
            i <- i+1
        write(ArsipMHS, markMHS)
        ...
        ```

### Skema Konsolidasi File
Note :
```
{Proses-proses}
    procedure Inisialisasi_Seluruh_Categ; {Inisialiasi global}
    procedure Terminasi_Seluruh_Categ; { Terminasi global}
    procedure Kasus_Kosong; {Penanganan kasus kosong}
    procedure Init_Categ; {Inisialiasi untuk 1 kategori}
    procedure Proses_Current_Categ; {Proses sebuah elemen dalam 1 kategori}
    procedure Terminasi_Categ; {Terminasi sebuah kategori}
    function EOP (rek : rekaman) -> boolean {true jika rek = mark}
    function separator (K : keytype) -> boolean {true jika K adalah separator}
```
* Tanpa Separator
    * Tanpa Penanganan Kasus Kosong
        ```
        SKEMA KONSOLIDASI Tanpa Separator
        { Input : sebuah arsip sekuensial, terurut}
        { Proses : proses setiap kategori adalah menghitung nilai rata-rata setiap mahasiswa}
        { Output : NIM dan Nilai rata-rata setiap mahasiswa}

        KAMUS
            type keytype : string { kunci rekaman }
            type valtype : integer { harga rekaman }
            type rekaman : < NIM : keytype, 
                             Nilai : valtype >
            constant mark : rekaman = <"99999999",0>
            ArsipMHS : SEQFILE of
                (*) RekMHS : rekaman
                (1) mark
            Current_NIM : keytype { Kategori yang sedang diproses}
            SUMNil : integer
            NKuliah : integer { banyaknya harga dari setiap kunci }

        ALGORITMA
            assign(ArsipMhs, "dataMhs.dat")
            open(ArsipMhs, RekMHS)
            while RekMhs.NIM != "99999999") do
                SumNIl <- 0; Nkuliah <- 0
                Current_NIM <- RekMHS.NIM
                repeat
                    SumNil <- SumNil + RekMHS.Nilai
                    NKuliah <- NKuliah + 1
                    read(ArsipMhs, RekMHS)
                until (Current_NIM != RekMHS.NIM)
                output(Current_NIM, SumNil/NKuliah)
            close(ArsipMhs)
        ```
    * Dengan Penanganan Kasus Kosong
        ```
        SKEMA KONSOLIDASI Tanpa Separator
        { Input : sebuah arsip sekuensial, terurut}
        { Proses : proses setiap kategori adalah menghitung nilai rata-rata setiap mahasiswa}
        { Output : NIM dan Nilai rata-rata setiap mahasiswa}

        KAMUS
            type keytype : string { kunci rekaman }
            type valtype : integer { harga rekaman }
            type rekaman : < NIM : keytype, 
                             Nilai : valtype >
            constant mark : rekaman = <"99999999",0>
            ArsipMHS : SEQFILE of
                (*) RekMHS : rekaman
                (1) mark
            Current_NIM : keytype { Kategori yang sedang diproses}
            SUMNil : integer
            NKuliah : integer { banyaknya harga dari setiap kunci }

        ALGORITMA
            assign(ArsipMhs, "dataMhs.dat")
            open(ArsipMhs, RekMHS)
            if (RekMhs.NIM = "99999999") then
                output("Arsip Kosong")
            else
                repeat
                    SumNIl <- 0; Nkuliah <- 0
                    Current_NIM <- RekMHS.NIM
                    repeat
                        SumNil <- SumNil + RekMHS.Nilai
                        NKuliah <- NKuliah + 1
                        read(ArsipMhs, RekMHS)
                    until (Current_NIM != RekMHS.NIM)
                    output(Current_NIM, SumNil/NKuliah)
                until (RekMhs.NIM = "99999999")
            close(ArsipMhs)
        ```

* Dengan Separator
<br> Note : separator bisa lebih dari 1 </br>

```
Program HitungPanjangKata
{ Input : sebuah arsip sekuensial berisi teks }
{ Proses : menghitung kata terpanjang pada arsip sekuensial }
{ Output : panjang kata maksimum }

KAMUS
    type keytype : character {valtype gak ada, soalnya isinya 1 saja}
    type rekaman : keytype
    constant mark : character = "."
    constant blank : character = " " {sebagai separator}
    ArsipIn : SEQFILE of 
        (*) CC : rekaman
        (1) mark
    PanjangKata : integer {Panjang kata current_categ}
    MaxLength : integer {Panjang kata maksimum}

ALGORITMA
    assign(ArsipIn, "data.txt")
    open(ArsipIn, CC)
    while (CC != mark) and (CC = blank) do
        read(ArsipIn, CC)
    if (CC = mark) then
        output("Arsip Kosong")
    else
        MaxLength <- 0
        repeat
            PanjangKata <- 0
            while (CC != mark) and (CC != blank) do
                PanjangKata <- PanjangKata + 1
                read(ArsipIn, CC)
            if (MaxLength < PanjangKata) then
                MaxLength <- PanjangKata
            while (CC != mark) and (CC = blank) do
                read(ArsipIn, CC)
        until(CC = mark)
        output("Panjang kata maksimum = ", MaxLength)
    close(ArsipIn)
```

### Skema Merging 2 File
* Merging - AND
    ```
    Program Merging - AND
    { Input : Dua arsip sekuensial }
    { Proses : Menggabung kedua arsip menjadi arsip baru yang terurut }
    { Output : Sequential file baru yang terurut }

    KAMUS
        type keytype : ...
        type valtype : ...
        type rekaman : < KeyIn : keytype 
                         ValIn : valtype >
        constant mark : rekaman = <...,...>
        ArsipIn1 : SEQFILE of
            (*) RekIn : rekaman
            (1) mark
        ArsipIn2 : SEQFILE of
            (*) RekIn2 : rekaman
            (1) mark
        ArsipOut : SEQFILE of
            (*) RekOut : rekaman
            (1) mark
    
    ALGORITMA { ini tidak ada valtypenya }
        assign (ArsipIn1, "data.txt")
        open (ArsipIn1, RekIn1)
        assign (ArsipIn2, "data.txt")
        open (ArsipIn2, RekIn2)
        assign (ArsipOut "data.txt")
        open (ArsipOut, RekOut)
        while (RekIn1.KeyIn != mark.KeyIn) and (RekIn2.KeyIn != mark) do
            if (RekIn1.KeyIn <= RekIn2.KeyIn) then
                write(ArsipOut, RekIn1)
                read(ArsipIn1, RekIn1)
            else
                write(ArsipOut, RekIn2)
                read(ArsipIn2, RekIn2)
        {RekIn = mark }
        while (RekIn1.KeyIn != mark) do
            write(ArsipOut, RekIn1)
            read(ArsipIn1, RekIn1)
        while (RekIn2.KeyIn != mark) do
            write(ArsipOut, RekIn2)
            read(ArsipIn2, RekIn2)
        close(ArsipIn1)
        close(ArsipIn2)
        close(ArsipOut)
    ```

* Merging - OR (Note : dipakai jika marknya paling besar diantara KeyIn)
    ```
    Program Merging - AND
    { Input : Dua arsip sekuensial }
    { Proses : Menggabung kedua arsip menjadi arsip baru yang terurut }
    { Output : Sequential file baru yang terurut }

    KAMUS
        type keytype : ...
        type valtype : ...
        type rekaman : < KeyIn : keytype 
                         ValIn : valtype >
        constant mark : rekaman = <...,...>
        ArsipIn1 : SEQFILE of
            (*) RekIn : rekaman
            (1) mark
        ArsipIn2 : SEQFILE of
            (*) RekIn2 : rekaman
            (1) mark
        ArsipOut : SEQFILE of
            (*) RekOut : rekaman
            (1) mark
    
    ALGORITMA
        assign (ArsipIn1, "data.txt")
        open (ArsipIn1, RekIn1)
        assign (ArsipIn2, "data.txt")
        open (ArsipIn2, RekIn2)
        assign (ArsipOut "data.txt")
        open (ArsipOut, RekOut)
        while (RekIn1.KeyIn != mark) or (RekIn2.KeyIn != mark) do
            if (RekIn1.KeyIn <= RekIn2.KeyIn) then
                write(ArsipOut, RekIn1)
                read(ArsipIn1, RekIn1)
            else
                write(ArsipOut, RekIn2)
                read(ArsipIn2, RekIn2)
        close(ArsipIn1)
        close(ArsipIn2)
        close(ArsipIn3)
    ```