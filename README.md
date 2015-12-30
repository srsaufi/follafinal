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


