# HANDOVER MASTER — RALLY ENGINE (baca-dulu untuk chat baru) · 2026-07-23

**Ini satu-satunya pintu masuk. File HANDOVER_CHAT_BARU_2026-07-20/21/22 + ADDENDUM adalah arsip sejarah — jangan baca dulu sebelum dokumen ini.**

---

## 0. APA SISTEM INI (1 paragraf)

Mesin penulis-konten kontes Rally (app.rally.fun) untuk akun **@il3nnn** (userXId 50337469). User mengetik `/rally <alamat_campaign> misi N`, engine menjalankan pipeline penuh: tarik data dari API → census pool → pilih jangkar 0%-saturasi → tulis → QA skrip → stress test → Q&A pack → serahkan blok post ke user. **User yang memposting manual; engine tidak pernah memposting.** Target = skor juri maksimal (7 kategori) dengan klaim jujur (range + ceiling, tanpa janji "pasti").

## 1. VERSI KEBENARAN (penangkal bingung #1)

Folder bernama `RALLY_ENGINE_v3.1` dan zip lama bernama `v3.7` — **nama itu historis, jangan dijadikan acuan versi.** Acuan hidup:
- **Doc/lexicon: `RALLY_ENGINE_v3.1/REAL_DEDUCTION_LEXICON.md` v2.3** (18 entry D-01..D-18 + Hukum #1-5). Changelog lengkap: `VERSION.txt`.
- **Pipeline: `RALLY_ENGINE_v3.1/skills/33_LEAN_MODE.md`** (7 langkah + LEAN 1.1-1.7).
- **Mesin penegak closure: `rally_run/TOOLS/closure_check.py` v1.2** (13 cek; CEK6 mewajibkan SEMUA entry lexicon ter-walk, dibaca dari disk).
- Jika zip ini konflik dengan apapun: **DOKUMEN DI DALAM ZIP INI ADALAH KEBENARAN.** Jika ada workspace hidup: **disk workspace = kebenaran, zip = snapshot.**

## 2. STARTUP WAJIB (tiap giliran bicara)

1. `python3 rally_run/TOOLS/reconcile.py` — SELALU aksi pertama (jawab "N utuh").
2. Selesai build/edit apa pun: `python3 rally_run/TOOLS/checkpoint.py "<deskripsi>"`.
3. Sebelum mengaku "run selesai": `python3 rally_run/TOOLS/closure_check.py <run_dir> <deliverable_dir> --mission mission-N` → wajib 13/13.
Workspace limit 110MB; folder cache/build tak ikut snapshot.

## 3. ALUR `/rally <alamat> misi N` (ringkas; detail = skills/33)

1. Fetch verbatim: `app.rally.fun/api/submissions?campaignAddress=<addr>&missionId=mission-N&limit=100&offset=<n>` (header User-Agent; mission brief ada di kolom `mission` tiap baris). Tulis CAMPAIGN_FIELDS_VERBATIM.md + **SEMUA batas periode** (P0, P1, ... dari periodLengthDays).
2. Panen teks pool via `api.fxtwitter.com/status/<tweetId>` (file-nya JSON — ukur field `text`, BUKAN panjang file; pelajaran instrumen 2026-07-23).
3. Census: rate per bucket (EP **dan** TQ, semua-data — dilarang winner-only), saturasi tema, base rates. Jalankan `rally_run/VERDICT_MINER/verdict_miner.py <subs.json> "<Nama>"` (L1).
4. ≥2 kandidat tertulis di CANDIDATES.md + keputusan (user memilih/mendelegasikan).
5. Draft → QA skrip hard-gates (tiru pola `qa_3D84.py` dari run sebelumnya) → **KB-sweep** → stress test walk **SEMUA D-01..D-18** + hostile-10 + **TASTE-PASS** (boleh "N/A — genre bukan rasa") + **TORCH-TEST** (jawaban tunjuk kalimat) → klasifikasi STRONG/WATCH.
6. QNA: **baca skills/21, 22, 23 dari disk DULU** → 20 pasangan (4SP/5CH/5TD/4HT/2RE), Q 160-260c tanpa titik dua, A ≤280c, SP quote verbatim 100%, ranking + qa_ranking.json, review per-pair ≥4.
7. Deliverable WAJIB di `konten/<NamaCampaign>/mission-N/`: content.txt + QNA_PACK.md + combined.md + SHIP_PACKAGE.md + qa_ranking.json. Blok post di ```text harus **BYTE-IDENTICAL** dengan content.txt.
8. Prediction jujur: base-rate pool + range + ceiling + LAW 6. Dilarang "pasti".

## 4. PAGAR YANG TIDAK BOLEH DILANGGAR

- **PAGAR-1:** konten lolos-QA hanya berubah bila (a) pelanggaran gate mekanis, (b) langgar entry PORTABLE lexicon, (c) editorial murni dideklarasikan "rasa, bukan data". Dilarang membedah atas sinyal statistik tunggal.
- **PAGAR-2:** setelah blok diserahkan user (SHIP), content.txt BEKU. Revisi hanya atas perintah user → naik versi (v2, v3...) → blok lama dinyatakan kedaluwarsa. Semua versi disimpan.
- **Klausul anti-template #14:** lexicon = daftar PENOLAK, bukan mesin tulis.
- **Hukum #5 (doktrin naik):** ≥4/5 pool + ≥5pp + n≥30 + counterexample-check + instrumen dideklarasi + **gas user**.
- **Prinsip user:** "hal yang tidak mempengaruhi kualitas konten kita abaikan" — tapi setiap langkah wajib TERTANGANI TERTULIS (dijalankan ATAU ditunda-dengan-keputusan; senyap = pelanggaran).
- **THE OATH (skills/20):** jawab dari data (grep/skap/API), bukan ingatan; akui seketika; koreksi ditulis, tak ada yang dihapus; koreksi status dari user SELALU menang.
- Copy publik: 0 em dash (—), 0 en dash (–), 0 semicolon (di seluruh file deliverable, bukan cuma blok).

## 5. PETA FILE

| Lokasi | Isi |
|---|---|
| `RALLY_ENGINE_v3.1/` | skills 00-35, lexicon, VERSION.txt, PROOF_AND_LESSONS.md |
| `rally_run/TOOLS/` | reconcile.py, checkpoint.py, closure_check.py |
| `rally_run/MEGA_TIER_A/` | 122k submisi (jsonl.gz), katalog 280 campaign, 5 pool Tier-B teks penuh EP4-5, tierb_epprose — sumber semua angka universe |
| `rally_run/VERDICT_MINER/` | miner + kamus weakness juri |
| `rally_run/run-*/` | folder proses tiap run (EVIDENCE_LOG = sumber kebenaran run) |
| `konten/` | deliverable beku per campaign/misi |

## 6. KEADAAN SAAT ZIP INI DIBUAT (2026-07-23 sore WITA)

- **v3 GenLayer m1 (tweet 2080135549705482657): LIVE, 7/7 kategori max, atemporal 2.70, rank 9/213; SYNCED.** Settlement P0: 19:00 WITA hari ini. v1 (4.3158 all-max) hilang dari feed — bukti banding: `rally_run/BANDING_GenLayer_m1_evidence.md`.
- **Antrian beku siap posting:** Last Tweet m0 (`konten/Your_Last_Tweet/mission-0/`, P0 tutup 06:00 WITA 24 Jul) · Origin Story m0 (`konten/The_Origin_Story/mission-0/`, P0 06:00 WITA 24 Jul) · Wingston m1 (25 Jul 06:00) · Internet Court m0 + Court of Internet m0 (25 Jul 19:30, quote-tweet per SHIP masing-masing).
- **run-e873-m0 (Last Tweet):** closure 13/13; koreksi-1/2/3 di EVIDENCE_LOG (bucket≠range; EP+TQ semua-data; instrumen-baris-vs-kalimat).
- **run-3D84-m0 (Origin Story):** T1 arisan, 1373c, closure 13/13, QNA ALL PASS.
- **QNA R19-R20** di setiap pack = SIMULATED_ARCHETYPE — deploy HANYA bila komentar organik cocok (CONDITIONAL_ORGANIC_MATCH_ONLY).
- **API penting:** `app.rally.fun/api/campaigns?page=N&limit=50` (280) · `/api/submissions?campaignAddress=&limit=100&offset=` (±500 maks; `&missionId=` jalan) · UserAgent WAJIB.

## 7. KESALAHAN UMUM CHAT BARU (FAQ)

- **"Kenapa v3.1, v3.7, v2.3 beda-beda?"** → lihat §1. Nama historis vs versi kebenaran.
- **"Angka saya beda dari catatan!"** → cek instrumen dulu (file JSON vs field text; winner-only vs semua-data; rate vs median). Instrumen menentukan jawaban (lexicon D-12).
- **"Boleh perbaiki konten beku yang sudah dikirim user?"** → TIDAK. PAGAR-2. Perintah user eksplisit mengalahkan pagar (pagar mengingatkan, bukan memenjarakan) — tapi selalu naikkan versi + catat.
- **"Doktrin baru dari data mining, langsung pasang?"** → TIDAK. Hukum #5 + diskusi + gas user.
- **"Klaim peluang tinggi biar user senang?"** → DILARANG. 0/324 pool mendekati 100%; prediksi = range + ceiling + LAW 6.

## 8. CHANGELOG v3.7 → ZIP INI (v3.8, 2026-07-23)

1. **HANDOVER MASTER ini** — pintu masuk tunggal (5 handover lama = arsip).
2. Lexicon v2.1→v2.3: D-15/16/17 (v2.1), Hukum #5 + TORCH-TEST (v2.2), D-18 (v2.3). Skill 33 kini menunjuk D-01..D-18.
3. closure_check.py v1.1→v1.2: 9→13 cek (semua-entry-lexicon, TORCH, TASTE-PASS, miner, periode).
4. Data baru: run-e873-m0 + run-3D84-m0 lengkap; v3 GenLayer live max-skor; koreksi instrumen terdokumentasi.
5. Temuan tambang Tier-B (di lexicon + run e873): TQ↔EP 0.365, P(EP5|TQ5) 14.6%, you-address +21pp, ritme-pendek +17pp, lantai-800, FP=0 −7pp; register-promosi DITOLAK (catat-mati); ML ceiling AUC ~0.65 → tidak ada "pasti EP5".

---

# ADDENDUM SORE 2026-07-23 (setelah zip v3.8) — BACA SETELAH BAGIAN UTAMA

## Run baru selesai: Internet Court Is Here mission-0 → RUN V2 (dari awal, atas perintah user)
- Run: rally_run/run-7bE2-m0-v2 · Deliverable: konten/Internet_Court_Is_Here/mission-0-v2/ · Closure **13/13 v1.2**.
- Konten FINAL 1446c: cerita kakak titip-jual 40 sepatu (0 saturasi) → jembatan agen → mentions @GenLayer + @courtofinternet → 1 '?'.
- v1 beku (paman/Forbes, FP=0) DIARSIP: konten/Internet_Court_Is_Here/ARCHIVE_mission-0_v1_beku_unposted/ (pelajaran; tidak dihapus).
- Pelajaran penting run ini: (a) arsip teks lama TRUNCATED → selalu verifikasi instrumen (KOREKSI-1); (b) v1 ternyata tetangga fingerprint terkunci kita sendiri → patch tidak menyelamatkan, run dari awal benar; (c) pool ini membayar 1200-1600c dgn struktur ketat.
- Posting format: QUOTE x.com/GenLayer/status/2075601367092072877. Deadline Sabtu 25 Jul 20:30 WITA (P1 TERAKHIR).

## Perubahan aset
- RALLY_ENGINE_v3.7 zip: DIHAPUS (watchdog ruang) → tercatat KONTEN_DELETION_LOG. v3.8 → DIGANTIKAN **v3.9** (zip terbaru, superset, termasuk run-7bE2-m0-v2).

## Agenda berjalan (urut waktu, WITA)
1. HARI INI 19:00 — settlement GenLayer m1 (cek v3 masuk distribusi; kalau tidak → BANDING pack rally_run/BANDING_GenLayer_m1_evidence.md).
2. MALAM INI sebelum 06:00 (24 Jul) — POST Your Last Tweet (konten/Your_Last_Tweet/mission-0/combined.md) + Origin Story (konten/The_Origin_Story/mission-0/combined.md). Keduanya P0 tutup 22:00Z.
3. Secepatnya setelah itu — POST Internet Court v2 (Quote). Setelah tiap post: verifikasi baris API + deploy QNA (R01-R18 on match; R19-R20 hanya organic match).
4. 25 Jul 06:00 — Wingston m1 (beku: konten/Meet_Wingston_Agent/mission-1/).
5. 25 Jul 19:30 — Court of Internet 0x6576 m0 (BEKUNYA BELUM DIREVIEW — review dulu dengan metode data-lokal seperti review Internet Court).
6. Misi baru tersedia: Stump (28 Jul), CTL (28), FakeNews (29), Confess (29), The Mic/Twist (1 Agu), Easy Money (3), Get Rebate (4, maxsub 1).

## CATATAN DIET (sore): run-6133, run-6133-v2, USDC_LEGACY_2026-07-21, run-7bE2-m0 sekarang HANYA ada di zip v3.9 (workspace 71MB). Snapshot SNAP_* & evidence kunci tetap di workspace.

## CATATAN CEK13: closure_check SEKARANG v1.3 (14 cek) — user-catch blok QNA jadi cek permanen. Semua run lama terverifikasi lolos 14/14.
