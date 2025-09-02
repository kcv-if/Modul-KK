# Logic


## Daftar Isi
- [Logic](#logic)
  - [Daftar Isi](#daftar-isi)
  - [_Logical Sentences_](#logical-sentences)
    - [Operator untuk Membangun Kalimat Logika](#operator-untuk-membangun-kalimat-logika)
  - [Knowledge-Based Agents](#knowledge-based-agents)
  - [Basis Pengetahuan Proporsisional (Propositional Knowledge Bases)](#basis-pengetahuan-proporsisional-propositional-knowledge-bases)


## _Logical Sentences_

- Kalimat logika atau _logical sentences_ adalah pernyataan yang bisa dinilai benar atau salah. 
- Dalam logika proposisional, kita mulai dari kalimat atomik seperti P ,atau Q yang mewakili fakta sederhana. Kalimat lebih kompleks dibentuk dengan menambahkan penghubung logika seperti “tidak”, “dan”, “atau”. Cara menentukan kebenarannya adalah:

    - Konstanta `True` selalu benar dalam semua model dan `False` selalu salah.
    - Nilai kebenaran setiap simbol proposisi lainnya ditentukan langsung oleh model, contohnya :
        Misalnya kita punya simbol P = “hujan”, Q = “jalan licin”.
        - Dalam satu model, kita bisa tetapkan P = benar, Q = benar.
        - Dalam model lain, bisa saja P = salah, Q = benar.

- Untuk kalimat gabungan, kita lihat nilai setiap bagiannya. Contoh, ¬s (tidak s) benar hanya jika s salah. 


Contoh penerapan dari  kelas `Expr` dari [`logic.py`](https://github.com/kcv-if/Modul-KK/blob/main/Praktikum/2%20-%20Logical%20Agents/logic.py) menyimpan struktur kalimat logika.

Simbol dapat dibuat dengan Expr('P') atau menggunakan fungsi Symbol dan symbols. Operator Python sudah di‑overload sehingga kita bisa menulis kalimat seperti:

```python
from logic import expr, symbols
P, Q = symbols('P Q')       # membuat dua simbol proposisi
sentence = P & ~Q            # merepresentasikan P ∧ ¬Q
another = (P | Q) >> Q       # merepresentasikan (P ∨ Q) ⇒ Q
````

Fungsi bantu `expr` mengurai string menjadi objek `Expr` dan memahami simbol panah `==>`, `<==` dan `<=>` selain operator Python biasa. Kelas `Expr` sendiri tidak menetapkan makna apa pun pada kalimat; ia hanya merepresentasikan sintaksnya.

### Operator untuk Membangun Kalimat Logika



| Operation                | Book | Python Infix Input | Python Output | Python `Expr` Input
|--------------------------|----------------------|-------------------------|---|---|
| Negation                 | &not; P      | `~P`                       | `~P` | `Expr('~', P)`
| And                      | P &and; Q       | `P & Q`                     | `P & Q` | `Expr('&', P, Q)`
| Or                       | P &or; Q | `P`<tt> &#124; </tt>`Q`| `P`<tt> &#124; </tt>`Q` | `Expr('`&#124;`', P, Q)`
| Inequality (Xor)         | P &ne; Q     | `P ^ Q`                | `P ^ Q`  | `Expr('^', P, Q)`
| Implication                  | P &rarr; Q    | `P` <tt>&#124;</tt>`'==>'`<tt>&#124;</tt> `Q`   | `P ==> Q` | `Expr('==>', P, Q)`
| Reverse Implication      | Q &larr; P     | `Q` <tt>&#124;</tt>`'<=='`<tt>&#124;</tt> `P`  |`Q <== P` | `Expr('<==', Q, P)`
| Equivalence            | P &harr; Q   | `P` <tt>&#124;</tt>`'<=>'`<tt>&#124;</tt> `Q`   |`P <=> Q` | `Expr('<=>', P, Q)`


---

## Knowledge-Based Agents

Knowledge-based agents adalah pendekatan AI yang berusaha mencapai kecerdasan dengan menggunakan **pengetahuan** sebagai pusat pengambilan keputusan. Agen jenis ini memiliki kemampuan untuk:

* Menerima tugas baru dalam bentuk tujuan yang dijelaskan secara eksplisit.
* Mencapai kompetensi dengan cepat melalui proses belajar atau diberi pengetahuan baru tentang lingkungannya.
* Beradaptasi terhadap perubahan lingkungan dengan memperbarui pengetahuan yang relevan.

Komponen utama dari agen ini adalah **knowledge base (KB)**, yaitu sekumpulan kalimat atau pernyataan yang dinyatakan dalam bahasa representasi pengetahuan (*knowledge representation language*). Dari KB inilah agen melakukan proses **inferensi**, yaitu menghasilkan representasi atau kalimat baru berdasarkan pernyataan yang sudah ada. Proses inferensi ini yang memungkinkan agen membuat kesimpulan tentang tindakan yang perlu dilakukan.

Untuk berinteraksi dengan KB, terdapat dua operasi penting:

* **TELL(KB, S):** menambahkan kalimat *S* ke basis pengetahuan.
* **ASK(KB, Q):** mengajukan kueri *Q* untuk mengetahui apakah ia merupakan konsekuensi logis dari KB. Jika ya, sistem akan mengembalikan jawaban atau substitusi yang sesuai.

Dengan mekanisme ini, agen mampu membangun representasi dari dunia yang kompleks, melakukan inferensi, dan akhirnya menentukan aksi berdasarkan kesimpulan baru yang diperoleh.

---

## Basis Pengetahuan Proporsisional (Propositional Knowledge Bases)

![](https://files.catbox.moe/zlbw8f.jpg)

Dalam logika proposisional, basis pengetahuan didefinisikan sebagai kumpulan pernyataan (kalimat) logika yang dianggap benar oleh agen. Setiap pernyataan menggunakan simbol-simbol logika untuk merepresentasikan fakta tentang dunia (dunia agent).

KB proposisional menjadi pondasi   untuk membangun agen berbasis pengetahuan(KB). Dengan menambahkan (*TELL*) dan menanyakan (*ASK*) kalimat pada KB, agen bisa terus memperkaya pengetahuan serta menarik kesimpulan baru secara konsisten.

---