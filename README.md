**Nama**: Alyssa Layla Sasti  <br /> 
**Kelas**: AdPro B  <br />
**NPM**: 2306152052 <br />

## REFLECTION MODULE 9 PUBLISHER
1. How much data your publisher program will send to the message broker in one run?
    - Dalam satu kali eksekusi, program publisher mengirim 5 pesan ke message broker. Masing-masing pesan berisi data dari UserCreatedEventMessage, yaitu kombinasi dari user_id dan user_name. Setiap pesan dikirim melalui metode publish_event, sehingga dalam satu run, total ada 5 event yang diterbitkan ke broker. 
2. The url of: “amqp://guest:guest@localhost:5672” is the same as in the subscriber program, what does it mean?
    - URL amqp://guest:guest@localhost:5672 adalah informasi koneksi yang digunakan oleh publisher maupun subscriber untuk berkomunikasi dengan message broker (RabbitMQ).
    - guest:guest adalah pasangan username dan password default. Jadi, saya masuk ke server RabbitMQ dengan akun "guest"
    - localhost artinya RabbitMQ berjalan di komputer saya sendiri (tidak melalui jaringan luar).
    - 5672 adalah port default untuk protokol AMQP.
    - Karena URL-nya sama, maka baik publisher maupun subscriber akan terhubung ke broker yang sama, sehingga publisher dapat mengirim pesan yang nantinya bisa diterima oleh subscriber.

Running RabbitMQ as message broker screenshots:
![running raabitMQ](images/runningrabbit.png)

Running RabbitMQ with one connection screenshots:
![connection rabbit](images/connectionrabbit.png)

Running cargo run from the console:
![sending processing](images/sendingprocessing.png)
Publisher mengirim 5 event ke message broker yang akan diproses oleh subscriber

![spike](images/spike.png)
Setiap kali perintah cargo run dijalankan pada program publisher, terjadi spike pada grafik. Spike ini menunjukkan bahwa publisher berhasil mengirim pesan ke broker RabbitMQ. Pada kasus ini, program dijalankan dua kali sehingga tampak dua spike pada grafik dengan warna ungu yang menunjukkan aktivitas pengiriman (Publish) pesan. Karena tidak ada pesan yang tertinggal di antrean (Queued messages = 0), hal ini mengindikasikan bahwa pesan langsung diproses atau tidak memerlukan acknowledgment. 