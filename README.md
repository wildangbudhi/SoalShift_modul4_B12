# SoalShift_modul4_B12
+ [Soal1](#soal-1)
+ [Soal4](#soal-4)

## Soal1
Untuk menyelesaikan soal nomor 1 maka saya menambahkan fungsi _caesar()_, _encrypt_, dan _decrypt_. Selain itu juga dilakukan perubahan pada fungsi _readdir_, _read_, dan _getattr_.

Fungsi _caesar()_ saya gunakan untuk membuat array yang akan digunakan sebagai kunci dari _Caesar Cipher_. Berikut _source code_ dari fungsi _caesar()_:
```

char base[95]="qE1~ YMUR2\"`hNIdPzi%^t@(Ao:=CQ,nx4S[7mHFye#aT6+v)DfKL$r?bkOGB>}!9_wV']jcp5JZ&Xl|\\8s;g<{3.u*W-0";
char key[95];

void caesar()
{
    int shift=17, baselen = strlen(base), i, j;
    
    for(i=0, j=shift; j<baselen; j++, i++)
    {
        key[i] = base[j];
    }
    
    for(j=0; i<baselen; i++, j++)
    {
        key[i] = base[j];
    }
}
```
+ array `base` dan `key` digunakan untuk menyimpan kunci dari _Caesar Cipher_.
+ `int shift=17, baselen = strlen(base), i, j;` inisialisasi dan pemberian nilai pada variabel-variabel yang dibutuhkan.
+ Dua iterasi yang digunakan adalah untuk membentuk array kunci _Caesar Cipher_.

Fungsi _decrypt()_ saya gunakan untuk men-_decrypt_ nama file asli dan memunculkannya dalam bentuk yang bisa dibaca setelah folder _shift4_ di-_mount_. Berikut _source code_ dari fungsi _decrypt()_:

```

void decrypt(char kal[1000], char dec[1000])
{
    int i, j;
    for(i=0; i<strlen(kal); i++)
    {
        for(j=0; j<strlen(key); j++)
        {
            if(kal[i]==key[j])
            {
                dec[i]=base[j];
                break;
            }
        }
        if(j==strlen(base))
        {
            dec[i]=kal[i];
        }
    }
}
```
+ `void decrypt(char kal[1000], char dec[1000])` deklarasi fungsi _decrypt()_. _return_-nya bertipe _void_ (tidak me-_return_ sesuatu) dan parameternya berupa dua buah array.
+ `int i, j` menginisialisasi variabel yang dibutuhkan.
+ iterasi digunakan untuk memeriksa tiap karakter dan memeriksa kuncinya. Bila karakter yang diperiksa tidak terdapat dalam string kunci, maka string tersebut tidak akan di-_decrypt_. 

Fungsi _encrypt()_ saya gunakan untuk men-_encrypt_ nama file yang sudah ter-_decrypt_ dan mengembalikannya dalam bentuk aslinya (agar saat _getattr_ file/folder yang dimaksud dapat ditemukan). Berikut _source code_ dari fungsi _encrypt()_:
```
void encrypt(char kal[1000], char enc[1000])
{
    //Encrypt
    int i, j;
    for(i=0; i<strlen(kal); i++)
    {
        for(j=0; j<strlen(base); j++)
        {
            if(kal[i] == base[j])
            {
                enc[i]=key[j];
                break;
            }
        }
        if(j==strlen(base))
        {
            enc[i]=kal[i];
        }
    }
}
```
+ `void encrypt(char kal[1000], char enc[1000])` deklarasi fungsi _encrypt()_. _return_-nya bertipe _void_ (tidak me-_return_ sesuatu) dan parameternya berupa dua buah array.
+ Fungsi _encrypt()_ mirip seperti _decrypt_ tetapi array pengecekannya dibalik.

## Soal4
