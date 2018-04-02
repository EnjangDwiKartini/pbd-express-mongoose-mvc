#Penggunaan mongoDB pada windows 10 32 bit
====================
MongoDB adalah Produk database noSQl yang mengandalkan struktur JSON untuk menyimpan datanya, mongoDB biasanya sering dipakai untuk aplikasi Cloud, grid computing, atau big data.
*untuk mendapatkan software mongoDB untuk komputer versi 32 bit dapat diperoleh dari : https://www.mongodb.org/dl/win32/i386
*kemudian ekstarak download tersebut dan saya rename folder menjadi mongodb supaya mudah letakan di direktori yang saya inginkan yaitu di direktori F.
*selanjutnya saya buat folder data didalam folder mongodb buat file config.cfg  masukan dbpath=F:\mongodb\data\db logpath=F:\mongodb\log\mongo.log  ( taruh di didalam folder mongodb )
*untuk menjalankan server adalah dengan masuk ke F:\mongodb\bin dan mengetikkan mongod.exe –dbpath=F:\mongodb\data tunggu proses selesai
*selanjutnya ketik mongo “F:\mongodb\bin: mongo” jika ada tulisan Welcome to the mongodb shell berarti sekarang kita bisa menggunakan  mongoDB untuk mulai membuat database aplikasi kita.
*catatan : jika mengalami error rc100 maka tinggal  tambahkan perintah : –storageEngine=mmapv1  seperti contoh berikut : mongod –storageEngine=mmapv1 –dbpath F:\mongodb\data
*berikut adalah tampilan ketika berhasil menginstall mongoDB :
~~~
MongoDB shell version: 3.2.19-25-g88d1d469f9
connecting to: test
Welcome to the MongoDB shell.
For interactive help, type "help".
For more comprehensive documentation, see
        http://docs.mongodb.org/
Questions? Try the support group
        http://groups.google.com/group/mongodb-user
~~~

Berikut adalah proses pembuatan database dengan menggunakan mongoDB , disini saya membuat database dengan nama mahasiswa dan memasukkan 3 data mahasiswa:

~~~
> use mahasiswa
switched to db mahasiswa
> db.mahasiswa.insert(
... {
... nama:"Enjang Dwi Kartini",
... NIM : 163210011,
... Jurusan : "Komputerisasi Akuntansi"
... }
... )
WriteResult({ "nInserted" : 1 })
> db.mahasiswa.insert(
... ... {
... ... nama:"Reza Candra",
... ... NIM : 163310009,
... ... Jurusan : "Teknik Komputer"
... ... }
... ... )
WriteResult({ "nInserted" : 1 })
> db.mahasiswa.insert(
... ... {
... ... nama:"Kartika Widya Setya",
... ... NIM : 165610087,
... ... Jurusan : "Sistem Informasi"
... ... }
... ... )
WriteResult({ "nInserted" : 1 })
~~~

*untuk melihat data yang disimpan maka menggunakan perintah seperti berikut :
~~~
> db.mahasiswa.find()
{ "_id" : ObjectId("5ac1dee6ca781c78c730a48e"), "nama" : "Enjang Dwi Kartini", "NIM" : 163210011, "Jurusan" : "Komputerisasi Akuntansi" }
{ "_id" : ObjectId("5ac1df95ca781c78c730a48f"), "nama" : "Reza Candra", "NIM" : 163310009, "Jurusan" : "Teknik Komputer" }
{ "_id" : ObjectId("5ac1dff0ca781c78c730a490"), "nama" : "Kartika Widya Setya", "NIM" : 165610087, "Jurusan" : "Sistem Informasi" }
>
~~~
*menampilkan kolom tertentu :
~~~
> db.mahasiswa.find({},{"nama":1})
{ "_id" : ObjectId("5ac1dee6ca781c78c730a48e"), "nama" : "Enjang Dwi Kartini" }
{ "_id" : ObjectId("5ac1df95ca781c78c730a48f"), "nama" : "Reza Candra" }
{ "_id" : ObjectId("5ac1dff0ca781c78c730a490"), "nama" : "Kartika Widya Setya" }
>
~~~

*menghapus data :

~~~
>  db.mahasiswa.remove({nama:"Reza Candra"})
WriteResult({ "nRemoved" : 1 })
~~~