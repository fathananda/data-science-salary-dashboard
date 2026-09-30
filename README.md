# Data Science Salary Dashboard: dasbor Excel interaktif

💡 Coba Dashboard Interaktif:

Ingin mengeksplorasi data secara langsung? Anda dapat mengakses dashboard interaktif dan mencoba filter dropdown pada link berikut:

🔗 [Buka Live Interaktif Dashboard](https://s.id/DataScienceSalaryDashboard)🚀

Proyek belajar sekaligus etalase **Excel**: satu lembar dasbor (`Salary Dashboard`) dengan tiga dropdown (job, country, job type) yang menggerakkan tiga kartu KPI dan dua bar chart. Semua angka dihitung langsung dengan formula dinamis (`UNIQUE`, `SORT`, `MEDIAN(IF(...))`) dari tabel data mentah, tanpa makro dan tanpa pivot table.


## Dataset

Sheet `Resource` (tabel bernama `jobs`): **32.672 lowongan** kerja bidang data yang diposting sepanjang 2023 (1 Jan–31 Des), dari **111 negara**. Kolom utama: job title short, job location, job via (platform), job schedule type, job work from home, job no degree mention, job health insurance, job country, salary rate, salary year avg, salary hour avg, company name, dan job skills.

- Ada **10 job**: Data Analyst, Data Scientist, Data Engineer, Senior Data Analyst/Scientist/Engineer, Machine Learning Engineer, Software Engineer, Business Analyst, Cloud Engineer.

## Struktur workbook

| Sheet | Status | Isi |
|---|---|---|
| `Salary Dashboard` | terlihat | Dasbor: 3 dropdown, 3 kartu KPI, 2 bar chart |
| `Resource` | tersembunyi | Data mentah (tabel `jobs`) |
| `Feature Selection` | tersembunyi | Formula dinamis: median gaji per jabatan dan per tipe kerja, sudah terurut |
| `Platform` | tersembunyi | Hitung lowongan per platform untuk kartu "Top Job Platform" |
| `Country` | tersembunyi | Median gaji per negara (sumber peta dan dropdown negara) |

### Dropdown (data validation)

- **Job Title**: 10 job.
- **Country**: 83 negara yang punya data gaji.
- **Type**: Full-time, Contractor, Part-time, Internship, Temp work.

### Kartu KPI

**Median Salary**, **Top Job Platform**, dan **Job Count** untuk kombinasi pilihan dropdown. Formula memakai *named range* (`title`, `country`, `type`, `median`, `top_job`, `count`) agar mudah dibaca.

## Tampilan awal dasbor

![Tampilan awal](image/Data%20Science%20Salary%20Dashboard.png)

**Temuan utama:**

- Pilihan bawaan dashboard adalah **Data Scientist, Indonesia, Full-time**: median gaji **$90.001**, platform teratas **Ai-Jobs.net**, dan hanya **5 lowongan**. Sampelnya kecil (Indonesia total 46 lowongan, 39 di antaranya punya gaji), jadi angka ini indikatif saja.
- Di Indonesia (Full-time), **Senior Data Engineer** memimpin ($147.500) dan **Business Analyst** paling bawah ($64.800). Cloud Engineer tidak punya data, sehingga tidak muncul di chart.

## 1. Gaji per jabatan

**Temuan utama:**

- Secara global, **Senior Data Scientist** paling tinggi (median **$155.000**, 2.009 lowongan), disusul **Senior Data Engineer** ($147.500) dan Data Scientist ($127.500).
- **Data Analyst**, jabatan dengan lowongan terbanyak di antara yang bergaji ($90.000, 9.606 lowongan), masih di bawah Senior Data Analyst ($111.175). Selisih ini menunjukkan nilai naik level yang cukup besar.
- **Business Analyst** paling rendah ($85.000).

## 2. Tipe kerja dan platform

**Temuan utama:**

- **Full-time** mendominasi (21.506 lowongan bergaji, median $115.000). Contractor median $102.500 (463 lowongan).
- Median **Part-time ($128.816)** terlihat tertinggi, tetapi angka ini menyertakan lowongan bertipe gabungan seperti "Full-time and Part-time" (cara filter dropdown adalah mencari kata tipe di dalam kolom `job_schedule_type`). Internship dan Temp work masing-masing hanya 54 lowongan, jadi mediannya kurang stabil.
- Platform terbesar: **LinkedIn** (6.394), **Ai-Jobs.net** (4.975), dan **Indeed** (4.617). Hitungan platform mencakup lowongan tanpa gaji.

## 3. Gaji per negara

**Temuan utama:**

- **Amerika Serikat** mendominasi data: 25.141 dari 32.672 lowongan (sekitar 77%), dengan median $118.940.
- **Sudan** muncul dengan 2.680 lowongan dan median tertinggi ($127.500). Seluruh barisnya berasal dari lokasi pencarian "Sudan", jadi ini kemungkinan artefak cara data dikumpulkan, bukan pasar kerja yang sebenarnya. Hati-hati menafsirkannya.
- Dari 40 negara dengan minimal 30 lowongan bergaji, Australia ($118.500) dan Swedia ($118.140) berada tepat di bawah AS.

## Temuan tambahan dari data mentah

- Lowongan **remote (WFH)** punya median gaji lebih tinggi ($128.453) dibanding non-WFH ($115.000). Lowongan yang menyebut **asuransi kesehatan** juga lebih tinggi ($125.000 vs $111.175).
- Lowongan yang **tidak menyebut syarat gelar** bermedian lebih rendah ($110.000 vs $117.500).
- Skill yang paling sering disebut: **SQL** (18.500), **Python** (17.689), **Tableau** (7.046), R (6.929), AWS (6.844), Excel (6.264).

