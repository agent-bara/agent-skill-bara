# Agent Skills

**Keterampilan (skills) rekayasa kelas produksi untuk agen pemrograman AI.**

Keterampilan mengkodekan alur kerja, gerbang kualitas, dan praktik terbaik yang digunakan oleh senior engineer saat membangun perangkat lunak. Keterampilan ini dipaketkan agar agen AI mengikutinya secara konsisten di setiap fase pengembangan.

<a href="https://trendshift.io/repositories/25200" target="_blank"><img src="https://trendshift.io/api/badge/repositories/25200" alt="addyosmani%2Fagent-skills | Trendshift" style="width: 250px; height: 55px;" width="250" height="55"/></a>

![Addy's Agent Skills](https://addyosmani.com/assets/images/addys-agent-skills.jpg)

```
  DEFINE          PLAN           BUILD          VERIFY         REVIEW          SHIP
 ┌──────┐      ┌──────┐      ┌──────┐      ┌──────┐      ┌──────┐      ┌──────┐
 │ Idea │ ───▶ │ Spec │ ───▶ │ Code │ ───▶ │ Test │ ───▶ │  QA  │ ───▶ │  Go  │
 │Refine│      │  PRD │      │ Impl │      │Debug │      │ Gate │      │ Live │
 └──────┘      └──────┘      └──────┘      └──────┘      └──────┘      └──────┘
  /spec          /plan          /build        /test         /review       /ship
```

---

## Perintah (Commands)

8 slash commands yang memetakan siklus hidup pengembangan. Masing-masing mengaktifkan keterampilan yang tepat secara otomatis.

| Apa yang Anda lakukan | Perintah | Prinsip Utama |
|-------------------|---------|---------------|
| Tentukan apa yang akan dibangun | `/spec` | Spesifikasi sebelum kode |
| Rencanakan cara membangunnya | `/plan` | Tugas-tugas kecil yang atomik |
| Bangun secara bertahap | `/build` | Satu bagian kecil pada satu waktu |
| Buktikan bahwa itu berfungsi | `/test` | Pengujian adalah bukti |
| Tinjau sebelum penggabungan | `/review` | Tingkatkan kesehatan kode |
| Audit performa web | `/webperf` | Ukur sebelum Anda optimalkan |
| Sederhanakan kode | `/code-simplify` | Kejelasan di atas kecerdasan |
| Rilis ke produksi | `/ship` | Lebih cepat lebih aman |

Ingin lebih sedikit langkah manual setelah spesifikasi ada? **`/build auto`** menghasilkan rencana dan mengimplementasikan setiap tugas dalam satu langkah yang disetujui — Anda menyetujui rencana sekali, lalu berjalan secara otonom. Ini menghilangkan langkah campur tangan manusia *di antara* tugas-tugas, namun tetap menyertakan verifikasi: setiap tugas tetap diuji (TDD) dan di-commit satu per satu, serta akan berhenti otomatis jika terjadi kegagalan atau langkah berisiko.

Keterampilan juga aktif secara otomatis berdasarkan apa yang Anda lakukan — merancang API memicu `api-and-interface-design`, membangun antarmuka pengguna memicu `frontend-ui-engineering`, dan seterusnya.

---

## Mulai Cepat

**Jalur tercepat — agen apa pun, satu perintah.** [Skills CLI](https://github.com/vercel-labs/skills) terbuka terinstal ke dalam 70+ agen (Claude Code, Cursor, Codex, Copilot, Cline, dll):

```bash
npx skills add addyosmani/agent-skills            # instal semua 24 keterampilan
npx skills add addyosmani/agent-skills --list     # lihat daftar sebelum instal
```

Atau ambil keterampilan secara individual:

```bash
npx skills add addyosmani/agent-skills --skill code-review-and-quality   # tinjauan lima sumbu sebelum penggabungan
npx skills add addyosmani/agent-skills --skill interview-me              # interogasi kebutuhan, satu pertanyaan pada satu waktu
npx skills add addyosmani/agent-skills --skill test-driven-development   # red-green-refactor, dipaksakan
```

> **Menginstal satu keterampilan?** Proses instalasi `npx` per-skill hanya menyalin
> `skills/<name>/`, bukan direktori `references/` tingkat repositori. Keterampilan ini tetap
> berfungsi, tetapi jalur ke daftar periksa bersama tambahan tidak tersedia. Gunakan
> integrasi seluruh repositori, klon repositori, atau salin daftar periksa yang diperlukan ke dalam
> direktori `references/` di dalam keterampilan yang diinstal. Celah portabilitas ini
> dilacak di [#361](https://github.com/addyosmani/agent-skills/issues/361).

Lebih suka integrasi bawaan (native)? Pilih alat Anda di bawah ini.

<details>
<summary><b>Claude Code (disarankan)</b></summary>

**Instal dari marketplace:**

```
/plugin marketplace add addyosmani/agent-skills
/plugin install agent-skills@addy-agent-skills
```

> **Kesalahan SSH?** Marketplace mengkloning repo melalui SSH. Jika Anda belum menyiapkan kunci SSH di GitHub, [tambahkan kunci SSH Anda](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account) atau gunakan URL HTTPS lengkap untuk memaksa kloning HTTPS selama langkah add marketplace:
> ```bash
> /plugin marketplace add https://github.com/addyosmani/agent-skills.git
> /plugin install agent-skills@addy-agent-skills
> ```
>
> Jika `/plugin install` masih gagal dengan `git@github.com: Permission denied (publickey)` di Windows atau macOS, solusi yang disarankan adalah mengonfigurasi Git satu kali untuk menulis ulang URL SSH GitHub menjadi HTTPS untuk subproses kloning:
> ```bash
> git config --global url."https://github.com/".insteadOf git@github.com:
> ```

**Lokal / pengembangan:**

```bash
git clone https://github.com/addyosmani/agent-skills.git
claude --plugin-dir /path/to/agent-skills
```

</details>

<details>
<summary><b>Cursor</b></summary>

Letakkan keterampilan alur kerja di bawah `.cursor/skills/` (sinkronkan dari `agent-skills/skills/`) dan aturan singkat di `.cursor/rules/*.mdc` — jangan tempelkan keterampilan penuh ke dalam aturan (rules). Lihat [docs/cursor-setup.md](docs/cursor-setup.md).

</details>

<details>
<summary><b>Antigravity CLI</b></summary>

Instal sebagai plugin bawaan untuk keterampilan, subagen, dan perintah slash. Lihat [docs/antigravity-setup.md](docs/antigravity-setup.md).

**Instal dari repo:**

```bash
agy plugin install https://github.com/addyosmani/agent-skills.git
```

**Instal dari klon lokal:**

```bash
git clone https://github.com/addyosmani/agent-skills.git
agy plugin install ./agent-skills
```

</details>

<details>
<summary><b>Gemini CLI</b></summary>

Instal sebagai keterampilan bawaan untuk penemuan otomatis, atau tambahkan ke `GEMINI.md` untuk konteks berkelanjutan. Lihat [docs/gemini-cli-setup.md](docs/gemini-cli-setup.md).

**Instal dari repo:**

```bash
gemini skills install https://github.com/addyosmani/agent-skills.git --path skills
```

**Instal dari klon lokal:**

```bash
gemini skills install ./agent-skills/skills/
```

</details>

<details>
<summary><b>Windsurf</b></summary>

Tambahkan konten keterampilan ke konfigurasi aturan Windsurf Anda. Lihat [docs/windsurf-setup.md](docs/windsurf-setup.md).

</details>

<details>
<summary><b>OpenCode</b></summary>

Menggunakan eksekusi keterampilan berbasis agen melalui AGENTS.md dan perkakas `skill`.

Lihat [docs/opencode-setup.md](docs/opencode-setup.md).

</details>

<details>
<summary><b>GitHub Copilot</b></summary>

Gunakan definisi agen dari `agents/` sebagai persona Copilot dan konten keterampilan di `.github/copilot-instructions.md`. Lihat [docs/copilot-setup.md](docs/copilot-setup.md).

</details>

<details>
  <summary><b>Kiro IDE & CLI </b></summary>
  Keterampilan untuk Kiro berada di bawah ".kiro/skills/" dan dapat disimpan di tingkat Proyek atau Global. Kiro juga mendukung Agents.md. Lihat dokumentasi Kiro di https://kiro.dev/docs/skills/
</details>

<details>
<summary><b>Codex</b></summary>

Instal sebagai plugin Codex bawaan (Codex CLI v0.122+):

```bash
codex plugin marketplace add addyosmani/agent-skills
codex plugin add agent-skills@agent-skills
```

Perintah pertama mendaftarkan marketplace; yang kedua menginstal plugin. Codex membaca direktori `skills/` akar secara langsung melalui `.codex-plugin/plugin.json`. Setelah terinstal, jalankan keterampilan di obrolan menggunakan `@` (mis., `@spec-driven-development`). Lihat [docs/codex-setup.md](docs/codex-setup.md) untuk instalasi lokal dan pemecahan masalah.

</details>

<details>
<summary><b>Command Code</b></summary>

Instal secara bawaan dengan perintah `cmd skills` yang disertakan. Command Code mengkloning repo, menemukan setiap `SKILL.md`, dan menginstalnya ke `.commandcode/skills/`:

```bash
cmd skills add addyosmani/agent-skills            # pilih keterampilan untuk diinstal (proyek)
cmd skills add addyosmani/agent-skills --global   # instal untuk semua proyek (~/.commandcode/skills/)
cmd skills add addyosmani/agent-skills -s spec-driven-development  # instal keterampilan tertentu
```

Keterampilan yang terinstal muncul di menu slash TUI, mis. `/spec-driven-development`. Lihat [docs/commandcode-setup.md](docs/commandcode-setup.md).

</details>

<details>
<summary><b>Agen Lainnya</b></summary>

Keterampilan ini berupa Markdown biasa - mereka berfungsi dengan agen apa pun yang menerima prompt sistem atau file instruksi. Lihat [docs/getting-started.md](docs/getting-started.md).

</details>



---

## Adopsi

Sudah menginstal? Cara Anda menerapkannya bergantung pada basis kode Anda. **[Adopsi Panduan](docs/adoption-guide.md)** mencakup dua jalur: siklus hidup penuh dari hari pertama untuk proyek baru, atau penerapan inkremental, yang mengutamakan verifikasi untuk basis kode yang sudah mapan.

---

## Semua 24 Keterampilan

Perintah di atas adalah titik masuk. Paket ini mencakup 24 keterampilan total — 23 keterampilan siklus hidup ditambah meta-keterampilan `using-agent-skills`. Setiap keterampilan adalah alur kerja terstruktur dengan langkah-langkah, gerbang verifikasi, dan tabel anti-rasionalisasi. Anda juga dapat merujuk ke keterampilan apa pun secara langsung.

### Meta - Temukan keterampilan yang berlaku

| Keterampilan | Apa yang Dilakukannya | Kapan Menggunakannya |
|-------|-------------|----------|
| [using-agent-skills](skills/using-agent-skills/SKILL.md) | Memetakan pekerjaan yang masuk ke alur kerja keterampilan yang tepat dan mendefinisikan aturan operasi bersama | Memulai sesi atau memutuskan keterampilan mana yang berlaku |

### Definisikan - Perjelas apa yang akan dibangun

| Keterampilan | Apa yang Dilakukannya | Kapan Menggunakannya |
|-------|-------------|----------|
| [interview-me](skills/interview-me/SKILL.md) | Wawancara satu pertanyaan pada satu waktu yang mengekstrak apa yang sebenarnya diinginkan pengguna, alih-alih apa yang mereka pikir mereka inginkan, hingga ~95% kepercayaan | Permintaan kurang spesifik, atau pengguna memanggil "interview me" / "grill me" |
| [idea-refine](skills/idea-refine/SKILL.md) | Berpikir divergen/konvergen terstruktur untuk mengubah ide yang samar menjadi proposal konkret | Anda memiliki konsep kasar yang perlu dieksplorasi |
| [spec-driven-development](skills/spec-driven-development/SKILL.md) | Menulis PRD yang mencakup sasaran, perintah, struktur, gaya kode, pengujian, dan batasan sebelum ada kode | Memulai proyek, fitur, atau perubahan signifikan yang baru |

### Rencanakan - Pecah-pecah

| Keterampilan | Apa yang Dilakukannya | Kapan Menggunakannya |
|-------|-------------|----------|
| [planning-and-task-breakdown](skills/planning-and-task-breakdown/SKILL.md) | Memecah spesifikasi menjadi tugas-tugas kecil yang dapat diverifikasi dengan kriteria penerimaan dan urutan ketergantungan | Anda memiliki spesifikasi dan membutuhkan unit yang dapat diimplementasikan |

### Bangun - Tulis kode

| Keterampilan | Apa yang Dilakukannya | Kapan Menggunakannya |
|-------|-------------|----------|
| [incremental-implementation](skills/incremental-implementation/SKILL.md) | Potongan vertikal tipis - implementasi, uji, verifikasi, commit. Feature flags, pengaturan default yang aman, perubahan ramah rollback | Setiap perubahan yang memengaruhi lebih dari satu file |
| [test-driven-development](skills/test-driven-development/SKILL.md) | Red-Green-Refactor, piramida pengujian (80/15/5), ukuran pengujian, DAMP daripada DRY, Aturan Beyonce, pengujian browser | Menerapkan logika, memperbaiki bug, atau mengubah perilaku |
| [context-engineering](skills/context-engineering/SKILL.md) | Memberi agen informasi yang tepat pada waktu yang tepat - file aturan, pemaketan konteks, integrasi MCP | Memulai sesi, beralih tugas, atau saat kualitas keluaran turun |
| [source-driven-development](skills/source-driven-development/SKILL.md) | Mendasarkan setiap keputusan kerangka kerja (framework) pada dokumentasi resmi - verifikasi, kutip sumber, tandai yang tidak terverifikasi | Anda menginginkan kode otoritatif yang dikutip sumbernya untuk framework atau pustaka apa pun |
| [doubt-driven-development](skills/doubt-driven-development/SKILL.md) | Tinjauan konteks baru yang berlawanan (adversarial) untuk setiap keputusan non-sepele yang sedang berlangsung - KLAIM → EKSTRAK → RAGU → REKONSILIASI → BERHENTI, dengan eskalasi lintas model yang diizinkan pengguna | Risikonya tinggi (produksi, keamanan, tidak dapat diubah), bekerja dalam kode asing, atau keluaran yang yakin lebih murah untuk diverifikasi sekarang daripada di-debug nanti |
| [frontend-ui-engineering](skills/frontend-ui-engineering/SKILL.md) | Arsitektur komponen, sistem desain, manajemen status, desain responsif, aksesibilitas WCAG 2.1 AA | Membangun atau memodifikasi antarmuka yang menghadap pengguna |
| [api-and-interface-design](skills/api-and-interface-design/SKILL.md) | Desain mengutamakan kontrak, Hukum Hyrum, Aturan Satu-Versi, semantik kesalahan, validasi batasan | Merancang API, batasan modul, atau antarmuka publik |

### Verifikasi - Buktikan itu berfungsi

| Keterampilan | Apa yang Dilakukannya | Kapan Menggunakannya |
|-------|-------------|----------|
| [browser-testing-with-devtools](skills/browser-testing-with-devtools/SKILL.md) | MCP Alat Pengembang Chrome untuk data proses aktif (runtime) - inspeksi DOM, log konsol, pelacakan jaringan, profil performa | Membangun atau men-debug apa pun yang berjalan di browser |
| [debugging-and-error-recovery](skills/debugging-and-error-recovery/SKILL.md) | Triase lima langkah: reproduksi, lokalisasi, kurangi, perbaiki, jaga (guard). Aturan stop-the-line, mundur yang aman | Tes gagal, build rusak, atau perilaku tak terduga |

### Tinjau - Gerbang kualitas sebelum merge

| Keterampilan | Apa yang Dilakukannya | Kapan Menggunakannya |
|-------|-------------|----------|
| [code-review-and-quality](skills/code-review-and-quality/SKILL.md) | Tinjauan lima sumbu, penentuan ukuran perubahan (~100 baris), label keparahan (Nit/Opsional/FYI), norma kecepatan tinjauan, strategi pemisahan | Sebelum menggabungkan perubahan apa pun |
| [code-simplification](skills/code-simplification/SKILL.md) | Pagar Chesterton, Aturan 500, kurangi kerumitan namun tetap pertahankan perilaku yang persis | Kode berfungsi namun lebih sulit dibaca atau di-maintain daripada yang seharusnya |
| [security-and-hardening](skills/security-and-hardening/SKILL.md) | Pencegahan OWASP Top 10, pola auth, manajemen rahasia, audit dependensi, sistem batas tiga tingkat | Menangani input pengguna, auth, penyimpanan data, atau integrasi eksternal |
| [performance-optimization](skills/performance-optimization/SKILL.md) | Pendekatan ukur-dulu - Target Core Web Vitals, alur kerja pembuatan profil, analisis bundle, deteksi anti-pola | Persyaratan performa ada atau Anda mencurigai adanya kemunduran (regressions) |

### Rilis - Deploy dengan percaya diri

| Keterampilan | Apa yang Dilakukannya | Kapan Menggunakannya |
|-------|-------------|----------|
| [git-workflow-and-versioning](skills/git-workflow-and-versioning/SKILL.md) | Pengembangan berbasis Trunk, commit atomik, ukuran perubahan (~100 baris), pola commit-sebagai-titik-simpan | Melakukan perubahan kode apa pun (selalu) |
| [ci-cd-and-automation](skills/ci-cd-and-automation/SKILL.md) | Shift Left, Lebih Cepat Lebih Aman, feature flags, pipeline gerbang kualitas, loop umpan balik kegagalan | Menyiapkan atau memodifikasi pipeline build dan deploy |
| [deprecation-and-migration](skills/deprecation-and-migration/SKILL.md) | Pola pikir kode-sebagai-kewajiban, deprecation wajib vs nasihat, pola migrasi, penghapusan kode zombie | Menghapus sistem lama, memigrasikan pengguna, atau menghentikan fitur (sunsetting) |
| [documentation-and-adrs](skills/documentation-and-adrs/SKILL.md) | Rekaman Keputusan Arsitektur, dokumentasi API, standar dokumentasi sebaris (inline) - dokumentasikan *mengapa* | Membuat keputusan arsitektur, mengubah API, atau merilis fitur |
| [observability-and-instrumentation](skills/observability-and-instrumentation/SKILL.md) | Pencatatan terstruktur, metrik RED, pelacakan OpenTelemetry, peringatan berbasis gejala - pasang instrumen saat Anda membangun | Menambahkan telemetri, atau merilis apa pun yang berjalan dalam produksi |
| [shipping-and-launch](skills/shipping-and-launch/SKILL.md) | Daftar periksa prakeluncuran, siklus hidup feature flag, peluncuran bertahap, prosedur pembatalan (rollback), penyiapan pemantauan | Bersiap untuk rilis ke produksi |

---

## Persona Agen

Persona spesialis terkonfigurasi untuk ulasan yang ditargetkan:

| Agen | Peran | Perspektif |
|-------|------|-------------|
| [code-reviewer](agents/code-reviewer.md) | Senior Staff Engineer | Tinjauan kode lima sumbu dengan standar "apakah staf engineer akan menyetujui ini?" |
| [test-engineer](agents/test-engineer.md) | Spesialis QA | Strategi pengujian, analisis cakupan, dan pola Prove-It |
| [security-auditor](agents/security-auditor.md) | Engineer Keamanan | Deteksi kerentanan, pemodelan ancaman, penilaian OWASP |
| [web-performance-auditor](agents/web-performance-auditor.md) | Engineer Performa Web | Audit Core Web Vitals dengan mode Quick/Deep dan aturan kejujuran metrik; jalankan melalui `/webperf` |

Lihat [docs/agents.md](docs/agents.md) untuk matriks keputusan, aturan orkestrasi, dan bagaimana persona tergabung dengan keterampilan dan perintah slash.

---

## Daftar Periksa Referensi

Materi referensi cepat yang diambil oleh keterampilan saat diperlukan:

| Referensi | Mencakup |
|-----------|--------|
| [definition-of-done.md](references/definition-of-done.md) | Standar berdiri di seluruh proyek di mana setiap perubahan harus terpenuhi, kontras dengan kriteria penerimaan per-tugas |
| [testing-patterns.md](references/testing-patterns.md) | Struktur pengujian, penamaan, mocking, contoh React/API/E2E, anti-pola (JavaScript/TypeScript) |
| [security-checklist.md](references/security-checklist.md) | Pemeriksaan sebelum-commit, auth, validasi input, header, CORS, OWASP Top 10 |
| [performance-checklist.md](references/performance-checklist.md) | Target Core Web Vitals, daftar periksa frontend/backend, perintah pengukuran |
| [accessibility-checklist.md](references/accessibility-checklist.md) | Navigasi keyboard, pembaca layar, desain visual, ARIA, alat pengujian |
| [observability-checklist.md](references/observability-checklist.md) | Pertanyaan siaga (on-call), pencatatan terstruktur, metrik RED/USE, pelacakan, peringatan berbasis gejala, gerbang prakeluncuran |
| [orchestration-patterns.md](references/orchestration-patterns.md) | Pola orkestrasi multi-persona yang disahkan, anti-pola, dan aturan "persona tidak memanggil persona" |

---

## Cara Keterampilan Bekerja

Setiap keterampilan mengikuti anatomi yang konsisten:

```
┌─────────────────────────────────────────────────┐
│  SKILL.md                                       │
│                                                 │
│  ┌─ Frontmatter ─────────────────────────────┐  │
│  │ name: lowercase-hyphen-name               │  │
│  │ description: Guides agents through [task].│  │
│  │              Use when…                    │  │
│  └───────────────────────────────────────────┘  │                                                                                                
│  Overview         → Apa yang dilakukan ini      │
│  When to Use      → Kondisi pemicu              │
│  Process          → Alur kerja langkah demi     │
│  Rationalizations → Alasan + sanggahan          │
│  Red Flags        → Tanda ada yang salah        │
│  Verification     → Persyaratan bukti           │
└─────────────────────────────────────────────────┘
```

**Pilihan desain utama:**

- **Proses, bukan sekadar prosa.** Keterampilan adalah alur kerja yang diikuti agen, bukan sekadar dokumen referensi yang mereka baca. Masing-masing memiliki langkah-langkah, pos pemeriksaan, dan kriteria keluar.
- **Anti-rasionalisasi.** Setiap keterampilan mencakup tabel alasan umum yang digunakan agen untuk melewati langkah (misalnya, "Saya akan menambahkan pengujian nanti") beserta argumen sanggahan yang terdokumentasi.
- **Verifikasi tidak dapat dinegosiasikan.** Setiap keterampilan berakhir dengan persyaratan bukti - pengujian lulus, output pembuatan, data proses (runtime). "Tampaknya benar" tidak pernah cukup.
- **Pengungkapan progresif.** `SKILL.md` adalah titik masuk. Referensi pendukung hanya dimuat saat diperlukan, meminimalkan penggunaan token.

---

## Struktur Proyek

```
agent-skills/
├── skills/                            # 24 keterampilan (23 siklus hidup + 1 meta)
│   ├── interview-me/                  #   Define
│   ├── idea-refine/                   #   Define
│   ├── spec-driven-development/       #   Define
│   ├── planning-and-task-breakdown/   #   Plan
│   ├── incremental-implementation/    #   Build
│   ├── context-engineering/           #   Build
│   ├── source-driven-development/     #   Build
│   ├── doubt-driven-development/      #   Build
│   ├── frontend-ui-engineering/       #   Build
│   ├── test-driven-development/       #   Build
│   ├── api-and-interface-design/      #   Build
│   ├── browser-testing-with-devtools/ #   Verify
│   ├── debugging-and-error-recovery/  #   Verify
│   ├── code-review-and-quality/       #   Review
│   ├── code-simplification/           #   Review
│   ├── security-and-hardening/        #   Review
│   ├── performance-optimization/      #   Review
│   ├── git-workflow-and-versioning/   #   Ship
│   ├── ci-cd-and-automation/          #   Ship
│   ├── deprecation-and-migration/     #   Ship
│   ├── documentation-and-adrs/        #   Ship
│   ├── observability-and-instrumentation/ # Ship
│   ├── shipping-and-launch/           #   Ship
│   └── using-agent-skills/            #   Meta: cara menggunakan paket ini
├── agents/                            # 4 persona spesialis
├── references/                        # 7 daftar periksa tambahan
├── hooks/                             # Kait siklus hidup sesi
├── .claude/commands/                  # 8 perintah slash (Claude Code)
├── .gemini/commands/                  # 8 perintah slash (Gemini CLI)
├── commands/                          # 8 perintah slash (Antigravity CLI)
├── plugin.json                        # Manifes plugin Antigravity
└── docs/                              # Panduan pengaturan per alat
```

---

## Mengapa Keterampilan Agen?

Agen pengodean AI menggunakan jalur terpendek sebagai bawaan - yang sering kali berarti melewati spesifikasi, pengujian, tinjauan keamanan, dan praktik yang membuat perangkat lunak dapat diandalkan. Agent Skills memberi agen alur kerja terstruktur yang menerapkan disiplin yang sama seperti yang dibawa senior engineer ke dalam kode produksi.

Setiap keterampilan mengkodekan penilaian rekayasa yang dimenangkan dengan susah payah: *kapan* menulis spesifikasi, *apa* yang harus diuji, *bagaimana* meninjau, dan *kapan* merilis. Ini bukan prompt biasa - mereka adalah alur kerja berbasis proses dan berpendapat (opinionated) yang membedakan kualitas produksi dari kualitas prototipe.

Keterampilan menanamkan praktik terbaik dari budaya rekayasa Google — termasuk konsep dari [Rekayasa Perangkat Lunak di Google (SWE Book)](https://abseil.io/resources/swe-book) dan panduan praktik rekayasa Google. Anda akan menemukan Hukum Hyrum dalam desain API, Aturan Beyonce dan piramida pengujian dalam pengujian, penentuan ukuran perubahan dan norma kecepatan ulasan dalam ulasan kode, Pagar Chesterton dalam penyederhanaan, pengembangan berbasis trunk dalam alur kerja git, Shift Left dan bendera fitur di CI/CD, dan keterampilan penghentian khusus yang memperlakukan kode sebagai kewajiban. Ini bukan prinsip abstrak — mereka disematkan secara langsung ke dalam alur kerja langkah-demi-langkah yang diikuti agen.

---

## Bagaimana perbandingannya

Penasaran bagaimana ini sebanding dengan [Superpowers](https://github.com/obra/superpowers) atau [Keterampilan Matt Pocock](https://github.com/mattpocock/skills)? Lihat **[docs/comparison.md](docs/comparison.md)** untuk tinjauan jujur dan berdampingan tentang bagaimana ketiganya dibentuk secara berbeda dan kapan harus menggunakan masing-masing — termasuk tautan ke eksperimen head-to-head yang terkontrol [pengiriman lebih cepat, pemikiran lebih aman](https://www.linkedin.com/pulse/superpowers-vs-agent-skills-faster-shipping-safer-reasoning-om-mishra-dzakf/).

---

## Berkontribusi

Keterampilan harus **spesifik** (langkah-langkah yang dapat ditindaklanjuti, bukan saran samar), **dapat diverifikasi** (kriteria keluar yang jelas dengan persyaratan bukti), **teruji di lapangan** (berdasarkan alur kerja nyata), dan **minimal** (hanya yang diperlukan untuk memandu agen).

Lihat [docs/skill-anatomy.md](docs/skill-anatomy.md) untuk spesifikasi format dan [CONTRIBUTING.md](CONTRIBUTING.md) untuk pedoman.

---

## Tim

agent-skills dibangun dan dikelola oleh:

| | Nama | GitHub | Peran |
|---|------|--------|------|
| <img src="https://github.com/addyosmani.png?size=120" width="60" height="60" alt="Addy Osmani"> | **Addy Osmani** | [@addyosmani](https://github.com/addyosmani) | Pembuat |
| <img src="https://github.com/federicobartoli.png?size=120" width="60" height="60" alt="Federico Bartoli"> | **Federico Bartoli** | [@federicobartoli](https://github.com/federicobartoli) | Kolaborator |
| <img src="https://github.com/nucliweb.png?size=120" width="60" height="60" alt="Joan León"> | **Joan León** | [@nucliweb](https://github.com/nucliweb) | Kolaborator |

---

## Lisensi

MIT - gunakan keterampilan ini dalam proyek, tim, dan alat Anda.
