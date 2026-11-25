<!-- HERO BANNER -->
<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:064E3B,50:0F766E,100:14B8A6&height=210&section=header&text=Sistem%20Akademik%20Siswa&fontSize=44&fontColor=FFFFFF&fontAlignY=38&desc=Sistem%20Informasi%20Akademik%20Berbasis%20Peran%20dengan%20Python%20%26%20Django&descAlignY=63&descSize=16&animation=fadeIn" width="100%" alt="Banner Sistem Akademik Siswa" />
</div>

<div align="center">

[![Python](https://img.shields.io/badge/Python-3.11+-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![Django](https://img.shields.io/badge/Django-Full--Stack-092E20?style=for-the-badge&logo=django&logoColor=white)](https://www.djangoproject.com/)
[![HTML5](https://img.shields.io/badge/HTML5-Template-E34F26?style=for-the-badge&logo=html5&logoColor=white)](https://developer.mozilla.org/)
[![CSS3](https://img.shields.io/badge/CSS3-Styling-1572B6?style=for-the-badge&logo=css3&logoColor=white)](https://developer.mozilla.org/)
[![SQLite](https://img.shields.io/badge/Database-SQLite-003B57?style=for-the-badge&logo=sqlite&logoColor=white)](https://www.sqlite.org/)

<br />

**[Alur Sistem](#alur-sistem-berbasis-peran)** · **[Fitur Utama](#fitur-utama-berdasarkan-peran)** · **[Instalasi Lokal](#cara-menjalankan-di-lokal)** · **[Laporkan Bug](https://github.com/abdulgani89/SistemAkademikSiswa/issues)**

</div>

---

## Gambaran Umum

**Sistem Akademik Siswa** adalah aplikasi web *full-stack* berbasis **Django** untuk memusatkan pengelolaan administrasi akademik sekolah. Sistem ini memisahkan antarmuka dan alur kerja ke dalam tiga peran pengguna—**Administrator**, **Guru**, dan **Siswa**—agar pengelolaan data lebih aman dan terstruktur.

> [!IMPORTANT]
> **Hak Akses Berbasis Peran (RBAC):** Setiap pengguna yang masuk otomatis diarahkan ke *dashboard* sesuai perannya masing-masing, sehingga mencegah perubahan data nilai, jadwal, atau data induk akademik secara tidak sah.

---

## Tampilan Antarmuka

<div align="center">
  <table>
    <tr>
      <td align="center"><b>1. Dashboard Administrator</b></td>
      <td align="center"><b>2. Portal Guru</b></td>
      <td align="center"><b>3. Portal Siswa</b></td>
    </tr>
    <tr>
      <td align="center">
        <img src="./docs/admin-dashboard.png" width="260" alt="Dashboard Administrator" />
      </td>
      <td align="center">
        <img src="./docs/teacher-portal.png" width="260" alt="Portal Guru" />
      </td>
      <td align="center">
        <img src="./docs/student-portal.png" width="260" alt="Portal Siswa" />
      </td>
    </tr>
  </table>
  <sub><i>Tampilan antarmuka khusus untuk pengelolaan administrasi, pengajaran, dan pemantauan akademik siswa</i></sub>
</div>

---

## Alur Sistem Berbasis Peran

```mermaid
flowchart LR
    L["🔐 Halaman Login Terpadu"] --> R{"Cek Peran Pengguna<br/>(Hak Akses / RBAC)"}
    R -- "Admin" --> A["🛠️ Dashboard Admin<br/>Kelola Akun, Kelas, Mapel & Jadwal"]
    R -- "Guru" --> T["📘 Portal Guru<br/>Input Nilai, Absensi & Materi Kelas"]
    R -- "Siswa" --> S["🎓 Portal Siswa<br/>Lihat Jadwal, Nilai & Ringkasan Akademik"]
    A --> DB[("🗄️ Database Relasional<br/>Django ORM")]
    T --> DB
    S --> DB
```

---

## Fitur Utama Berdasarkan Peran

| Peran | Tanggung Jawab & Modul Utama |
| :--- | :--- |
| **Administrator** | CRUD lengkap untuk akun siswa dan guru, pengaturan kelas, mata pelajaran, tahun ajaran, serta pengawasan data sistem. |
| **Guru** | Mengakses kelas yang diampu, menginput dan memperbarui nilai siswa, serta memantau perkembangan akademik kelas. |
| **Siswa** | Melihat profil pribadi, jadwal pelajaran, daftar mata pelajaran, dan rekap nilai akademik secara langsung. |

*(Sesuaikan rincian fitur di tabel atas jika di proyekmu ada modul tambahan seperti absensi harian, pengumuman sekolah, atau cetak rapor PDF.)*

---

## Teknologi yang Digunakan

<div align="center">
  <img src="https://skillicons.dev/icons?i=python,django,html,css,sqlite,git&theme=dark" alt="Ikon Teknologi" />
</div>

- **Backend & ORM:** Python, Django
- **Frontend:** Django Templates (HTML5, CSS3)
- **Autentikasi:** Sistem autentikasi bawaan Django dengan pemisahan rute berbasis peran
- **Database:** SQLite (bawaan untuk pengembangan lokal; siap dimigrasi ke PostgreSQL)

---

## Cara Menjalankan di Lokal

### 1. Clone Repositori & Buat Virtual Environment

```bash
git clone [https://github.com/abdulgani89/SistemAkademikSiswa.git](https://github.com/abdulgani89/SistemAkademikSiswa.git)
cd SistemAkademikSiswa

# Buat virtual environment
python -m venv .venv

# Aktifkan di Windows (PowerShell)
.venv\Scripts\activate

# Aktifkan di macOS / Linux
source .venv/bin/activate
```

### 2. Instal Dependensi & Konfigurasi Environment

```bash
pip install -r requirements.txt
```

Salin file `.env.example` menjadi `.env`, lalu isi konfigurasi lokal berikut:

```env
SECRET_KEY=isi-dengan-django-secret-key-kamu
DEBUG=True
```

### 3. Jalankan Migrasi Database & Server Lokal

```bash
python manage.py migrate
python manage.py createsuperuser
python manage.py runserver
```

Buka `http://127.0.0.1:8000` di browser untuk mengakses aplikasi.

<details>
<summary><b>📂 Klik untuk melihat Struktur Proyek</b></summary>

```text
sistem-akademik-siswa/
├── config/                 # Konfigurasi proyek Django & URL utama (sesuaikan nama foldermu)
├── apps/                   # Aplikasi Django (accounts, academics, grades, dll.)
├── templates/              # Template HTML dikelompokkan per peran (admin, guru, siswa)
├── static/                 # File CSS, skrip, dan aset statis
├── docs/                   # Screenshot antarmuka untuk dokumentasi README
├── manage.py
├── requirements.txt        # Daftar dependensi Python
├── .env.example            # Template variabel environment
└── README.md
```

</details>

---

## Pengembang

<div align="center">

**Muhamad Abdul Gani**

[![GitHub](https://img.shields.io/badge/GitHub-abdulgani89-181717?style=flat-square&logo=github)](https://github.com/abdulgani89)
[![Proyek Lain](https://img.shields.io/badge/Proyek_Live-Gamasrent-0F766E?style=flat-square&logo=vercel)](https://gamasrent.vercel.app)

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:14B8A6,50:0F766E,100:064E3B&height=100&section=footer" width="100%" alt="Footer Wave" />

</div>
