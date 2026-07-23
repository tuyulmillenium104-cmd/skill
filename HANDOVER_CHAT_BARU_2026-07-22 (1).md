# 🤝 HANDOVER — UNTUK CHAT BARU (2026-07-22, KONSOLIDASI — menggantikan handover 07-20/21 + addendum)

## 0. CARA PAKAI DI CHAT BARU (3 langkah)
1. **Upload dua file:** `RALLY_ENGINE_v3.6_TRANSFER_2026-07-22.zip` + file handover ini.
2. **Perintahkan:** *"Ekstrak zip ke workspace, lalu baca URUTAN BACA WAJIB di handover. Jangan melakukan apa pun sebelum selesai membaca. Jawab dari file, bukan ingatan."*
3. **Tes cepat 30 detik** (agen yang benar-benar membaca pasti bisa jawab; yang ngaco suruh baca ulang):
   - "Skill 34 dan 35 tugasnya apa, bedanya apa?" → 34 = pencegahan (dump sementara, zip sekali pakai, watchdog 110 MB, redundansi DELIV_, hapus-butuh-bukti); 35 = pemulihan (checkpoint tiap build + reconcile tiap awal giliran; SNAP_* tak pernah dihapus; manifest = kebenaran).
   - "Kenapa folder baru di konten/ sempat menghilang 7x dan apa fix-nya?" → snapshot best-effort ~128 MB, workspace 144 MB → diet ke 53 MB (23 dump API + 4 zip lama); aturan empris: file flat di direktori eksis = persisten, direktori baru = menguap (pra-diet).
   - "GenLayer sudah disubmit belum, deadline kapan, paket di mana?" → BELUM (koreksi user 22 Jul); single-periode tutup 23 Jul 19:00 WITA; paket `konten/How_GenLayer_Verdict/` + flat `AKTIF_1/2_GenLayer_*`.
   - "Hipotesis absolute-judging statusnya apa, bukti terakhir?" → BERTAHAN 5/5 (snapshot 22 Jul: vektor + attoRaw beku saat pool tumbuh 1.4-2x; rank hanya bergeser relatif).
   - Info tambahan kalibrasi lama tetap sah di handover 07-21 (arsip historis).

⚠️ **Jujur tentang jaminan:** zip ini = sumber disiplin. Agen baru yang MEMBACA dan MEMATUHI akan berperilaku sama; tidak ada jaminan 100% — karena itu tes no.3 wajib.

---

## 0b. PROTOKOL ANTI-STUCK (kalau chat macet/error)
1. Berhenti di chat macet — jangan paksa.
2. Chat baru → upload zip + handover ini → perintah seperti bagian 0.
3. Semua pekerjaan aman di file (Skill 20: evidence ditulis SAAT terjadi). Lanjutkan dari EVIDENCE_LOG run terakhir + SNAPSHOT_MANIFEST (`python3 rally_run/TOOLS/reconcile.py`).
4. Kebiasaan: setelah kerja besar minta **"rebuild zip"**; chat ringan (ringkasan di chat, detail di file); satu chat satu fokus itu normal.

---

## 1. URUTAN BACA WAJIB (dari disk, jangan ingatan)
1. `RALLY_ENGINE_v3.1/RALLY_FUNDAMENTAL_LAW_v3.1.md`
2. `skills/20_OATH_AND_ENFORCEMENT.md`
3. `RALLY_EFFECTIVE_WORKFLOW_v3.1.md`
4. `REAL_DEDUCTION_LEXICON.md` (v1.6, D-01..D-11)
5. `PROOF_AND_LESSONS.md`
6. `skills/33_LEAN_MODE.md` (mode aktif)
7. `skills/34_WORKSPACE_HYGIENE.md` + `skills/35_SNAPSHOT_PROTOCOL.md` ⭐ BARU 22 Jul
8. `VERSION.txt`
`skills/EP_GATE_TEMPLATE_ORIGINAL.txt` = historis, JANGAN dipakai.

## 2. SIAPA USER-MU
Autor engine. Stress-tester kejujuran — tangkapannya hampir selalu isu nyata (sesi 22 Jul: status submit GenLayer salah-catat ditangkapnya). Ekspektasi: akui instan → bukti data → perbaiki formal → dokumentasikan (koreksi tidak dihapus). Bahasa: Indonesia santai, **SINGKAT, jelas, jujur**. Klaim terlarang: guaranteed winner/EP5; prediksi = range + ceiling + LAW 6. Keputusan doktrin: diskusi dulu, diratifikasi via "gas".

## 3. IDENTITAS TERVERIFIKASI
- GitHub: `tuyulmillenium104-cmd` (9 repos) · X: **@il3nnn** (1177 followers per fxtwitter 22 Jul → lolos gate 500 & 1000).
- GitHub re-verify: `curl https://api.github.com/users/tuyulmillenium104-cmd`.

## 4. MODE RUN
LEAN (Skill 33, default `/rally <addr>`) — verifikasi penuh, dokumentasi ringkas. FULL wajib untuk pemulihan Zero-Tolerance. Closure: `rally_run/TOOLS/closure_check.py` **v1.1** = **CEK0 (⌖workspace ≤110 MB) + 8 cek**; ATTEST (makna) = reviewer manusia.

## 5. ⭐ PAPAN STATUS FINAL 2026-07-22 (di sinilah kamu lanjut)

### A. BELUM diposting — URUTAN URGENSI
| # | Campaign/misi | Deadline WITA | Lokasi paket | Catatan kritis |
|---|---|---|---|---|
| 1 | **GenLayer m0+m1** `0x6133...417C` | **HARI INI 23 Jul 19:00** (single periode) | `konten/How_GenLayer_Verdict/mission-0/v2/` + `mission-1/` + flat `AKTIF_1/2_GenLayer_*` di `konten/` root | Keduanya QUOTE-mission: m0 quote 2072652114891882570, m1 quote 2073747067868971088. Mention @GenLayer. Gate 500 ✓ (1177). |
| 2 | Wingston m0 `0x6EB4...362dB` | 25 Jul 06:00 | `konten/Meet_Wingston_Agent/mission-0/` | Gate R05: user TES Wingston dulu (incl 1 pertanyaan Bahasa Indonesia) + screenshot = media, SEBELUM posting. |
| 3 | Wingston m1 | 25 Jul 06:00 | `konten/Meet_Wingston_Agent/mission-1/` (run-6EB4-m1, closure 9/9) | Sama R05. Content 978c QA 20/20 QNA 26/26. |
| 4 | Court of Internet m0 `0x6576...667` | 25 Jul 19:30 (P1 terakhir) | `konten/Court_of_Internet/mission-0/` + `DELIV_*` di run-6576-m9 | WAJIB: QUOTE tweet 2075565797007609898 + mention literal `@InternetCourt` (bukan @courtofinternet). Target kalahkan legacy 3.5765. |

### B. TERPOSTING & TERMONITOR (vec kita beku per 22 Jul — ABSOLUTE-JUDGING BERTAHAN 5/5)
| Campaign | attoRaw | Rank kini | Catatan |
|---|---|---|---|
| STUMP 0x8E04 | 2.840 beku | 44/98 | sampai 28 Jul |
| CTL 0x1474 | 3.507 beku | 26/106 | sampai 28 Jul |
| FUD 0x5e0D | 3.5520 beku | 12/95 | RQ 0/5 TETAP pasca-cutoff → verdict beku, tak ada refresh balasan |
| CONFESS 0x9aD6 | 3.5005 beku | 29/96 | P1 s.d. 29 Jul |
| FAKENEWS 0x1041 | 3.7300 beku | 7/95 | P1 s.d. 29 Jul |
Legacy ternilai (VN 3.2522, Cancel 3.4435 silver) + USDC legacy 07-21 di `rally_run/USDC_LEGACY_2026-07-21/`.

### C. SETELAH USER POSTING (prosedur)
Catat tweetId → GOLD_STANDARD_TRACKER + baseline monitor; verdict mendarat → verdict-intake, bandingkan prediksi (HIT/MISS → lexicon), kaku-audit (LEAN 1.7 #16).

## 6. ENGINE & WORKSPACE STATE (22 Jul)
- Skills: 00-33 (+34, 35). Lexicon v1.6. Versi closure v1.1 (9 cek).
- Workspace 67 MB (pasca-diet; dump mentah = re-fetch publik). Log: `rally_run/DIET_LOG_2026-07-22.md`, `KONTEN_DELETION_LOG_2026-07-22.md`.
- Protokol snapshot (Skill 35) HIDUP: `reconcile.py` tiap awal giliran (uji perdana 23 Jul pagi: 0 dipulihkan, 73 utuh), `checkpoint.py` tiap build; 73 file `SNAP_*` + `SNAPSHOT_MANIFEST.json` di `rally_run/`.
- Aturan empris persistence (pra-diet, tercatat di Skill 35): direktori baru menguap; file flat di direktori eksis persisten. Pasca-diet: normal.
- `VM/STRUCT_dataset`: BLOCKED menunggu user re-upload (`VM/STRUCT_dataset/build_dataset.py` siap).

## 7. API
Campaign: `app.rally.fun/api/campaigns/{addr}` · Submissions: `.../api/submissions?campaignAddress={addr}&limit=100&offset=N` · Tweet: `api.fxtwitter.com/status/{tweetId}` · User: `api.fxtwitter.com/il3nnn`.

## 8. LOKASI KUNCI
Paket aktif: `konten/` (7 folder) + flat `AKTIF_*`. Cadangan anti-hilang: `rally_run/run-*/DELIV_*` & `ARCHIVE_*` + `SNAP_*`. TOOLS: closure_check, checkpoint, reconcile, restore_konten, archive_then_delete, verdict_miner. Legacy gold verdicts: `rally_run/USDC_LEGACY_2026-07-21/`.
