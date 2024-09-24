# initpy

## Struktur dan Konfigurasi

Dokumen ini merupakan pengantar untuk membantu Anda berkenalan dengan struktur direktori proyek Python, khususnya untuk proyek analisis data. Direktori ini mengandung beberapa konfigurasi sehingga dapat digunakan dalam mode **Enhanced VSCode** dan mode **VSCode in Github Codespaces**. Berikut merupakan pohon struktur direktori:

```
.
├── .devcontainer
│   ├── Dockerfile
│   └── devcontainer.json
├── .gitignore
├── .python-version
├── README.md
├── data
│   └── data.csv
├── main.py
├── notebooks
│   └── 01-analysis.ipynb
├── poetry.lock
├── pyproject.toml
└── src
    ├── __init__.py
    └── module.py
```

Dari struktur direktori di atas, berikut merupakan beberapa berkas konfigurasi penting yang perlu Anda ketahui:

+ `Dockerfile`: berfungsi sebagai 'resep' konfigurasi sistem operasi, program yang terpasang, dan hak akses
+ `devcontainer.json`: berfungsi untuk mengatur Dev container meliputi: 'resep' sistem operasi (yang dinyatakan dalam `Dockerfile`), pengaturan VSCode, dan ekstensi VSCode
+ `.gitignore`: berfungsi untuk mengatur Git agar mengabaikan berkas-berkas tertentu
+ `.python-version`: berfungsi untuk mengatur versi Python yang digunakan dalam proyek
+ `pyproject.toml` dan `poetry.lock`: berfungsi untuk mengelola dependensi paket yang digunakan dalam proyek

## *Whole Game*

Sekarang, mari kita jalankan beberapa perintah *shell* agar Anda semakin mengenal beberapa alur pengelolaan proyek kerja. Pertama, silakan buka *Command Palette* (Ctrl+Shift+P atau Cmd+Shift+P) dan pilih 'Terminal: Create New Terminal'.

Jendela Terminal baru akan segera terbuka, selanjutnya Anda dipersilakan untuk menyalin baris kode berikut dan menjalankannya di Terminal (ketik 'Enter' setelah disalin):

```shell
pyenv versions
```

Baris kode di atas berfungsi untuk melihat versi Python yang terpasang dalam sistem operasi. Untuk mengatur Python versi berapa yang akan dipakai dalam proyek ini (misal Python versi 3.11), Anda dapat menjalankan:

```shell
pyenv local 3.11
```

Silakan konfirmasi dengan cara menjalankan perintah berikut:

```shell
pyenv which python
```

Setelah mengatur versi Python, berikutnya Anda dapat mengaktifkan Poetry untuk pengelolaan dependesi paket. Caranya adalah dengan menjalankan perintah:

```shell
poetry init
```

Pada berkas `pyproject.toml` yang dibuat oleh Poetry, pastikan baris berikut ini tertulis di bawah baris 'readme = "README.md"':
 
```toml
package-mode = false
```

Jika belum ada, silakan Anda tambahkan baris kode tersebut ya! Fungsinya adalah untuk menyatakan bahwa Poetry yang digunakan dalam proyek ini hanya bertugas dalam lingkup pengelolaan dependensi saja.

Kemudian untuk mengaktifkan *virtual environtment* yang dikelola oleh Poetry, Anda dapat menjalankan beris kode berikut:

```shell
poetry shell
```

Setelah melakukan konfigurasi di atas, Anda dapat menggunakan perintah `poetry add nama_paket` untuk menginstal paket dalam proyek. Dalam contoh berikut Anda akan menginstall sebuah paket bernama `cowsay`:

```shell
poetry add cowsay
```

Cobalah menjalankan berkas Python 'main.py' dengan perintah berikut di Terminal:

```shell
python main.py
```

Adapun untuk menghapus paket, Anda dapat menjalankan perintah semisal di bawah ini:

```shell
poetry remove cowsay
```

Cobalah jalankan kembali perintah berikut:

```shell
python main.py
```

Apa yang terjadi?