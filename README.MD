# NLP technique with Face Hugging Pipeline
Notebook berisi tentang penggunaan macam-macam pipeline yang disediakan oleh transformer Pipeline dari face hugging

## Tech
<div align="center">
    <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python" />
    <img src="https://img.shields.io/badge/Jupyter-F37626?style=for-the-badge&logo=jupyter&logoColor=white" alt="Jupyter Notebook" />
    <img src="https://img.shields.io/badge/Hugging%20Face-FFD21F?style=for-the-badge&logo=huggingface&logoColor=black" alt="Hugging Face" />
</div>

## Analysis
### 1. Zero Shot Classification
Klasifikasi ini merupakan klasifikasi dalam NLP yang menggunakan teknik zero shot, yaitu pemberian tugas pada ke model tanpa adanya contoh sebelumnya yang relevan. Hal  menarik yang Saya temukan adalah mungkin secara tidak sadar kita sering menggunakan teknik ini ketika melakukan *prompting*, terutama ketika baru saja menggunakan layanan LLM. Teknik ini dapat digunakan untuk mengukur kualitas model karena jawaban yang diberikan dapat menunjukan seberapa baik pemahaman model terhadap bahasa manusia yang pastinya sangat rentan terhadap *noise*, dikarenakan tiap manusia memiliki cara atau penyampaian tulisan yang unik. <br>
Pada percobaan yang dilakukan, model melakukan klasifikasi dengan baik karena dapat mengetahui bahwa konteks yang diberikan merupakan konteks mengenai basket (Golde State Warriors merupakan tim basket)
<br><br>

### 2. Text generation
Text generation merupakan suatu teknik yang digunakan untuk men-*generate* teks sesuai dengan *prompt* yang diberikan. Pada umumnya, model yang digunakan untuk *text generation* menggunakan arsitektur *transformer* bertipe *decoder-only*, contohnya seperti ChatGPT. Pada arsitektur ini, untuk men-generate kata selanjutnya dilakukan kalkulasi terlebih dahulu kata demi kata untuk menghasilkan kata selanjutnya. <br>
Secara umum, arsitektur ini bekerja dengan cara memecah teks menjadi per kata (token) dan akan diubah ke dalam format numerik, serta posisi dari masing-masing kata juga disimpan dengan kalkulasi tertentu. Setelah itu, kalkulasi akan bekerja dengan MHA (*Masked Head Attention*) untuk memastikan kata berikutnya tidak dipengaruhi oleh kata-kata setelahnya, sehingga hanya dipengaruhi oleh kata-kata sebelumnya, lalu masuk ke normalisasi dan penambahan *residual connections* untuk menjaga stabilitas nilai, serta dilakukan *feedforward* untuk memperkaya representasi kata. Setelah itu, baru masuk ke fungsi linear & softmax, dan akhirnya diambil probabilitas tertinggi sebagai kata berikutnya. <br>
Pada percobaan ini, hasil dari *text generation* sangat buruk dikarenakan output yang dihasilkan berbeda jauh dengan konteks yang diberikan.
<br><br>

### 3. Fill mask
Ingat ketika kita mengerjakan soal-soal isian singkat di zaman sekolah dasar? Kurang lebih seperti itu konsep kerja dari teknik ini. Teknik ini bekerja dengan cara mengisi kekosongan kata pada *prompt* yang ditandai dengan kata kunci <mask>. <br>
Pada percobaan yang dilakukan, hasil yang dikeluarkan bisa dibilang cukup buruk karena jawaban yang dihasilkan tidak berkorelasi dengan kalimat sebelum dan setelahnya. <br>
Mungkin boleh dicoba dengan soal SD ya :D
<br><br>

### 4. NER (Named Entity Recognition)
NER merupakan teknik yang dilakukan untuk klasifikasi setiap kata pada suatu teks ke dalam beberapa bagian, yaitu PER (Person), LOC (Location), ORG (Organization), MISC (Miscellanous), DATE, TIME, MONEY, PERCENT, dan GPE (Geopolitical Entity). <br>
Pada percobaan yang dilakukan, model telah mengelompokan kata-kata dengan baik, namun tidak lengkap dalam melakukan pengelompokan, seperti aple community yang seharusnya organisasi dan Depok yang seharusnya Lokasi (mungkin modelnya ga kenal depok hehehe :D)
<br><br>

### 5. Question Answering
Merupakan teknik yang dapat menjawab persoalan-persoalan yang terdapat pada konteks yang diberikan.
Pada percobaan ini, Saya menggunakan 2 bahasa untuk menguji pemahaman model, yaitu bahasa Indonesia dan juga bahasa Inggris. Konteks yang digunakan adalah biografi singkat seorang penyanyi, yaitu Rafi Sudirman. <br>
Hasilnya adalah model dengan konteks dan pertanyaan menggunakan bahasa inggris lebih baik ketimbang bahasa indonesia. Dengan pertanyaan yang sama, model yang menerima konteks dan pertanyaan dengan bahasa inggris dapat menjawab pertanyaan dengan benar, sedangkan yang menggunakan bahasa Indonesia menjawab soal dengan salah. Jadi dapat disimpulkan bahwa model akan bekerja lebih baik jika menggunakan bahasa inggris.
<br><br>

### 6. Sentiment Analysis
Sentiment Analysis merupakan teknik yang digunakan untuk mengidentifikasi sentimen suatu teks. Teknik ini dapat digunakan untuk mengetahui persepsi seseorang terhadap suatu hal, contohnya persepsi seseorang terhadap kedai makan lewat penilaian, atau tempat lainnya. Teknik ini banyak dijumpai pada skripsi di bidang IT. <br>
Pada percobaan ini, model diminta untuk menganalisis suatu teks tentang penilaian timnas sepak bola di era Shin Tae-Yong. Hasilnya model dapat melakukan klasifikasi dengan benar. 
<br><br>

### 7. Summarization
Merupakan teknik yang sangat menarik dan memiliki kebermanfaatan tinggi bagi beberapa orang karena dapat merangkum seluruh intisari-intisari dalam suatu dokumen atau teks.<br>
Pada percobaan ini, teks yang digunakan mengenai makna logo UPN Veteran Jakarta dan menggunakan bahasa inggris. Hasil dari summarization menunjukan bahwa model yang digunakan tidak cukup baik untuk merangkum poin-poin pada teks dikarenakan rangkuman yang dihasilkan tidak menyeluruh, sehingga terdapat simbol yang tidak masuk ke dalam kesimpulan. 
<br><br>

### 8. Translation
Teknik ini bisa dibilang juga memiliki kebermanfaatan yang tinggi dikarenakan dapat mengubah suatu teks dari suatu bahasa ke bahasa lainnya. <br>
Hasil percobaan menunjukan bahwa model dapat menerjemahkan teks dengan sangat baik dikarenakan terjemahan yang dihasilkan benar.
<br><br>
