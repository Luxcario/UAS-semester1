# UAS-semester1
# Projek UAS Bahasa Pemrograman

Nama  : Muhamad David Ali


NIM   : 312210291


kelas : TI 22 A1

# Membuat Package dan Modul dengan sruktur 

![Screenshot (59)](https://user-images.githubusercontent.com/116184002/211849423-b825fa3d-22bc-41f7-bd90-1a7689a76593.png)

# kode program pada package modul

daftar_nilai.py
~~~
data_mahasiswa = {}

def tambahkan():
    print('|===========================================|')
    print('|>>>>>>>>>  Tambah Data Mahasiswa  <<<<<<<<<|')
    print('|===========================================|')
    print('|>>>>>>>>> Masukkan Data Mahasiswa <<<<<<<<<|')

def hapus():
    print('|===========================================|')
    print('|>>>>>>>>>  Hapus Data Mahasiswa   <<<<<<<<<|')
    print('|===========================================|')
    nama = input('Masukkan Nama Mahasiswa\t\t: ')
    if nama in data_mahasiswa.keys():
        del data_mahasiswa[nama]
        print('\n|>>>>>>>>> Data Mahasiswa Berhasil di Hapus <<<<<<<<|')
    else:
        print('\nData {0} Tiak diemukan'.format(nama))

def ubah():
    print('|===========================================|')
    print('\nMengubah Data Mahasiswa')
    nama = input('Masukkan nama mahasiswa\t\t\t: ')
    if nama in data_mahasiswa.keys():
        nim = int(input('Masukkan NIM baru Mahasiswa\t\t: '))
        tugas = int(input('Masukkan nilai tugas terbaru Mahasiswa\t: '))
        uts = int(input('Masukkan nilai UTS terbaru\t\t: '))
        uas = int(input('Masukkan nilai UAS terbaru\t\t: '))
        hasil = (tugas*0.3) + (uts*0.35) + (uas*0.35)
        data_mahasiswa[nama] = nim, tugas, uts, uas, hasil
        print('\n|>>>>>>>>> Data Mahasiswa Berhasil diubah <<<<<<<<|')
    else:
        print('\nData {0} tidak ditemukan'.format(nama))

def cari():
    print('|===========================================|')
    print('|>>>>>>>>>>> Cari Data Mahasiswa <<<<<<<<<<<|')
    print('|===========================================|')
    print('|>>>>>>>>> Masukan Data Mahasiswa <<<<<<<<<<|')
    print('=============================================')
~~~

# kode program pada package view 

input_nilai.py
~~~
from model.daftar_nilai import data_mahasiswa

def tambahdata():
    nama = input('\nMasukkan Nama Mahasiswa\t\t\t: ')
    nim = int(input('Masukkan NIM Mahasiswa\t\t\t: '))
    tugas = int(input('Masukkan nilai Tugas Mahasiswa\t: '))
    uts = int(input('Masukkan nilai UTS Mahasiswa\t: '))
    uas = int(input('Masukkan nilai UAS Mahasiswa\t: '))
    hasil = (tugas*0.3) + (uts*0.35) + (uas*0.35)
    data_mahasiswa[nama] = nim, tugas, uts, uas, hasil
~~~

view_nilai.py
~~~
from model.daftar_nilai import data_mahasiswa

def tampil():
    print('\n=========================== Daftar Nilai Mahasiswa ============================')
    print('|==============================================================================|')
    print('| No |    Nama     |     NIM     |  Tugas  |   UTS   |   UAS   |  NILAI AKHIR  |')
    print('|==============================================================================|')
    i = 0
    for x in data_mahasiswa.items():
        i +=1
        print('| {6:4} | {0:13s} | {1:13} | {2:8d} | {3:6d} | {4:d} | {5:12.2f} | '
              .format(x[0], x[1][0], x[1][1], x[1][2], x[1][3], x[1][4], i))
        print('================================================================================')
    else:
        print('================================================================================')
        print('|==============================  Daftar Nilai  ================================|')
        print('| No |    Nama     |     NIM     |  Tugas  |   UTS   |   UAS   |  NILAI AKHIR  |')
        print('================================================================================')
        print('|                               Tidak ada Data                                 |')
        print('================================================================================')

def caridata():
    nama = input("Masukkan Nama\t: ")
    if nama in data_mahasiswa.keys():
        print("================================================================================")
        print("|==============================   Daftar Nilai  ===============================|")
        print("|==============================================================================|")
        print("|===============| Nama | (NIM, TUGAS, UTS, UAS, NILAI AKHIR) |=================|")
        print("================================================================================")
        print('|               |  {0} | {1} | '.format(nama, data_mahasiswa[nama]))
    else:
        print("Data {0} tidak ada ".format(nama))
~~~

# kode program main.py
~~~
from model.daftar_nilai import tambahkan, ubah, hapus, cari
from view.input_nilai import tambahdata
from view.view_nilai import tampil, caridata

while True:
    print('\nPilihlah menu dibawah ini: ')
    print('==============================')
    print('\n1.Tambah \n2.Tampil \n3.Hapus \n4.Ubah \n5.Cari \n6.Keluar dari Program')
    x = input('\nMasukkan Pilihan Anda\t: ')
    if x.lower() == "1":
        tambahkan()
        tambahdata()
    elif x.lower() == "2":
        tampil()
    elif x.lower() == "3":
        hapus()
    elif x.lower() == "4":
        ubah()
    elif x.lower() == "5":
        cari()
        caridata()
    elif x.lower() == "6":
        print('Anda sudah keluar dari program')
        break

    else:
        print('Pilih menu yang ada di atas')
~~~

# hasil output dari program diatas

![Screenshot (89)](https://user-images.githubusercontent.com/116184002/211872550-8dd2a336-0a8c-4e1c-8e28-c00cf0e93353.png)


- Hasil dari menjalankan program dengan input 1(tambah) dan memasukkan 2 data
![Screenshot (82)](https://user-images.githubusercontent.com/116184002/211870216-fb0c24fc-1b94-4362-874a-1d3cb284ec2c.png)
![Screenshot (83)](https://user-images.githubusercontent.com/116184002/211870251-2c51ced3-74c8-4666-8482-a77f6095441c.png)


- Hasil dari menjalankan program menu 2 (tampil) menampilkan data yang tadi di input
![Screenshot (84)](https://user-images.githubusercontent.com/116184002/211870552-29458f54-9a09-402b-8f5b-d20c7b596c32.png)


- Hasil dari menjalankan program menu 3 (hapus), menghapus data yang dipilih 
![Screenshot (85)](https://user-images.githubusercontent.com/116184002/211870807-27efcc72-e6d5-49f0-8792-f60dc54e6e4c.png)




- Hasil dari menjalankan program menu 4 (ubah), mengubah data yang ada

![Screenshot (86)](https://user-images.githubusercontent.com/116184002/211871083-0e2a8c14-1442-4977-b697-ba4497b68482.png)





- Hasil dari menjalankan program menu 5 (cari), mencari sebauh data
![Screenshot (87)](https://user-images.githubusercontent.com/116184002/211871362-1819afa1-f8b2-423f-b289-653a2f01f94e.png)






- Hasil dari menjalankan proogram menu 6 (keluar dari program)

![Screenshot (88)](https://user-images.githubusercontent.com/116184002/211871568-3b4d2c62-13ab-4d7d-bdb9-004c7e6d60a1.png)




sekian terimakasih

untuk penjelasan youtube menyusul karna masih dalam proses








