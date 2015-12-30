FOLLA: WATER FLOW DETECTOR
Pendeteksi Level Ketinggian pada Penampung Air
(Web Service)

-web ini fungsinya membaca status ketinggian air dari server menggunakan ajax.
format file yang diterima yaitu json contohnya:
{"Level":100} -> dimana ini memiliki key=Level dan value=100 
valuenya satuannya dalam cm dan di web service di tampilkan dalam satuan m nama filenya data.json. 
-di webservice disediakan fungsi setLevel.php yang berfungsi untuk menge-set
json dengan format :
{"Level": 100} -> fungsi ini menerima jarak antara ping dan air yang dikirim oleh Rasberry pi.  
-kemudian di webservice disediakan fungsi createLevel.php dan akan membuat level.txt. yang isinya data di level. untuk membuat persentase ketinggian yang
sudah di olah oleh webservice. dan datanya akan di ambil oleh Rasberry pi untuk keperluan gpio  
-web ini juga mengganti status aplikasi Rasberry Pi dari ON/OFF dengan mengubah data status.json dimana data tersebut
memiliki format sbb:
{"status":1} -> menandakan ON
{"status":0} -> menandakan OFF
fungsi ini diImplementasikan oleh createFile.php yang dipanggil di javascript webservice-nya.


--------------PUNYA BINTANG-----------------------
(GPIO)
File yang mengatur GPIO dan mengatur hubungan antara web dan pi adalah:
 
1. ledStatus.sh: file ini bertugas mengatur lampu yang menyala saat ini, sesuai dengan level air pada penyimpanan air
lampu yang menyala = +1 lampu setiap 20% ketinggian air.

2. nyala.sh: file ini adalah file looping ketika mesin dalam keadaaan menyala, bertugas menghidupkan ledStatus, ketika mesin dimatikan, ia akan switch ke mati.sh

3. mati.sh: file ini adalah looping saat mesin mati, fungsinya mematikan ledStatus dan semua led, jika mesin dinyalakan ia akan switch ke nyala.sh