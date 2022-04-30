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
constant NMax : integer = 100
type TabInt : <Tab : array [1..NMax] of integer,
                Neff : integer {1 <= Neff <= NMax} >
T1 : TabInt
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
* [Bag. 2](#bagian-2--skema-traversal-pencarian-nilai-ekstrim-dan-searching-pada-array)
* [Bag. 3]()
* [Bag. 4]()

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
        SKEMA PEMROSESAN SEKUENSIAL TANPA MARK
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


## Bagian 2 : Skema Traversal, Pencarian Nilai Ekstrim, dan Searching pada Array    

###  



