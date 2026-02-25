<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=2.0">
<title>QRG Digital – Pengkajian Nyeri Pediatrik PICU | RSHS Bandung</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800;900&display=swap" rel="stylesheet">
<style>
  :root {
    --pcpot:  #1e6fa8;
    --green:  #2e9e6b;
    --orange: #e07b00;
    --red:    #c0392b;
    --purple: #6a3093;
    --bg:     #eef2f7;
    --card:   #ffffff;
    --text:   #1a2a3a;
    --muted:  #6c7a89;
    --shadow: 0 2px 12px rgba(0,0,0,0.08), 0 1px 3px rgba(0,0,0,0.06);
    --shadow-lg: 0 8px 32px rgba(0,0,0,0.12), 0 2px 8px rgba(0,0,0,0.08);
    --radius: 16px;
    --radius-sm: 10px;
  }

  * { box-sizing: border-box; margin: 0; padding: 0; -webkit-tap-highlight-color: transparent; }

  html { scroll-behavior: smooth; }

  body {
    font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Arial, sans-serif;
    background: var(--bg);
    color: var(--text);
    min-height: 100vh;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
  }

  /* ===== NAV ===== */
  .tab-nav {
    position: sticky; top: 0; z-index: 100;
    background: #0d1721;
    display: flex; overflow-x: auto;
    scrollbar-width: none;
    padding: 8px 8px 10px;
    gap: 5px;
    box-shadow: 0 4px 20px rgba(0,0,0,0.45);
    border-bottom: 1px solid rgba(255,255,255,0.05);
  }
  .tab-nav::-webkit-scrollbar { display: none; }

  .tab-btn {
    flex-shrink: 0;
    padding: 8px 12px;
    font-family: inherit;
    font-size: 9.5px; font-weight: 800;
    border: none; border-radius: 50px;
    cursor: pointer; text-align: center;
    transition: all 0.2s cubic-bezier(.34,1.56,.64,1);
    white-space: nowrap;
    line-height: 1.35;
    color: rgba(255,255,255,0.42);
    background: rgba(255,255,255,0.06);
    letter-spacing: 0.3px;
    border: 1px solid transparent;
    min-width: 52px;
  }
  .tab-btn:hover {
    color: rgba(255,255,255,0.82);
    background: rgba(255,255,255,0.12);
    border-color: rgba(255,255,255,0.1);
    transform: translateY(-1px);
  }
  .tab-btn:active { transform: scale(0.96); }

  /* Per-tab active colors */
  .tab-btn[data-tab="0"].active { background: linear-gradient(135deg,#1e6fa8,#0a3d62); color:#fff; box-shadow: 0 3px 12px rgba(30,111,168,0.5); transform:translateY(-2px) scale(1.04); }
  .tab-btn[data-tab="1"].active { background: linear-gradient(135deg,#f39c12,#a04000); color:#fff; box-shadow: 0 3px 12px rgba(243,156,18,0.5); transform:translateY(-2px) scale(1.04); }
  .tab-btn[data-tab="2"].active { background: linear-gradient(135deg,#27ae60,#0e5e33); color:#fff; box-shadow: 0 3px 12px rgba(39,174,96,0.5); transform:translateY(-2px) scale(1.04); }
  .tab-btn[data-tab="3"].active { background: linear-gradient(135deg,#e74c3c,#7b0e0e); color:#fff; box-shadow: 0 3px 12px rgba(231,76,60,0.5); transform:translateY(-2px) scale(1.04); }
  .tab-btn[data-tab="4"].active { background: linear-gradient(135deg,#8e44ad,#4a1060); color:#fff; box-shadow: 0 3px 12px rgba(142,68,173,0.5); transform:translateY(-2px) scale(1.04); }
  .tab-btn[data-tab="5"].active { background: linear-gradient(135deg,#16a085,#0a4d3e); color:#fff; box-shadow: 0 3px 12px rgba(22,160,133,0.5); transform:translateY(-2px) scale(1.04); }
  .tab-btn[data-tab="6"].active { background: linear-gradient(135deg,#d35400,#7d1f00); color:#fff; box-shadow: 0 3px 12px rgba(211,84,0,0.5); transform:translateY(-2px) scale(1.04); }
  .tab-btn[data-tab="7"].active { background: linear-gradient(135deg,#2980b9,#1a4e75); color:#fff; box-shadow: 0 3px 12px rgba(41,128,185,0.5); transform:translateY(-2px) scale(1.04); }

  /* dot indicator bawah aktif */
  .tab-btn.active::after {
    content: '';
    display: block;
    width: 4px; height: 4px;
    border-radius: 50%;
    background: rgba(255,255,255,0.8);
    margin: 3px auto 0;
  }

  /* ===== PAGES ===== */
  .page { display: none; padding: 14px; max-width: 600px; margin: 0 auto; animation: fadeIn 0.18s ease; }
  .page.active { display: block; }

  @keyframes fadeIn { from { opacity:0; transform:translateY(4px); } to { opacity:1; transform:translateY(0); } }

  /* ===== COVER ===== */
  .cover-hero {
    background: linear-gradient(135deg, #1a2a3a 0%, #1e6fa8 55%, #2e9e6b 100%);
    border-radius: var(--radius);
    padding: 28px 20px;
    color: #fff;
    text-align: center;
    margin-bottom: 14px;
    position: relative; overflow: hidden;
  }
  .cover-hero::before {
    content: '';
    position: absolute; inset: 0;
    background-image: url("data:image/svg+xml,%3Csvg width='60' height='60' viewBox='0 0 60 60' xmlns='http://www.w3.org/2000/svg'%3E%3Cg fill='none'%3E%3Cg fill='%23ffffff' fill-opacity='0.04'%3E%3Cpath d='M36 34v-4h-2v4h-4v2h4v4h2v-4h4v-2h-4zm0-30V0h-2v4h-4v2h4v4h2V6h4V4h-4zM6 34v-4H4v4H0v2h4v4h2v-4h4v-2H6zM6 4V0H4v4H0v2h4v4h2V6h4V4H6z'/%3E%3C/g%3E%3C/g%3E%3C/svg%3E");
  }
  .cover-badge {
    display: inline-block;
    background: rgba(255,255,255,0.2);
    border: 1px solid rgba(255,255,255,0.3);
    border-radius: 50px;
    padding: 4px 14px;
    font-size: 10px; font-weight: 700;
    letter-spacing: 1px; text-transform: uppercase;
    margin-bottom: 12px; position: relative;
  }
  .cover-title {
    font-size: 22px; font-weight: 900;
    line-height: 1.2; margin-bottom: 6px; position: relative;
  }
  .cover-sub { font-size: 12px; opacity: 0.8; margin-bottom: 16px; position: relative; }
  .cover-chips { display: flex; flex-wrap: wrap; gap: 6px; justify-content: center; position: relative; }
  .chip { padding: 5px 12px; border-radius: 50px; font-size: 11px; font-weight: 700; color: #fff; }

  /* ===== CARDS ===== */
  .info-card {
    background: var(--card);
    border-radius: var(--radius);
    padding: 14px 16px;
    margin-bottom: 12px;
    box-shadow: var(--shadow);
    transition: box-shadow 0.2s;
  }
  .info-card h3 {
    font-size: 11px; font-weight: 800;
    text-transform: uppercase; letter-spacing: 0.6px;
    color: var(--muted); margin-bottom: 10px;
  }
  .meta-row { display: flex; justify-content: space-between; font-size: 12px; padding: 5px 0; border-bottom: 1px solid #f0f2f5; }
  .meta-row:last-child { border-bottom: none; }
  .meta-key { font-weight: 700; color: var(--muted); }
  .meta-val { color: var(--text); font-weight: 600; text-align: right; max-width: 62%; }

  /* ===== PAGE TITLE ===== */
  .page-title { font-size: 18px; font-weight: 900; margin-bottom: 4px; letter-spacing: -0.3px; }
  .page-desc { font-size: 12px; color: var(--muted); margin-bottom: 14px; font-weight: 500; }

  /* ===== FLOWCHART ===== */
  .flow-box {
    border-radius: 12px; padding: 12px 16px;
    text-align: center; font-size: 13px; font-weight: 800;
    margin-bottom: 6px;
  }
  .flow-start { background: #1a2a3a; color: #fff; }
  .flow-arrow { text-align: center; font-size: 20px; color: var(--muted); margin: 2px 0; }
  .flow-question {
    background: #fff3cd; border: 2px solid #ffc107;
    border-radius: 50px; padding: 11px 18px;
    text-align: center; font-size: 13px; font-weight: 800;
    margin-bottom: 6px; color: #7c5e00;
  }

  /* Alur bercabang dua kolom */
  .branch-row {
    display: grid; grid-template-columns: 1fr 1fr;
    gap: 10px; margin-bottom: 6px;
  }
  .branch-box {
    border-radius: 12px; padding: 13px 10px;
    color: #fff; text-align: center;
    position: relative;
  }
  .branch-box .b-label {
    font-size: 10px; font-weight: 700; opacity: 0.85;
    text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px;
  }
  .branch-box .b-title {
    font-size: 15px; font-weight: 900; margin-bottom: 4px;
  }
  .branch-box .b-sub {
    font-size: 10px; opacity: 0.88; line-height: 1.4;
  }

  /* Converge arrow row */
  .converge-row {
    display: grid; grid-template-columns: 1fr 1fr;
    gap: 10px; margin-bottom: 2px;
  }
  .converge-arrow {
    text-align: center; font-size: 22px; color: var(--muted);
  }

  /* P-CPOT FOCUS box */
  .pcpot-focus {
    background: linear-gradient(135deg, #1a2a3a 0%, #1e6fa8 100%);
    border-radius: 14px; padding: 18px 20px;
    color: #fff; text-align: center; margin-bottom: 12px;
    border: 2px solid #4db6f7;
    box-shadow: 0 4px 20px rgba(30,111,168,0.3);
  }
  .pcpot-focus .pf-badge {
    display: inline-block;
    background: rgba(255,255,255,0.2);
    border-radius: 50px; padding: 3px 14px;
    font-size: 10px; font-weight: 800; letter-spacing: 1px;
    text-transform: uppercase; margin-bottom: 8px;
  }
  .pcpot-focus .pf-name { font-size: 28px; font-weight: 900; letter-spacing: 1px; }
  .pcpot-focus .pf-full { font-size: 11px; opacity: 0.85; margin-bottom: 10px; }
  .pcpot-focus .pf-chips { display: flex; gap: 8px; justify-content: center; flex-wrap: wrap; }
  .pcpot-focus .pf-chip {
    background: rgba(255,255,255,0.2);
    border-radius: 6px; padding: 4px 10px;
    font-size: 11px; font-weight: 800;
  }

  .special-card {
    border-radius: 12px; padding: 13px 15px;
    margin-bottom: 10px; color: #fff;
  }
  .special-card h4 { font-size: 13px; font-weight: 800; margin-bottom: 5px; }
  .special-card p { font-size: 12px; opacity: 0.92; line-height: 1.5; }

  /* ===== INSTRUMENT TABLES ===== */
  .instrument-card {
    background: var(--card);
    border-radius: var(--radius);
    overflow: hidden;
    margin-bottom: 14px;
    box-shadow: var(--shadow);
  }
  .inst-header { padding: 14px 18px; color: #fff; }
  .inst-header .inst-name { font-size: 22px; font-weight: 900; margin-bottom: 2px; }
  .inst-header .inst-full { font-size: 11px; opacity: 0.85; }
  .inst-header .inst-meta { display: flex; gap: 14px; margin-top: 10px; }
  .inst-meta-item { font-size: 11px; }
  .inst-meta-item span { font-weight: 900; font-size: 16px; display: block; }

  table.domain-table { width: 100%; border-collapse: collapse; font-size: 11.5px; }
  table.domain-table thead tr { background: #f4f7fa; }
  table.domain-table th {
    padding: 8px 10px; text-align: left;
    font-size: 10px; font-weight: 800;
    text-transform: uppercase; color: var(--muted);
    letter-spacing: 0.4px;
  }
  table.domain-table td {
    padding: 10px; border-top: 1px solid #eef0f3; vertical-align: top;
  }
  table.domain-table tr:hover { background: #f7f9fc; }
  .domain-name { font-weight: 800; color: var(--text); }

  /* ===== SCORING GUIDE ===== */
  .score-band {
    border-radius: 16px; padding: 16px 18px;
    margin-bottom: 12px; color: #fff;
    box-shadow: 0 4px 16px rgba(0,0,0,0.15);
  }
  .score-band .sb-top {
    display: flex; align-items: center; gap: 12px; margin-bottom: 10px;
  }
  .score-band .sb-score {
    font-size: 30px; font-weight: 900; line-height: 1;
    flex-shrink: 0;
  }
  .score-band .sb-right {}
  .score-band .sb-label { font-size: 14px; font-weight: 800; margin-bottom: 2px; }
  .score-band .sb-freq {
    display: inline-flex; align-items: center; gap: 5px;
    background: rgba(255,255,255,0.22);
    border-radius: 50px; padding: 3px 12px;
    font-size: 11px; font-weight: 800;
  }
  .score-band ul { font-size: 12px; padding-left: 16px; }
  .score-band li { margin-bottom: 4px; opacity: 0.95; line-height: 1.45; }

  /* ===== REFERENSI ===== */
  .ref-item {
    background: var(--card);
    border-radius: 12px; padding: 13px 14px;
    margin-bottom: 10px;
    box-shadow: var(--shadow);
    border-left: 4px solid var(--pcpot);
    transition: box-shadow 0.2s, transform 0.15s;
  }
  .ref-item:hover { box-shadow: var(--shadow-lg); transform: translateX(2px); }
  .ref-num {
    font-size: 10px; font-weight: 800; color: var(--pcpot);
    text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 3px;
  }
  .ref-citation { font-size: 12px; line-height: 1.6; color: var(--text); }
  .ref-doi { font-size: 10px; color: var(--muted); margin-top: 3px; font-family: monospace; }

  .section-divider {
    text-align: center; font-size: 10px;
    font-weight: 800; text-transform: uppercase;
    letter-spacing: 1px; color: var(--muted);
    margin: 14px 0 10px;
    display: flex; align-items: center; gap: 8px;
  }
  .section-divider::before, .section-divider::after {
    content: ''; flex: 1; height: 1px; background: #dde3ea;
  }

  footer {
    text-align: center; padding: 22px 16px;
    font-size: 10px; color: var(--muted);
  }

  /* ===== MOBILE RESPONSIVE ===== */
  @media (max-width: 380px) {
    .tab-btn { padding: 7px 9px; font-size: 9px; min-width: 46px; }
    .page { padding: 10px; }
    .cover-title { font-size: 19px; }
    .branch-row { gap: 7px; }
    .field-row-2 { grid-template-columns: 1fr; }
    .domain-score-header { font-size: 11.5px; }
    .radio-desc { font-size: 10.5px; }
  }

  @media (min-width: 520px) {
    .tab-btn { padding: 8px 14px; font-size: 10px; }
  }

  /* Prevent text size adjustments on orientation change */
  @media screen and (orientation: landscape) and (max-height: 500px) {
    .tab-nav { padding: 5px 6px 7px; }
    .tab-btn { padding: 6px 10px; font-size: 9px; }
  }

  /* ===== SOP FREQ BADGE ===== */
  .sop-badge {
    display: inline-block;
    padding: 2px 9px; border-radius: 50px;
    font-size: 10px; font-weight: 800; color: #fff;
  }

  /* ===== VERSION BADGE ===== */
  .ver-badge {
    display: inline-block;
    background: #e8f4fd; color: var(--pcpot);
    border: 1.5px solid var(--pcpot);
    border-radius: 50px;
    padding: 3px 12px;
    font-size: 10px; font-weight: 800;
    margin-bottom: 8px;
  }
</style>
</head>
<body>

<nav class="tab-nav">
  <button class="tab-btn active" data-tab="0" onclick="showPage(0)">📋<br>COVER</button>
  <button class="tab-btn" data-tab="1" onclick="showPage(1)">🔀<br>ALUR</button>
  <button class="tab-btn" data-tab="2" onclick="showPage(2)">🩺<br>P-CPOT</button>
  <button class="tab-btn" data-tab="3" onclick="showPage(3)">🚨<br>TINDAK</button>
  <button class="tab-btn" data-tab="4" onclick="showPage(4)">📚<br>REFERENSI</button>
  <button class="tab-btn" data-tab="5" onclick="showPage(5)">📝<br>LEMBAR</button>
  <button class="tab-btn" data-tab="6" onclick="showPage(6)">🤝<br>HUDDLE</button>
  <button class="tab-btn" data-tab="7" onclick="showPage(7)">🖼️<br>MEDIA</button>
</nav>

<!-- =================== HALAMAN 0: COVER =================== -->
<div class="page active" id="page0">
  <div class="cover-hero">
    <div class="cover-badge">RSUP Dr. Hasan Sadikin Bandung</div>
    <div class="cover-title">QRG Digital<br>Pengkajian Nyeri<br>Pediatrik PICU</div>
    <div class="cover-sub">Quick Reference Guide — Sesuai SOP RSHS 2026</div>
    <div class="cover-chips">
      <div class="chip" style="background:rgba(30,111,168,0.85)">⭐ P-CPOT</div>
      <div class="chip" style="background:rgba(192,57,43,0.7)">SCCM 2022</div>
    </div>
  </div>

  <div class="info-card">
    <h3>Identitas Dokumen</h3>
    <div class="meta-row"><span class="meta-key">Versi</span><span class="meta-val">v2.0 — Februari 2026</span></div>
    <div class="meta-row"><span class="meta-key">Penyusun</span><span class="meta-val">Asep Rizkika Setia, A.Md.Kep</span></div>
    <div class="meta-row"><span class="meta-key">Jabatan</span><span class="meta-val">Perawat Terampil — PICU</span></div>
    <div class="meta-row"><span class="meta-key">Mentor</span><span class="meta-val">Amelia Ganefianty, S.Kep., Ners., M.Kep., Sp.Kep.MB, PhD</span></div>
    <div class="meta-row"><span class="meta-key">Coach</span><span class="meta-val">dr. Wulandari Indri Hapsari, MPH</span></div>
    <div class="meta-row"><span class="meta-key">Unit</span><span class="meta-val">RSUP Dr. Hasan Sadikin Bandung</span></div>
  </div>

  <div class="info-card">
    <h3>🎯 Fokus Instrumen Utama</h3>
    <div style="background:linear-gradient(135deg,#1a2a3a,#1e6fa8);border-radius:10px;padding:12px 14px;color:#fff;margin-bottom:8px">
      <div style="font-size:11px;font-weight:800;opacity:0.8;letter-spacing:1px;text-transform:uppercase;margin-bottom:4px">Instrumen Primer PICU RSHS</div>
      <div style="font-size:20px;font-weight:900;margin-bottom:2px">P-CPOT</div>
      <div style="font-size:11px;opacity:0.85">Pediatric Critical-Care Pain Observation Tool</div>
      <div style="display:flex;gap:6px;margin-top:8px;flex-wrap:wrap">
        <span style="background:rgba(255,255,255,0.2);border-radius:6px;padding:3px 9px;font-size:10px;font-weight:800">✅ Terintubasi</span>
        <span style="background:rgba(255,255,255,0.2);border-radius:6px;padding:3px 9px;font-size:10px;font-weight:800">✅ Tidak Terintubasi</span>
        <span style="background:rgba(255,255,255,0.2);border-radius:6px;padding:3px 9px;font-size:10px;font-weight:800">✅ Semua Usia PICU</span>
      </div>
    </div>
    <p style="font-size:12px;line-height:1.6;color:var(--muted)">
      P-CPOT berlaku untuk semua pasien anak PICU yang tidak dapat verbalisasi nyeri, baik yang terintubasi maupun tidak terintubasi.
    </p>
  </div>

  <div class="info-card">
    <h3>⏱️ Frekuensi Pengkajian — SOP RSHS</h3>
    <div style="display:flex;flex-direction:column;gap:8px">
      <div style="display:flex;align-items:center;gap:10px;background:#e8f5e9;border-radius:10px;padding:10px 12px">
        <div style="background:#27ae60;border-radius:8px;padding:6px 10px;color:#fff;font-size:18px;font-weight:900;min-width:44px;text-align:center">0–3</div>
        <div>
          <div style="font-size:12px;font-weight:800;color:#1a2a3a">Tidak Ada / Nyeri Ringan</div>
          <div style="font-size:11px;color:#27ae60;font-weight:700">🕐 Setiap 8 jam</div>
        </div>
      </div>
      <div style="display:flex;align-items:center;gap:10px;background:#fff8e1;border-radius:10px;padding:10px 12px">
        <div style="background:#f39c12;border-radius:8px;padding:6px 10px;color:#fff;font-size:18px;font-weight:900;min-width:44px;text-align:center">4–6</div>
        <div>
          <div style="font-size:12px;font-weight:800;color:#1a2a3a">Nyeri Sedang</div>
          <div style="font-size:11px;color:#e07b00;font-weight:700">🕐 Setiap 2 jam</div>
        </div>
      </div>
      <div style="display:flex;align-items:center;gap:10px;background:#fdecea;border-radius:10px;padding:10px 12px">
        <div style="background:#e74c3c;border-radius:8px;padding:6px 10px;color:#fff;font-size:18px;font-weight:900;min-width:44px;text-align:center">7–10</div>
        <div>
          <div style="font-size:12px;font-weight:800;color:#1a2a3a">Nyeri Berat</div>
          <div style="font-size:11px;color:#c0392b;font-weight:700">🕐 Setiap 1 jam</div>
        </div>
      </div>
      <div style="display:flex;align-items:center;gap:10px;background:#f3e5f5;border-radius:10px;padding:10px 12px">
        <div style="background:#7b1fa2;border-radius:8px;padding:6px 4px;color:#fff;font-size:12px;font-weight:900;min-width:44px;text-align:center">Obat<br>Baru</div>
        <div>
          <div style="font-size:12px;font-weight:800;color:#1a2a3a">Setelah Pemberian Obat Baru / Bolus</div>
          <div style="font-size:11px;color:#7b1fa2;font-weight:700">🕐 Asesmen ulang 30 menit</div>
        </div>
      </div>
    </div>
  </div>

  <div class="info-card">
    <h3>📖 Cara Penggunaan QRG</h3>
    <p style="font-size:12px;line-height:1.7;color:var(--muted)">
      Tab <b>🔀 ALUR</b> → lihat alur pengkajian nyeri. Tab <b>🩺 P-CPOT</b> → skoring instrumen utama. Tab <b>🚨 TINDAK LANJUT</b> → intervensi sesuai skor dan frekuensi monitoring SOP RSHS.
    </p>
  </div>
</div>

<!-- =================== HALAMAN 1: ALUR (BARU) =================== -->
<div class="page" id="page1">
  <div class="page-title">Alur Pengkajian Nyeri PICU</div>
  <div class="page-desc">Sesuai SOP RSHS — Instrumen utama: P-CPOT</div>

  <!-- START -->
  <div class="flow-box flow-start">👶 Pasien Anak PICU<br><span style="font-size:11px;font-weight:600;opacity:0.8">Tidak dapat verbalisasi nyeri</span></div>
  <div class="flow-arrow">↓</div>

  <!-- PERTANYAAN STATUS INTUBASI -->
  <div class="flow-question">❓ Status Ventilasi Pasien?</div>
  <div class="flow-arrow" style="opacity:0">↓</div>

  <!-- DUA CABANG -->
  <div class="branch-row">
    <div class="branch-box" style="background:linear-gradient(135deg,#1a2a3a,#1e6fa8)">
      <div class="b-label">Kondisi A</div>
      <div class="b-title">🫁 Terintubasi</div>
      <div class="b-sub">Terpasang ETT / Ventilator Mekanik — tidak dapat bicara</div>
    </div>
    <div class="branch-box" style="background:linear-gradient(135deg,#1a3a28,#2e9e6b)">
      <div class="b-label">Kondisi B</div>
      <div class="b-title">😮 Tidak Terintubasi</div>
      <div class="b-sub">Napas spontan / CPAP / HFT — tidak dapat/mau bicara</div>
    </div>
  </div>

  <!-- PANAH CONVERGE -->
  <div class="converge-row">
    <div class="converge-arrow">↘️</div>
    <div class="converge-arrow">↙️</div>
  </div>

  <!-- TITIK TEMU: P-CPOT -->
  <div class="pcpot-focus">
    <div class="pf-badge">⭐ Instrumen Utama PICU RSHS</div>
    <div class="pf-name">P-CPOT</div>
    <div class="pf-full">Pediatric Critical-Care Pain Observation Tool</div>
    <div class="pf-chips">
      <span class="pf-chip">Skor 0–10</span>
      <span class="pf-chip">Threshold ≥ 4</span>
      <span class="pf-chip">5 Domain</span>
    </div>
  </div>

  <!-- PENJELASAN DOMAIN BERBEDA -->
  <div class="info-card" style="margin-bottom:10px;background:#eaf3fb;border-left:4px solid var(--pcpot)">
    <h3>📌 Perbedaan Domain P-CPOT</h3>
    <div style="display:grid;grid-template-columns:1fr 1fr;gap:8px;margin-top:4px">
      <div style="background:#1a2a3a;border-radius:10px;padding:10px;color:#fff">
        <div style="font-size:10px;font-weight:800;opacity:0.75;text-transform:uppercase;margin-bottom:6px">🫁 Saat Terintubasi</div>
        <div style="font-size:11px;font-weight:700;color:#4db6f7;margin-bottom:2px">Domain 3:</div>
        <div style="font-size:11px;color:#e0e8f0;line-height:1.5">Kepatuhan terhadap ventilator<br><span style="opacity:0.7">Toleransi / batuk / fighting vent</span></div>
      </div>
      <div style="background:#1a3a28;border-radius:10px;padding:10px;color:#fff">
        <div style="font-size:10px;font-weight:800;opacity:0.75;text-transform:uppercase;margin-bottom:6px">😮 Saat Tidak Terintubasi</div>
        <div style="font-size:11px;font-weight:700;color:#4ddb97;margin-bottom:2px">Domain 3:</div>
        <div style="font-size:11px;color:#e0f0e8;line-height:1.5">Vokalisasi<br><span style="opacity:0.7">Tidak menangis / erangan / tangis</span></div>
      </div>
    </div>
    <p style="font-size:11px;color:var(--muted);margin-top:8px;line-height:1.5">Domain 1, 2, 4, 5 (Ekspresi Wajah, Gerakan Tubuh, Tegangan Otot, Konsolabilitas) — <b>sama untuk keduanya.</b></p>
  </div>

  <div class="info-card" style="background:#e8f5e9;border-left:4px solid var(--green);margin-top:10px">
    <h3>💡 Tips Klinis — 3 Waktu Pengkajian</h3>
    <p style="font-size:12px;line-height:1.7">
      Lakukan pengkajian P-CPOT pada <b>3 waktu</b>: saat istirahat <b>(T1)</b>, selama prosedur <b>(T2)</b>, dan 15 menit setelah prosedur <b>(T3)</b>. Catat ketiga nilai dalam dokumentasi.
    </p>
  </div>

  <!-- ASESMEN ULANG NYERI -->
  <div class="info-card" style="background:#fff;padding:0;overflow:hidden">
    <div style="background:linear-gradient(135deg,#1a2a3a,#1e6fa8);padding:12px 16px;color:#fff">
      <div style="font-size:11px;font-weight:800;opacity:0.75;letter-spacing:0.5px;text-transform:uppercase;margin-bottom:3px">SOP RSHS — Panduan Manajemen Nyeri 2022</div>
      <div style="font-size:16px;font-weight:900">🔄 Kapan Asesmen Ulang Dilakukan?</div>
    </div>
    <div style="padding:14px 16px">

      <!-- Trigger 1: Rutin -->
      <div style="margin-bottom:10px">
        <div style="font-size:10px;font-weight:900;text-transform:uppercase;letter-spacing:0.5px;color:var(--muted);margin-bottom:6px">⏱ Rutin Berdasarkan Skor</div>
        <div style="display:flex;flex-direction:column;gap:6px">
          <div style="display:flex;align-items:center;gap:10px;background:linear-gradient(90deg,#e8f5e9,#f0faf4);border-radius:10px;padding:9px 12px;border-left:3px solid #27ae60">
            <div style="background:#27ae60;border-radius:7px;padding:4px 8px;color:#fff;font-size:14px;font-weight:900;min-width:36px;text-align:center">0–3</div>
            <div>
              <div style="font-size:12px;font-weight:800;color:#1a2a3a">Tidak Nyeri / Nyeri Ringan</div>
              <div style="font-size:11px;color:#27ae60;font-weight:700">→ Asesmen ulang setiap <b>8 jam</b></div>
            </div>
          </div>
          <div style="display:flex;align-items:center;gap:10px;background:linear-gradient(90deg,#fff8e1,#fffdf0);border-radius:10px;padding:9px 12px;border-left:3px solid #f39c12">
            <div style="background:#f39c12;border-radius:7px;padding:4px 8px;color:#fff;font-size:14px;font-weight:900;min-width:36px;text-align:center">4–6</div>
            <div>
              <div style="font-size:12px;font-weight:800;color:#1a2a3a">Nyeri Sedang</div>
              <div style="font-size:11px;color:#e07b00;font-weight:700">→ Asesmen ulang setiap <b>2 jam</b></div>
            </div>
          </div>
          <div style="display:flex;align-items:center;gap:10px;background:linear-gradient(90deg,#fdecea,#fff5f5);border-radius:10px;padding:9px 12px;border-left:3px solid #e74c3c">
            <div style="background:#e74c3c;border-radius:7px;padding:4px 8px;color:#fff;font-size:14px;font-weight:900;min-width:36px;text-align:center">7–10</div>
            <div>
              <div style="font-size:12px;font-weight:800;color:#1a2a3a">Nyeri Berat</div>
              <div style="font-size:11px;color:#c0392b;font-weight:700">→ Asesmen ulang setiap <b>1 jam</b></div>
            </div>
          </div>
        </div>
      </div>

      <div style="height:1px;background:#eef0f3;margin:10px 0"></div>

      <!-- Trigger 2: Kondisi Klinis -->
      <div style="margin-bottom:10px">
        <div style="font-size:10px;font-weight:900;text-transform:uppercase;letter-spacing:0.5px;color:var(--muted);margin-bottom:6px">🚨 Asesmen Segera — Bila Ada Kondisi Berikut</div>
        <div style="display:flex;flex-direction:column;gap:5px">
          <div style="display:flex;align-items:flex-start;gap:8px;padding:8px 10px;background:#fff8e1;border-radius:8px;border-left:3px solid #f39c12">
            <span style="font-size:14px;flex-shrink:0">🔍</span>
            <div style="font-size:12px;font-weight:700;color:#1a2a3a;line-height:1.4">Setiap kali melakukan <b>pemeriksaan fisik</b> pada pasien</div>
          </div>
          <div style="display:flex;align-items:flex-start;gap:8px;padding:8px 10px;background:#fdecea;border-radius:8px;border-left:3px solid #e74c3c">
            <span style="font-size:14px;flex-shrink:0">⚠️</span>
            <div style="font-size:12px;font-weight:700;color:#1a2a3a;line-height:1.4"><b>Ada perubahan kondisi klinis</b> pasien</div>
          </div>
          <div style="display:flex;align-items:flex-start;gap:8px;padding:8px 10px;background:#fdecea;border-radius:8px;border-left:3px solid #e74c3c">
            <span style="font-size:14px;flex-shrink:0">😣</span>
            <div style="font-size:12px;font-weight:700;color:#1a2a3a;line-height:1.4">Pasien <b>mengeluh nyeri</b> (verbal/non-verbal)</div>
          </div>
        </div>
      </div>

      <div style="height:1px;background:#eef0f3;margin:10px 0"></div>

      <!-- Trigger 3: Setelah Obat -->
      <div>
        <div style="font-size:10px;font-weight:900;text-transform:uppercase;letter-spacing:0.5px;color:var(--muted);margin-bottom:6px">💊 Setelah Pemberian Obat Nyeri</div>
        <div style="display:flex;align-items:center;gap:10px;background:linear-gradient(90deg,#f3e5f5,#fdf0ff);border-radius:10px;padding:9px 12px;border-left:3px solid #7b1fa2">
          <div style="background:#7b1fa2;border-radius:7px;padding:4px 8px;color:#fff;font-size:11px;font-weight:900;min-width:36px;text-align:center">Bolus</div>
          <div>
            <div style="font-size:12px;font-weight:800;color:#1a2a3a">Obat nyeri baru atau dosis bolus diberikan</div>
            <div style="font-size:11px;color:#7b1fa2;font-weight:700">→ Asesmen ulang <b>30 menit</b> setelah pemberian</div>
          </div>
        </div>
        <div style="margin-top:6px;font-size:10px;color:var(--muted);font-weight:700;line-height:1.5;padding:0 2px">
          Nyeri sedang &amp; berat: asesmen ulang dilanjutkan sampai nyeri masuk kategori ringan (0–3), selanjutnya monitoring sesuai jadwal rutin.
        </div>
      </div>

    </div>
  </div>
</div>

<!-- =================== HALAMAN 2: P-CPOT (FOKUS UTAMA) =================== -->
<div class="page" id="page2">
  <div class="page-title">P-CPOT — Instrumen Utama</div>
  <div class="page-desc">Berlaku untuk pasien terintubasi &amp; tidak terintubasi</div>

  <div class="instrument-card">
    <div class="inst-header" style="background:linear-gradient(135deg,#1a2a3a,#1e6fa8)">
      <div style="display:flex;justify-content:space-between;align-items:flex-start">
        <div>
          <div class="inst-name">P-CPOT</div>
          <div class="inst-full">Pediatric Critical-Care Pain Observation Tool</div>
        </div>
        <div style="background:rgba(255,255,255,0.15);border-radius:8px;padding:4px 10px;font-size:10px;font-weight:800;text-align:center">
          ⭐ UTAMA<br>RSHS
        </div>
      </div>
      <div class="inst-meta">
        <div class="inst-meta-item"><span>0–10</span>Skor</div>
        <div class="inst-meta-item"><span>≥ 4</span>Nyeri</div>
        <div class="inst-meta-item"><span>5</span>Domain</div>
        <div class="inst-meta-item"><span>r=0.996</span>Reliabilitas</div>
      </div>
    </div>

    <!-- TABLE -->
    <table class="domain-table">
      <thead>
        <tr>
          <th style="width:30%">Domain</th>
          <th style="width:23%">Skor 0</th>
          <th style="width:23%">Skor 1</th>
          <th style="width:24%">Skor 2</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td><div class="domain-name">😐 Ekspresi Wajah</div></td>
          <td>Rileks, netral</td>
          <td>Tegang / cemberut</td>
          <td>Meringis, mengerutkan dahi</td>
        </tr>
        <tr>
          <td><div class="domain-name">🤸 Gerakan Tubuh</div></td>
          <td>Tidak ada gerakan abnormal</td>
          <td>Melindungi area nyeri</td>
          <td>Gelisah / menarik selang</td>
        </tr>
        <tr style="background:#eaf3fb">
          <td>
            <div class="domain-name">🫁 Ventilator</div>
            <small style="color:#1e6fa8;font-weight:700">Saat TERINTUBASI ↓</small>
          </td>
          <td>Toleransi ventilator / tidak batuk</td>
          <td>Batuk tapi dapat toleransi</td>
          <td>Fighting ventilator / melawan</td>
        </tr>
        <tr style="background:#e6f7ef">
          <td>
            <div class="domain-name">😮 Vokalisasi</div>
            <small style="color:#2e9e6b;font-weight:700">Saat TIDAK INTUBASI ↓</small>
          </td>
          <td>Tidak menangis / tenang</td>
          <td>Erangan / rengekan</td>
          <td>Menangis / menjerit keras</td>
        </tr>
        <tr>
          <td><div class="domain-name">💪 Tegangan Otot</div></td>
          <td>Relaks, tidak tahanan</td>
          <td>Sedikit kaku</td>
          <td>Sangat kaku / fleksi</td>
        </tr>
        <tr>
          <td>
            <div class="domain-name">🤗 Konsolabilitas</div>
            <small style="color:var(--muted)">(+ vs CPOT dewasa)</small>
          </td>
          <td>Tenang / dapat ditenangkan</td>
          <td>Tenang dengan sentuhan</td>
          <td>Tidak dapat ditenangkan</td>
        </tr>
      </tbody>
    </table>
    <div style="padding:10px 14px;background:#eaf3fb;font-size:11px;color:var(--pcpot)">
      <b>Cara Skoring:</b> Jumlah skor domain 1 + 2 + 3<em>(atau 4)</em> + 5 + 6 = <b>Total 0–10</b><br>
      Gunakan domain <b>Ventilator</b> jika terintubasi, domain <b>Vokalisasi</b> jika tidak terintubasi.<br>
      <b>Sumber:</b> Tao &amp; Galagarza, <em>Pain Management Nursing</em>, 2020 | Sensitivitas 98.6%
    </div>
  </div>

  <!-- INTERPRETASI CEPAT -->
  <div class="info-card">
    <h3>🎯 Interpretasi Skor P-CPOT</h3>
    <div style="display:flex;flex-direction:column;gap:6px">
      <div style="display:flex;align-items:center;gap:10px;background:linear-gradient(90deg,#27ae60,#1e8449);border-radius:10px;padding:10px 14px;color:#fff">
        <div style="font-size:22px;font-weight:900;min-width:48px">0–3</div>
        <div>
          <div style="font-weight:800;font-size:13px">🟢 Tidak Ada / Nyeri Ringan</div>
          <div style="font-size:11px;opacity:0.9">Monitoring rutin — <b>setiap 8 jam (SOP RSHS)</b></div>
        </div>
      </div>
      <div style="display:flex;align-items:center;gap:10px;background:linear-gradient(90deg,#f39c12,#d68910);border-radius:10px;padding:10px 14px;color:#fff">
        <div style="font-size:22px;font-weight:900;min-width:48px">4–6</div>
        <div>
          <div style="font-weight:800;font-size:13px">🟡 Nyeri Sedang</div>
          <div style="font-size:11px;opacity:0.9">Intervensi + evaluasi ulang — <b>setiap 2 jam (SOP RSHS)</b></div>
        </div>
      </div>
      <div style="display:flex;align-items:center;gap:10px;background:linear-gradient(90deg,#e74c3c,#c0392b);border-radius:10px;padding:10px 14px;color:#fff">
        <div style="font-size:22px;font-weight:900;min-width:48px">7–10</div>
        <div>
          <div style="font-weight:800;font-size:13px">🔴 Nyeri Berat</div>
          <div style="font-size:11px;opacity:0.9">Intervensi segera + evaluasi ketat — <b>setiap 1 jam (SOP RSHS)</b></div>
        </div>
      </div>
      <div style="display:flex;align-items:center;gap:10px;background:linear-gradient(90deg,#6a1b9a,#4a148c);border-radius:10px;padding:10px 14px;color:#fff">
        <div style="font-size:13px;font-weight:900;min-width:48px;text-align:center">💊<br>Bolus</div>
        <div>
          <div style="font-weight:800;font-size:13px">🟣 Setelah Obat Baru / Bolus</div>
          <div style="font-size:11px;opacity:0.9">Asesmen ulang — <b>30 menit setelah pemberian (SOP RSHS)</b></div>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- =================== HALAMAN 3: TINDAK LANJUT =================== -->
<div class="page" id="page3">
  <div class="page-title">Panduan Tindak Lanjut Skor</div>
  <div class="page-desc">SOP RSHS + SCCM PANDEM Guidelines 2022</div>

  <!-- SKOR 0-3 -->
  <div class="score-band" style="background:linear-gradient(135deg,#27ae60,#1e8449)">
    <div class="sb-top">
      <div class="sb-score">0–3</div>
      <div class="sb-right">
        <div class="sb-label">🟢 Tidak Ada / Nyeri Ringan</div>
        <span class="sb-freq">⏱ Monitoring: <b>Setiap 8 jam</b></span>
      </div>
    </div>
    <ul>
      <li>Lanjutkan monitoring rutin setiap <b>8 jam</b> (SOP RSHS)</li>
      <li>Pertahankan posisi nyaman, jaga lingkungan tenang</li>
      <li>Intervensi non-farmakologis: sentuhan lembut, musik, swaddling</li>
      <li>Dokumentasikan skor dalam rekam medis / flowchart</li>
      <li>Tidak diperlukan intervensi farmakologis segera</li>
    </ul>
  </div>

  <!-- SKOR 4-6 -->
  <div class="score-band" style="background:linear-gradient(135deg,#f39c12,#d68910)">
    <div class="sb-top">
      <div class="sb-score">4–6</div>
      <div class="sb-right">
        <div class="sb-label">🟡 Nyeri Sedang — Intervensi</div>
        <span class="sb-freq">⏱ Monitoring: <b>Setiap 2 jam</b></span>
      </div>
    </div>
    <ul>
      <li>Laporkan ke dokter / DPJP segera</li>
      <li>Berikan analgesik sesuai advis (non-opioid lini pertama)</li>
      <li>Intervensi non-farmakologis: reposisi, distraksi, sentuhan, swaddling</li>
      <li>Evaluasi ulang skor P-CPOT setelah 30 menit intervensi</li>
      <li>Jika skor tetap ≥ 4 setelah 1 jam → eskalasi ke tatalaksana nyeri berat</li>
      <li>Dokumentasikan intervensi, waktu, dan respons pasien</li>
    </ul>
  </div>

  <!-- SKOR 7-10 -->
  <div class="score-band" style="background:linear-gradient(135deg,#e74c3c,#c0392b)">
    <div class="sb-top">
      <div class="sb-score">7–10</div>
      <div class="sb-right">
        <div class="sb-label">🔴 Nyeri Berat — SEGERA</div>
        <span class="sb-freq">⏱ Monitoring: <b>Setiap 1 jam</b></span>
      </div>
    </div>
    <ul>
      <li><b>Aktifkan protokol nyeri berat PICU — jangan tunda!</b></li>
      <li>Hubungi dokter / DPJP <b>SEGERA</b></li>
      <li>Opioid IV dipertimbangkan sebagai lini pertama (SCCM 2022)</li>
      <li>Monitor ketat tanda vital, saturasi, dan efek samping</li>
      <li>Evaluasi skor P-CPOT setiap 1 jam hingga skor &lt; 4</li>
      <li>Jika skor &lt; 4 tercapai → turunkan frekuensi ke setiap 2 jam</li>
      <li>Dokumentasikan waktu intervensi, dosis, dan respons</li>
    </ul>
  </div>

  <!-- BOLUS -->
  <div class="score-band" style="background:linear-gradient(135deg,#6a1b9a,#4a148c)">
    <div class="sb-top">
      <div class="sb-score" style="font-size:20px">💊 Bolus</div>
      <div class="sb-right">
        <div class="sb-label">🟣 Setelah Obat Nyeri Baru / Bolus</div>
        <span class="sb-freq">⏱ Asesmen ulang: <b>30 menit setelah pemberian</b></span>
      </div>
    </div>
    <ul>
      <li>Nilai ulang skor P-CPOT <b>30 menit</b> setelah pemberian analgesik baru atau bolus</li>
      <li>Dokumentasikan: nama obat, dosis, waktu pemberian, skor sebelum dan sesudah</li>
      <li>Jika skor tidak turun setelah 30 menit → laporkan DPJP untuk eskalasi</li>
      <li>Berlaku untuk semua kategori nyeri yang mendapat tambahan obat baru</li>
      <li><b>Sumber: Panduan Manajemen Nyeri RSHS 2022</b></li>
    </ul>
  </div>

  <!-- RINGKASAN SOP -->
  <div class="info-card" style="background:#fff;border:2px solid var(--pcpot)">
    <h3>📋 Ringkasan Frekuensi Monitoring — SOP RSHS</h3>
    <table class="domain-table">
      <thead>
        <tr>
          <th>Skor P-CPOT</th>
          <th>Kategori</th>
          <th>Frekuensi</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td><b style="color:#27ae60">0 – 3</b></td>
          <td>Tidak ada / Ringan</td>
          <td><b>Tiap 8 jam</b></td>
        </tr>
        <tr>
          <td><b style="color:#e07b00">4 – 6</b></td>
          <td>Sedang</td>
          <td><b>Tiap 2 jam</b></td>
        </tr>
        <tr>
          <td><b style="color:#c0392b">7 – 10</b></td>
          <td>Berat</td>
          <td><b>Tiap 1 jam</b></td>
        </tr>
        <tr>
          <td><b style="color:#7b1fa2">Obat Baru / Bolus</b></td>
          <td>Setelah pemberian</td>
          <td><b>30 menit</b></td>
        </tr>
      </tbody>
    </table>
  </div>

  <div class="info-card" style="background:#e8f4fd;border-left:4px solid var(--pcpot)">
    <h3>📌 Prinsip PANDEM SCCM 2022</h3>
    <p style="font-size:12px;line-height:1.7">
      <b>"Treat pain first"</b> — Analgesik diberikan sebelum sedatif. Utamakan opioid IV untuk nyeri non-neuropatik. Minimalisasi benzodiazepin untuk mencegah delirium. Gunakan instrumen tervalidasi secara rutin sesuai jadwal SOP RSHS: <b>0–3 → tiap 8 jam</b>, <b>4–6 → tiap 2 jam</b>, <b>7–10 → tiap 1 jam</b>. Bila diberikan obat nyeri baru atau bolus: <b>asesmen ulang 30 menit setelah pemberian</b>.
    </p>
  </div>
</div>

<!-- =================== HALAMAN 4: REFERENSI =================== -->
<div class="page" id="page4">
  <div class="page-title">Daftar Referensi</div>
  <div class="page-desc">Sumber tervalidasi — jurnal terindeks internasional</div>

  <div class="section-divider">Instrumen Utama</div>

  <div class="ref-item">
    <div class="ref-num">Ref 1 — P-CPOT (Validasi Utama)</div>
    <div class="ref-citation">
      Tao, H., &amp; Galagarza, S. R. (2020). P-CPOT: An adaptation of the Critical-Care Pain Observation Tool for pediatric intensive care unit patients. <i>Pain Management Nursing, 21</i>(2), 172–178.
    </div>
    <div class="ref-doi">DOI: 10.1016/j.pmn.2019.07.012 | PMID: 31506237</div>
  </div>

  <div class="ref-item" style="border-left-color:var(--green)">
    <div class="ref-num" style="color:var(--green)">Ref 2 — SCCM PANDEM Guidelines 2022</div>
    <div class="ref-citation">
      Smith, H. A. B., et al. (2022). 2022 SCCM clinical practice guidelines on prevention and management of pain, agitation, neuromuscular blockade, and delirium in critically ill pediatric patients. <i>Pediatric Critical Care Medicine, 23</i>(2), e74–e110.
    </div>
    <div class="ref-doi">DOI: 10.1097/PCC.0000000000002873 | PMID: 35119438</div>
  </div>

  <div class="section-divider">Studi Pendukung</div>

  <div class="ref-item" style="border-left-color:var(--orange)">
    <div class="ref-num" style="color:var(--orange)">Ref 3 — Studi Diagnostik P-CPOT di PICU (2025)</div>
    <div class="ref-citation">
      BMC Pediatrics. (2025). Investigating the diagnostic value of the pediatric critical care observation tool (P-CPOT) among children hospitalized in the PICU in 2021 — a comparative study. <i>BMC Pediatrics</i>.
    </div>
    <div class="ref-doi">DOI: 10.1186/s12887-025-06231-1</div>
  </div>

  <div class="ref-item" style="border-left-color:var(--red)">
    <div class="ref-num" style="color:var(--red)">Ref 4 — Systematic Review Skala Nyeri Pediatrik</div>
    <div class="ref-citation">
      Giordano, V., et al. (2019). Pain and sedation scales for neonatal and pediatric patients in a preverbal stage of development: a systematic review. <i>JAMA Pediatrics, 173</i>(12), 1186–1197.
    </div>
    <div class="ref-doi">DOI: 10.1001/jamapediatrics.2019.3351</div>
  </div>

  <div class="ref-item" style="border-left-color:#888">
    <div class="ref-num" style="color:#888">Ref 5 — Validasi CPOT Anak Ortopedi (2023)</div>
    <div class="ref-citation">
      Validation of the Critical-Care Pain Observation Tool (CPOT) in pediatric patients undergoing orthopedic surgery. (2023). <i>Canadian Journal of Pain</i>.
    </div>
    <div class="ref-doi">DOI: 10.1080/24740527.2022.2156332 | PMID: 36874228</div>
  </div>

  <div class="info-card" style="background:#fffde7;border-left:4px solid #f9a825;margin-top:14px">
    <h3>📌 Catatan Habituasi</h3>
    <p style="font-size:12px;line-height:1.7">
      QRG Digital v3.0 ini telah disesuaikan dengan SOP RSHS — fokus instrumen P-CPOT untuk seluruh pasien PICU (terintubasi &amp; tidak terintubasi), dengan frekuensi monitoring: 0–3 (8 jam), 4–6 (2 jam), 7–10 (1 jam). Bila obat baru/bolus diberikan → asesmen ulang 30 menit..
    </p>
  </div>
</div>

<!-- =================== HALAMAN 5: LEMBAR PENGISIAN =================== -->
<div class="page" id="page5">
  <div class="page-title">Lembar Pengkajian P-CPOT</div>
  <div class="page-desc">Isi dan centang sesuai kondisi pasien saat ini</div>

  <style>
    /* ===== FORM STYLES ===== */
    .form-section { background:#fff; border-radius:var(--radius); padding:14px 16px; margin-bottom:12px; box-shadow:var(--shadow); }
    .form-section h3 { font-size:11px; font-weight:800; text-transform:uppercase; letter-spacing:0.5px; color:var(--muted); margin-bottom:10px; }

    .field-row { display:flex; flex-direction:column; margin-bottom:10px; }
    .field-label { font-size:11px; font-weight:800; color:var(--text); margin-bottom:4px; }
    .field-input {
      border:1.5px solid #dde3ea; border-radius:10px;
      padding:10px 12px; font-size:13px; font-family:inherit;
      color:var(--text); background:#f8fafc;
      outline:none; transition:border-color 0.2s, box-shadow 0.2s;
      width: 100%;
    }
    .field-input:focus { border-color:var(--pcpot); background:#fff; box-shadow: 0 0 0 3px rgba(30,111,168,0.12); }

    .field-row-2 { display:grid; grid-template-columns:1fr 1fr; gap:10px; margin-bottom:10px; }

    /* Domain scoring */
    .domain-score-card {
      border:1.5px solid #eef0f3; border-radius:12px;
      overflow:hidden; margin-bottom:10px;
    }
    .domain-score-header {
      padding:9px 14px; font-size:12px; font-weight:800;
      color:#fff; display:flex; align-items:center; gap:8px;
    }
    .domain-options { padding:8px 10px; display:flex; flex-direction:column; gap:6px; }

    .radio-option {
      display:flex; align-items:flex-start; gap:10px;
      padding:10px 12px; border-radius:10px; cursor:pointer;
      border:1.5px solid transparent; transition:all 0.15s;
      background:#f8fafc;
      min-height: 46px;
    }
    .radio-option:hover { background:#eaf3fb; border-color:#c5dff0; }
    .radio-option input[type=radio] { display:none; }
    .radio-option.selected { border-color:var(--pcpot); background:#eaf3fb; }
    .radio-option.selected-1 { border-color:#f39c12; background:#fff8e1; }
    .radio-option.selected-2 { border-color:#c0392b; background:#fdecea; }

    .radio-dot {
      width:18px; height:18px; border-radius:50%;
      border:2px solid #c5d0db; flex-shrink:0; margin-top:1px;
      display:flex; align-items:center; justify-content:center;
      transition:all 0.15s;
    }
    .radio-option.selected .radio-dot,
    .radio-option.selected-1 .radio-dot,
    .radio-option.selected-2 .radio-dot {
      border-color:var(--pcpot);
    }
    .radio-option.selected-1 .radio-dot { border-color:#f39c12; }
    .radio-option.selected-2 .radio-dot { border-color:#c0392b; }
    .radio-inner { width:9px; height:9px; border-radius:50%; display:none; }
    .radio-option.selected .radio-inner { display:block; background:var(--pcpot); }
    .radio-option.selected-1 .radio-inner { display:block; background:#f39c12; }
    .radio-option.selected-2 .radio-inner { display:block; background:#c0392b; }

    .radio-content { flex:1; }
    .radio-score { font-size:10px; font-weight:900; margin-bottom:1px; }
    .radio-desc { font-size:11px; color:var(--muted); line-height:1.4; font-weight:600; }

    /* Score display */
    .score-display {
      background:linear-gradient(135deg,#1a2a3a,#1e6fa8);
      border-radius:14px; padding:16px 18px; color:#fff;
      text-align:center; margin-bottom:12px;
    }
    .score-display .sd-label { font-size:11px; font-weight:700; opacity:0.75; margin-bottom:4px; }
    .score-display .sd-num { font-size:48px; font-weight:900; line-height:1; }
    .score-display .sd-max { font-size:14px; opacity:0.6; }
    .score-display .sd-interp { font-size:13px; font-weight:800; margin-top:6px; padding:4px 16px; border-radius:50px; display:inline-block; }

    /* Checklist tindak lanjut */
    .check-item {
      display:flex; align-items:flex-start; gap:10px;
      padding:9px 10px; border-radius:10px; cursor:pointer;
      border:1.5px solid #eef0f3; background:#f8fafc;
      margin-bottom:7px; transition:all 0.15s;
    }
    .check-item:hover { background:#eaf3fb; border-color:#c5dff0; }
    .check-item input[type=checkbox] { display:none; }
    .check-box {
      width:20px; height:20px; border-radius:5px;
      border:2px solid #c5d0db; flex-shrink:0;
      display:flex; align-items:center; justify-content:center;
      transition:all 0.15s; margin-top:1px;
    }
    .check-item.checked { background:#e8f5e9; border-color:#2e9e6b; }
    .check-item.checked .check-box { background:#2e9e6b; border-color:#2e9e6b; color:#fff; font-size:12px; }
    .check-text { font-size:12px; font-weight:700; color:var(--text); line-height:1.4; }
    .check-item.checked .check-text { color:#1a6640; text-decoration:line-through; opacity:0.75; }

    /* Reset button */
    .btn-reset {
      width:100%; padding:13px; border-radius:12px;
      background:#fdecea; color:#c0392b;
      border:1.5px solid #c0392b; font-size:13px;
      font-weight:800; font-family:inherit; cursor:pointer;
      transition:all 0.15s;
      letter-spacing: 0.2px;
    }
    .btn-reset:hover { background:#c0392b; color:#fff; }
    .btn-reset:active { transform: scale(0.98); }

    .btn-save {
      width:100%; padding:14px; border-radius:12px;
      background:linear-gradient(135deg,#1a2a3a,#1e6fa8);
      color:#fff; border:none; font-size:13px;
      font-weight:800; font-family:inherit; cursor:pointer;
      margin-bottom:8px; transition:opacity 0.15s, transform 0.15s;
      box-shadow: 0 4px 16px rgba(30,111,168,0.35);
      letter-spacing: 0.2px;
    }
    .btn-save:hover { opacity:0.9; box-shadow: 0 6px 20px rgba(30,111,168,0.45); }
    .btn-save:active { transform: scale(0.98); }

    .ventilator-toggle {
      display:flex; gap:0; border-radius:10px; overflow:hidden;
      border:1.5px solid var(--pcpot); margin-bottom:10px;
    }
    .vent-btn {
      flex:1; padding:11px 6px; font-size:12px; font-weight:800;
      font-family:inherit; border:none; cursor:pointer;
      background:#f0f4f8; color:var(--muted); transition:all 0.15s;
    }
    .vent-btn.active { background:var(--pcpot); color:#fff; }
    .vent-btn:active { opacity: 0.85; }

    .vent-note { font-size:10px; color:var(--muted); font-weight:700; margin-bottom:8px; text-align:center; }

    .timestamp { font-size:10px; color:var(--muted); font-weight:700; text-align:center; margin-top:6px; }
  </style>

  <!-- IDENTITAS PASIEN -->
  <div class="form-section">
    <h3>👤 Identitas Pasien</h3>
    <div class="field-row">
      <label class="field-label">Nama Pasien</label>
      <input class="field-input" type="text" id="f-nama" placeholder="Nama lengkap pasien">
    </div>
    <div class="field-row-2">
      <div class="field-row" style="margin-bottom:0">
        <label class="field-label">No. RM</label>
        <input class="field-input" type="text" id="f-rm" placeholder="No. Rekam Medis">
      </div>
      <div class="field-row" style="margin-bottom:0">
        <label class="field-label">Usia</label>
        <input class="field-input" type="text" id="f-usia" placeholder="Contoh: 3 thn 2 bln">
      </div>
    </div>
    <div class="field-row" style="margin-bottom:0">
      <label class="field-label">Tanggal &amp; Jam Pengkajian</label>
      <input class="field-input" type="datetime-local" id="f-waktu">
    </div>
  </div>

  <!-- STATUS VENTILASI -->
  <div class="form-section">
    <h3>🫁 Status Ventilasi</h3>
    <div class="ventilator-toggle">
      <button class="vent-btn active" id="vent-ya" onclick="setVent('terintubasi')">🫁 Terintubasi / ETT</button>
      <button class="vent-btn" id="vent-tidak" onclick="setVent('tidak')">😮 Tidak Terintubasi</button>
    </div>
    <div class="vent-note" id="vent-note">Domain 3 aktif: Kepatuhan Ventilator</div>
  </div>

  <!-- SCORING P-CPOT -->
  <div class="form-section">
    <h3>🩺 Penilaian 5 Domain P-CPOT</h3>

    <!-- Domain 1: Ekspresi Wajah -->
    <div class="domain-score-card">
      <div class="domain-score-header" style="background:linear-gradient(135deg,#1a2a3a,#1e6fa8)">
        😐 Domain 1 — Ekspresi Wajah
      </div>
      <div class="domain-options" id="d1">
        <label class="radio-option" onclick="selectOption('d1',0,this)">
          <input type="radio" name="d1"><div class="radio-dot"><div class="radio-inner"></div></div>
          <div class="radio-content"><div class="radio-score" style="color:#27ae60">Skor 0</div><div class="radio-desc">Rileks, netral, tidak ada ketegangan</div></div>
        </label>
        <label class="radio-option" onclick="selectOption('d1',1,this)">
          <input type="radio" name="d1"><div class="radio-dot"><div class="radio-inner"></div></div>
          <div class="radio-content"><div class="radio-score" style="color:#f39c12">Skor 1</div><div class="radio-desc">Tegang, cemberut, mengerutkan dahi</div></div>
        </label>
        <label class="radio-option" onclick="selectOption('d1',2,this)">
          <input type="radio" name="d1"><div class="radio-dot"><div class="radio-inner"></div></div>
          <div class="radio-content"><div class="radio-score" style="color:#c0392b">Skor 2</div><div class="radio-desc">Meringis, menangis keras, wajah sangat terdistorsi</div></div>
        </label>
      </div>
    </div>

    <!-- Domain 2: Gerakan Tubuh -->
    <div class="domain-score-card">
      <div class="domain-score-header" style="background:linear-gradient(135deg,#1a2a3a,#1e6fa8)">
        🤸 Domain 2 — Gerakan Tubuh
      </div>
      <div class="domain-options" id="d2">
        <label class="radio-option" onclick="selectOption('d2',0,this)">
          <input type="radio" name="d2"><div class="radio-dot"><div class="radio-inner"></div></div>
          <div class="radio-content"><div class="radio-score" style="color:#27ae60">Skor 0</div><div class="radio-desc">Tidak ada gerakan abnormal, posisi normal</div></div>
        </label>
        <label class="radio-option" onclick="selectOption('d2',1,this)">
          <input type="radio" name="d2"><div class="radio-dot"><div class="radio-inner"></div></div>
          <div class="radio-content"><div class="radio-score" style="color:#f39c12">Skor 1</div><div class="radio-desc">Melindungi area nyeri, gerakan lambat/berhati-hati</div></div>
        </label>
        <label class="radio-option" onclick="selectOption('d2',2,this)">
          <input type="radio" name="d2"><div class="radio-dot"><div class="radio-inner"></div></div>
          <div class="radio-content"><div class="radio-score" style="color:#c0392b">Skor 2</div><div class="radio-desc">Gelisah, menarik selang, mencoba duduk, memukul</div></div>
        </label>
      </div>
    </div>

    <!-- Domain 3: Ventilator / Vokalisasi (dinamis) -->
    <div class="domain-score-card">
      <div class="domain-score-header" id="d3-header" style="background:linear-gradient(135deg,#1a2a3a,#1e6fa8)">
        🫁 Domain 3 — Kepatuhan Ventilator
      </div>
      <div class="domain-options" id="d3">
        <label class="radio-option" onclick="selectOption('d3',0,this)">
          <input type="radio" name="d3"><div class="radio-dot"><div class="radio-inner"></div></div>
          <div class="radio-content"><div class="radio-score" style="color:#27ae60">Skor 0</div><div class="radio-desc" id="d3-0">Toleran terhadap ventilator, tidak batuk</div></div>
        </label>
        <label class="radio-option" onclick="selectOption('d3',1,this)">
          <input type="radio" name="d3"><div class="radio-dot"><div class="radio-inner"></div></div>
          <div class="radio-content"><div class="radio-score" style="color:#f39c12">Skor 1</div><div class="radio-desc" id="d3-1">Batuk tapi masih dapat toleransi</div></div>
        </label>
        <label class="radio-option" onclick="selectOption('d3',2,this)">
          <input type="radio" name="d3"><div class="radio-dot"><div class="radio-inner"></div></div>
          <div class="radio-content"><div class="radio-score" style="color:#c0392b">Skor 2</div><div class="radio-desc" id="d3-2">Fighting ventilator, melawan / asinkroni</div></div>
        </label>
      </div>
    </div>

    <!-- Domain 4: Tegangan Otot -->
    <div class="domain-score-card">
      <div class="domain-score-header" style="background:linear-gradient(135deg,#1a2a3a,#1e6fa8)">
        💪 Domain 4 — Tegangan Otot
      </div>
      <div class="domain-options" id="d4">
        <label class="radio-option" onclick="selectOption('d4',0,this)">
          <input type="radio" name="d4"><div class="radio-dot"><div class="radio-inner"></div></div>
          <div class="radio-content"><div class="radio-score" style="color:#27ae60">Skor 0</div><div class="radio-desc">Relaks, tidak ada tahanan pada gerakan pasif</div></div>
        </label>
        <label class="radio-option" onclick="selectOption('d4',1,this)">
          <input type="radio" name="d4"><div class="radio-dot"><div class="radio-inner"></div></div>
          <div class="radio-content"><div class="radio-score" style="color:#f39c12">Skor 1</div><div class="radio-desc">Sedikit kaku, resistensi minimal-sedang</div></div>
        </label>
        <label class="radio-option" onclick="selectOption('d4',2,this)">
          <input type="radio" name="d4"><div class="radio-dot"><div class="radio-inner"></div></div>
          <div class="radio-content"><div class="radio-score" style="color:#c0392b">Skor 2</div><div class="radio-desc">Sangat kaku / fleksi, gerakan tidak dapat diselesaikan</div></div>
        </label>
      </div>
    </div>

    <!-- Domain 5: Konsolabilitas -->
    <div class="domain-score-card">
      <div class="domain-score-header" style="background:linear-gradient(135deg,#1a2a3a,#1e6fa8)">
        🤗 Domain 5 — Konsolabilitas
      </div>
      <div class="domain-options" id="d5">
        <label class="radio-option" onclick="selectOption('d5',0,this)">
          <input type="radio" name="d5"><div class="radio-dot"><div class="radio-inner"></div></div>
          <div class="radio-content"><div class="radio-score" style="color:#27ae60">Skor 0</div><div class="radio-desc">Tenang, dapat ditenangkan dengan mudah</div></div>
        </label>
        <label class="radio-option" onclick="selectOption('d5',1,this)">
          <input type="radio" name="d5"><div class="radio-dot"><div class="radio-inner"></div></div>
          <div class="radio-content"><div class="radio-score" style="color:#f39c12">Skor 1</div><div class="radio-desc">Tenang dengan sentuhan / diajak bicara</div></div>
        </label>
        <label class="radio-option" onclick="selectOption('d5',2,this)">
          <input type="radio" name="d5"><div class="radio-dot"><div class="radio-inner"></div></div>
          <div class="radio-content"><div class="radio-score" style="color:#c0392b">Skor 2</div><div class="radio-desc">Sulit ditenangkan meskipun sudah diupayakan maksimal</div></div>
        </label>
      </div>
    </div>
  </div>

  <!-- TOTAL SKOR -->
  <div class="score-display" id="score-display">
    <div class="sd-label">Total Skor P-CPOT</div>
    <div><span class="sd-num" id="score-num">—</span><span class="sd-max"> / 10</span></div>
    <div id="score-interp" style="margin-top:6px;font-size:12px;opacity:0.7">Pilih semua domain untuk melihat skor</div>
  </div>

  <!-- CHECKLIST TINDAK LANJUT -->
  <div class="form-section" id="checklist-section" style="display:none">
    <h3>✅ Tindak Lanjut — Centang yang Sudah Dilakukan</h3>
    <div id="checklist-items"></div>
  </div>

  <!-- CATATAN -->
  <div class="form-section">
    <h3>📝 Catatan Klinis</h3>
    <div class="field-row" style="margin-bottom:0">
      <textarea class="field-input" id="f-catatan" rows="3" placeholder="Catatan tambahan perawat..."></textarea>
    </div>
  </div>

  <!-- PERAWAT -->
  <div class="form-section">
    <h3>👩‍⚕️ Perawat Pengkaji</h3>
    <div class="field-row" style="margin-bottom:0">
      <input class="field-input" type="text" id="f-perawat" placeholder="Nama perawat pengkaji">
    </div>
  </div>

  <!-- TOMBOL UTAMA -->
  <button class="btn-save" onclick="saveSummary()">💾 Simpan &amp; Lihat Ringkasan</button>

  <!-- TOMBOL EXPORT LEMBAR (muncul setelah simpan) -->
  <div id="export-lembar-btns" style="display:none;margin-bottom:8px">
    <div style="font-size:10px;font-weight:800;text-transform:uppercase;letter-spacing:0.5px;color:var(--muted);margin-bottom:6px;text-align:center">📤 Export Data Pengkajian Ini</div>
    <div style="display:grid;grid-template-columns:1fr 1fr;gap:8px">
      <button onclick="exportLembarCSV()" style="padding:10px 8px;border-radius:10px;background:linear-gradient(135deg,#27ae60,#1e8449);color:#fff;border:none;font-size:11px;font-weight:800;font-family:inherit;cursor:pointer">
        📊 Export CSV
      </button>
      <button onclick="printLembar()" style="padding:10px 8px;border-radius:10px;background:linear-gradient(135deg,#1a2a3a,#1e6fa8);color:#fff;border:none;font-size:11px;font-weight:800;font-family:inherit;cursor:pointer">
        🖨️ Cetak / PDF
      </button>
    </div>
    <div style="margin-top:6px">
      <button onclick="tambahKeRiwayat()" style="width:100%;padding:10px;border-radius:10px;background:linear-gradient(135deg,#e07b00,#a04000);color:#fff;border:none;font-size:11px;font-weight:800;font-family:inherit;cursor:pointer">
        📋 Simpan ke Riwayat Pasien
      </button>
    </div>
  </div>

  <button class="btn-reset" onclick="resetForm()">🔄 Reset Formulir</button>
  <div class="timestamp" id="saved-ts"></div>

  <!-- RIWAYAT SEMUA PENGKAJIAN -->
  <div id="riwayat-section" style="margin-top:14px">
    <div id="riwayat-toggle-btn" onclick="toggleRiwayat()" style="background:#f0f4f8;border-radius:12px;padding:10px 16px;cursor:pointer;display:flex;justify-content:space-between;align-items:center;margin-bottom:0">
      <span style="font-size:12px;font-weight:800;color:var(--text)">📋 Riwayat Pengkajian Tersimpan</span>
      <span id="riwayat-count-badge" style="background:var(--pcpot);color:#fff;border-radius:50px;padding:2px 9px;font-size:10px;font-weight:800">0</span>
    </div>
    <div id="riwayat-panel" style="display:none;background:#fff;border-radius:0 0 12px 12px;padding:14px 16px;box-shadow:var(--shadow)">
      <div style="display:grid;grid-template-columns:1fr 1fr;gap:8px;margin-bottom:10px">
        <button onclick="exportAllLembarCSV()" style="padding:10px 8px;border-radius:10px;background:linear-gradient(135deg,#27ae60,#1e8449);color:#fff;border:none;font-size:11px;font-weight:800;font-family:inherit;cursor:pointer">
          📊 Export Semua CSV
        </button>
        <button onclick="clearRiwayat()" style="padding:10px 8px;border-radius:10px;background:#fdecea;color:#c0392b;border:1.5px solid #c0392b;font-size:11px;font-weight:800;font-family:inherit;cursor:pointer">
          🗑️ Hapus Riwayat
        </button>
      </div>
      <div id="riwayat-list"></div>
    </div>
  </div>

  <!-- RINGKASAN TERSIMPAN -->
  <div id="summary-box" style="display:none;margin-top:14px"></div>
</div>

<!-- =================== HALAMAN 6: HUDDLE 5 MENIT =================== -->
<div class="page" id="page6">
  <div class="page-title">Huddle 5 Menit</div>
  <div class="page-desc">Validasi Nyeri Antarperawat — Setiap Operan Shift</div>

  <style>
    /* ===== HUDDLE STYLES ===== */
    .huddle-hero {
      background: linear-gradient(135deg, #1a2a3a 0%, #1e6fa8 50%, #2e9e6b 100%);
      border-radius: var(--radius); padding: 18px 18px 14px;
      color: #fff; margin-bottom: 12px; position: relative; overflow: hidden;
    }
    .huddle-hero::before {
      content: ''; position: absolute; inset: 0;
      background-image: url("data:image/svg+xml,%3Csvg width='40' height='40' viewBox='0 0 40 40' xmlns='http://www.w3.org/2000/svg'%3E%3Cg fill='%23ffffff' fill-opacity='0.04'%3E%3Ccircle cx='20' cy='20' r='3'/%3E%3C/g%3E%3C/svg%3E");
    }
    .huddle-hero .hh-badge {
      display: inline-block; background: rgba(255,255,255,0.2);
      border: 1px solid rgba(255,255,255,0.3); border-radius: 50px;
      padding: 3px 12px; font-size: 9px; font-weight: 800;
      letter-spacing: 1px; text-transform: uppercase; margin-bottom: 8px; position: relative;
    }
    .huddle-hero .hh-title { font-size: 22px; font-weight: 900; line-height: 1.2; position: relative; margin-bottom: 4px; }
    .huddle-hero .hh-sub { font-size: 11px; opacity: 0.85; position: relative; margin-bottom: 12px; }
    .huddle-hero .hh-chips { display: flex; gap: 6px; flex-wrap: wrap; position: relative; }
    .huddle-hero .hh-chip {
      background: rgba(255,255,255,0.18); border-radius: 6px;
      padding: 4px 10px; font-size: 10px; font-weight: 800;
    }

    /* Timeline steps */
    .timeline { position: relative; padding-left: 28px; }
    .timeline::before {
      content: ''; position: absolute; left: 10px; top: 6px; bottom: 6px;
      width: 2px; background: linear-gradient(to bottom, #1e6fa8, #2e9e6b);
      border-radius: 2px;
    }
    .tl-step { position: relative; margin-bottom: 12px; }
    .tl-dot {
      position: absolute; left: -22px; top: 6px;
      width: 16px; height: 16px; border-radius: 50%;
      background: var(--pcpot); border: 2px solid #fff;
      box-shadow: 0 0 0 2px var(--pcpot);
      display: flex; align-items: center; justify-content: center;
      font-size: 8px; font-weight: 900; color: #fff;
    }
    .tl-card {
      background: #fff; border-radius: 10px; padding: 10px 12px;
      box-shadow: 0 2px 8px rgba(0,0,0,0.07); border-left: 3px solid var(--pcpot);
    }
    .tl-card .tl-label { font-size: 9px; font-weight: 800; color: var(--pcpot); text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 3px; }
    .tl-card .tl-title { font-size: 13px; font-weight: 900; color: var(--text); margin-bottom: 3px; }
    .tl-card .tl-desc { font-size: 11px; color: var(--muted); line-height: 1.5; font-weight: 600; }

    /* Log form */
    .log-header {
      background: linear-gradient(135deg, #1a2a3a, #2e9e6b);
      border-radius: 12px 12px 0 0; padding: 12px 16px; color: #fff;
    }
    .log-header .lh-title { font-size: 15px; font-weight: 900; }
    .log-header .lh-sub { font-size: 10px; opacity: 0.8; margin-top: 2px; }

    .log-body { background: #fff; border-radius: 0 0 12px 12px; padding: 14px 16px; box-shadow: var(--shadow); margin-bottom: 12px; }

    .sesi-counter {
      display: flex; align-items: center; justify-content: space-between;
      background: #f0f4f8; border-radius: 10px; padding: 10px 14px; margin-bottom: 12px;
    }
    .sesi-counter .sc-label { font-size: 11px; font-weight: 800; color: var(--muted); }
    .sesi-counter .sc-num { font-size: 26px; font-weight: 900; color: var(--pcpot); }
    .sesi-counter .sc-target { font-size: 10px; color: var(--muted); font-weight: 700; }

    /* Progress bar */
    .progress-wrap { background: #eef0f3; border-radius: 50px; height: 8px; margin-bottom: 14px; overflow: hidden; }
    .progress-bar { height: 100%; border-radius: 50px; background: linear-gradient(90deg, #1e6fa8, #2e9e6b); transition: width 0.4s ease; }

    /* Skor comparison */
    .skor-row {
      display: grid; grid-template-columns: 1fr auto 1fr;
      gap: 8px; align-items: center; margin-bottom: 10px;
    }
    .skor-box {
      border-radius: 10px; padding: 10px 8px; text-align: center;
    }
    .skor-box .sb-role { font-size: 9px; font-weight: 800; text-transform: uppercase; letter-spacing: 0.5px; margin-bottom: 4px; }
    .skor-box .sb-val { font-size: 26px; font-weight: 900; line-height: 1; }
    .skor-box.selesai-shift { background: #eaf3fb; border: 1.5px solid #1e6fa8; }
    .skor-box.selesai-shift .sb-role { color: #1e6fa8; }
    .skor-box.selesai-shift .sb-val { color: #1e6fa8; }
    .skor-box.mulai-shift { background: #e6f7ef; border: 1.5px solid #2e9e6b; }
    .skor-box.mulai-shift .sb-role { color: #2e9e6b; }
    .skor-box.mulai-shift .sb-val { color: #2e9e6b; }
    .vs-badge {
      background: #1a2a3a; color: #fff;
      border-radius: 50%; width: 28px; height: 28px;
      display: flex; align-items: center; justify-content: center;
      font-size: 9px; font-weight: 900; flex-shrink: 0;
    }

    /* Kesepakatan */
    .kesepakatan-box {
      background: linear-gradient(135deg, #1a2a3a, #1e6fa8);
      border-radius: 10px; padding: 12px 14px; color: #fff;
      display: flex; align-items: center; gap: 12px; margin-bottom: 12px;
    }
    .kesepakatan-box .kb-label { font-size: 10px; font-weight: 800; opacity: 0.75; text-transform: uppercase; margin-bottom: 2px; }
    .kesepakatan-box .kb-val { font-size: 24px; font-weight: 900; }

    /* Sesi log list */
    .log-list { margin-top: 4px; }
    .log-entry {
      background: #f8fafc; border-radius: 10px; padding: 10px 12px;
      margin-bottom: 8px; border-left: 3px solid #dde3ea; cursor: pointer;
      transition: all 0.15s;
    }
    .log-entry:hover { background: #eaf3fb; border-left-color: var(--pcpot); }
    .log-entry.consensus { border-left-color: #27ae60; }
    .log-entry.discrepancy { border-left-color: #f39c12; }
    .log-entry .le-top { display: flex; justify-content: space-between; align-items: center; margin-bottom: 3px; }
    .log-entry .le-sesi { font-size: 10px; font-weight: 800; color: var(--muted); }
    .log-entry .le-badge { font-size: 9px; font-weight: 800; padding: 2px 8px; border-radius: 50px; }
    .badge-consensus { background: #e8f5e9; color: #27ae60; }
    .badge-discrepancy { background: #fff8e1; color: #e07b00; }
    .log-entry .le-pasien { font-size: 12px; font-weight: 800; color: var(--text); }
    .log-entry .le-skor { font-size: 11px; color: var(--muted); font-weight: 600; }

    /* Shift toggle */
    .shift-toggle {
      display: flex; gap: 0; border-radius: 8px; overflow: hidden;
      border: 1.5px solid var(--pcpot); margin-bottom: 10px;
    }
    .shift-btn {
      flex: 1; padding: 8px 6px; font-size: 10px; font-weight: 800;
      font-family: inherit; border: none; cursor: pointer;
      background: #f0f4f8; color: var(--muted); transition: all 0.15s;
    }
    .shift-btn.active { background: var(--pcpot); color: #fff; }

    .btn-tambah-sesi {
      width: 100%; padding: 12px; border-radius: 10px;
      background: linear-gradient(135deg, #1a2a3a, #2e9e6b);
      color: #fff; border: none; font-size: 13px;
      font-weight: 900; font-family: inherit; cursor: pointer;
      margin-bottom: 10px; transition: opacity 0.15s;
      letter-spacing: 0.3px;
    }
    .btn-tambah-sesi:hover { opacity: 0.88; }

    .btn-reset-huddle {
      width: 100%; padding: 10px; border-radius: 10px;
      background: #fdecea; color: #c0392b;
      border: 1.5px solid #c0392b; font-size: 11px;
      font-weight: 800; font-family: inherit; cursor: pointer;
    }

    .selisih-badge {
      text-align: center; font-size: 11px; font-weight: 800;
      padding: 6px 12px; border-radius: 8px; margin-bottom: 10px;
    }

    /* Input skor number */
    .skor-input {
      width: 100%; text-align: center; font-size: 28px; font-weight: 900;
      border: 2px solid #dde3ea; border-radius: 8px; padding: 6px 4px;
      font-family: inherit; color: var(--text); background: #fff;
      outline: none;
    }
    .skor-input:focus { border-color: var(--pcpot); }

    .input-grid-2 { display: grid; grid-template-columns: 1fr 1fr; gap: 10px; margin-bottom: 10px; }
  </style>

  <!-- HERO -->
  <div class="huddle-hero">
    <div class="hh-badge">⏱ Inovasi Keperawatan PICU RSHS</div>
    <div class="hh-title">Huddle 5 Menit<br>Validasi Nyeri</div>
    <div class="hh-sub">Forum belajar bersama antarperawat saat setiap operan shift — bukan audit, bukan penilaian kinerja</div>
    <div class="hh-chips">
      <span class="hh-chip">🌅 Pagi → Sore</span>
      <span class="hh-chip">🌙 Sore → Malam</span>
      <span class="hh-chip">🌛 Malam → Pagi</span>
      <span class="hh-chip">🎯 Target: 10 Sesi</span>
    </div>
  </div>

  <!-- MEKANISME -->
  <div class="info-card">
    <h3>📋 Mekanisme Huddle — 5 Langkah</h3>
    <div class="timeline">
      <div class="tl-step">
        <div class="tl-dot">1</div>
        <div class="tl-card" style="border-left-color:#1e6fa8">
          <div class="tl-label" style="color:#1e6fa8">Langkah 1 — Pilih Pasien</div>
          <div class="tl-title">Tentukan 1 Pasien yang Dibahas</div>
          <div class="tl-desc">Pilih secara bergantian setiap sesi. Prioritaskan pasien terintubasi yang sedang mendapat tatalaksana nyeri.</div>
        </div>
      </div>
      <div class="tl-step">
        <div class="tl-dot" style="background:#f39c12;box-shadow:0 0 0 2px #f39c12">2</div>
        <div class="tl-card" style="border-left-color:#f39c12">
          <div class="tl-label" style="color:#f39c12">Langkah 2 — Perawat Selesai Shift</div>
          <div class="tl-title">Sampaikan Hasil Pengkajian</div>
          <div class="tl-desc">Jelaskan: (a) instrumen yang digunakan, (b) alasan pemilihan, (c) skor beserta domain spesifik, (d) tindak lanjut yang sudah dilakukan.</div>
        </div>
      </div>
      <div class="tl-step">
        <div class="tl-dot" style="background:#2e9e6b;box-shadow:0 0 0 2px #2e9e6b">3</div>
        <div class="tl-card" style="border-left-color:#2e9e6b">
          <div class="tl-label" style="color:#2e9e6b">Langkah 3 — Perawat Mulai Shift</div>
          <div class="tl-title">Nilai Mandiri dengan QRG Digital</div>
          <div class="tl-desc">Scan QR Code → buka P-CPOT → nilai pasien yang sama secara independen sebelum mendengar skor rekan.</div>
        </div>
      </div>
      <div class="tl-step">
        <div class="tl-dot" style="background:#9b59b6;box-shadow:0 0 0 2px #9b59b6">4</div>
        <div class="tl-card" style="border-left-color:#9b59b6">
          <div class="tl-label" style="color:#9b59b6">Langkah 4 — Bandingkan &amp; Diskusi</div>
          <div class="tl-title">Bahas Perbedaan Skor</div>
          <div class="tl-desc">Jika ada perbedaan: <em>"Domain mana yang kita nilai berbeda? Perilaku apa yang masing-masing kita amati? Mana interpretasi yang lebih akurat?"</em></div>
        </div>
      </div>
      <div class="tl-step" style="margin-bottom:0">
        <div class="tl-dot" style="background:#c0392b;box-shadow:0 0 0 2px #c0392b">5</div>
        <div class="tl-card" style="border-left-color:#c0392b">
          <div class="tl-label" style="color:#c0392b">Langkah 5 — Catat Kesepakatan</div>
          <div class="tl-title">Dokumentasikan Skor Final</div>
          <div class="tl-desc">Catat: instrumen, skor sebelum &amp; sesudah diskusi, kesepakatan akhir, dan rencana intervensi. Gunakan form log di bawah ini.</div>
        </div>
      </div>
    </div>
  </div>

  <!-- INFO BOX -->
  <div class="info-card" style="background:#e8f4fd;border-left:4px solid var(--pcpot)">
    <h3>💡 Prinsip Huddle — Ruang Belajar Aman</h3>
    <p style="font-size:12px;line-height:1.7;color:var(--text)">
      Forum ini <b>bukan penilaian kinerja, bukan audit, dan bukan ancaman</b>. Setiap perawat keluar dengan pemahaman yang lebih baik dari saat mereka masuk. Perbedaan skor adalah peluang belajar — bukan kesalahan yang dihukum.
      <br><br>
      <b style="color:var(--pcpot)">Goldenhar et al. (2013) — BMJ Quality &amp; Safety:</b> Huddle meningkatkan <em>situational awareness</em> tim dan memperkuat budaya keselamatan pasien secara keseluruhan.
    </p>
  </div>

  <!-- LOG FORM -->
  <div class="log-header">
    <div class="lh-title">📝 Log Sesi Huddle</div>
    <div class="lh-sub">Catat setiap sesi — target minimal 10 sesi per 30 hari habituasi</div>
  </div>
  <div class="log-body">

    <!-- Progress -->
    <div class="sesi-counter">
      <div>
        <div class="sc-label">Sesi Terlaksana</div>
        <div class="sc-target">Target: 10 sesi / 30 hari</div>
      </div>
      <div class="sc-num" id="h-sesi-count">0</div>
    </div>
    <div class="progress-wrap">
      <div class="progress-bar" id="h-progress" style="width:0%"></div>
    </div>

    <!-- Form Input Sesi Baru -->
    <div class="form-section" style="background:#f8fafc;border:1.5px solid #dde3ea;box-shadow:none;padding:12px 14px">
      <h3>➕ Tambah Sesi Baru</h3>

      <!-- Shift -->
      <div style="margin-bottom:8px">
        <div class="field-label" style="font-size:11px;font-weight:800;margin-bottom:4px">Shift Operan</div>
        <div class="shift-toggle">
          <button class="shift-btn active" id="h-shift-ps" onclick="setHuddleShift('pagi-sore')">🌅 Pagi→Sore</button>
          <button class="shift-btn" id="h-shift-sm" onclick="setHuddleShift('sore-malam')">🌙 Sore→Malam</button>
          <button class="shift-btn" id="h-shift-mp" onclick="setHuddleShift('malam-pagi')">🌛 Malam→Pagi</button>
        </div>
      </div>

      <!-- Tanggal & Waktu -->
      <div class="field-row" style="margin-bottom:8px">
        <label class="field-label">Tanggal &amp; Jam</label>
        <input class="field-input" type="datetime-local" id="h-waktu">
      </div>

      <!-- Pasien -->
      <div class="input-grid-2">
        <div class="field-row" style="margin-bottom:0">
          <label class="field-label">Nama Pasien</label>
          <input class="field-input" type="text" id="h-pasien" placeholder="Inisial / Nama">
        </div>
        <div class="field-row" style="margin-bottom:0">
          <label class="field-label">No. Bed</label>
          <input class="field-input" type="text" id="h-bed" placeholder="Bed 1...">
        </div>
      </div>

      <!-- Perawat -->
      <div class="input-grid-2" style="margin-top:8px">
        <div class="field-row" style="margin-bottom:0">
          <label class="field-label">Perawat Selesai Shift</label>
          <input class="field-input" type="text" id="h-pw-selesai" placeholder="Nama">
        </div>
        <div class="field-row" style="margin-bottom:0">
          <label class="field-label">Perawat Mulai Shift</label>
          <input class="field-input" type="text" id="h-pw-mulai" placeholder="Nama">
        </div>
      </div>

      <!-- Skor -->
      <div style="margin-top:10px">
        <div class="field-label" style="font-size:11px;font-weight:800;margin-bottom:6px">Skor P-CPOT (0–10)</div>
        <div class="skor-row">
          <div class="skor-box selesai-shift">
            <div class="sb-role">Perawat Selesai</div>
            <input class="skor-input" type="number" id="h-skor-a" min="0" max="10" placeholder="—" oninput="updateSelisih()">
          </div>
          <div class="vs-badge">VS</div>
          <div class="skor-box mulai-shift">
            <div class="sb-role">Perawat Mulai</div>
            <input class="skor-input" type="number" id="h-skor-b" min="0" max="10" placeholder="—" oninput="updateSelisih()">
          </div>
        </div>
        <div id="h-selisih-info" class="selisih-badge" style="display:none"></div>
      </div>

      <!-- Skor Kesepakatan -->
      <div class="kesepakatan-box">
        <div>
          <div class="kb-label">Skor Kesepakatan Akhir</div>
          <div class="kb-val" id="h-skor-final-display">—</div>
        </div>
        <input type="number" id="h-skor-final" min="0" max="10" placeholder="0"
          style="width:60px;text-align:center;font-size:22px;font-weight:900;border:2px solid rgba(255,255,255,0.4);border-radius:8px;padding:4px;background:rgba(255,255,255,0.15);color:#fff;font-family:inherit;outline:none"
          oninput="document.getElementById('h-skor-final-display').textContent=this.value||'—'">
      </div>

      <!-- Catatan diskusi -->
      <div class="field-row" style="margin-bottom:10px">
        <label class="field-label">Catatan Diskusi / Domain yang Berbeda</label>
        <textarea class="field-input" id="h-catatan" rows="2" placeholder="Contoh: Perbedaan pada domain Konsolabilitas — Domain 5. Sepakat skor 1 setelah diskusi."></textarea>
      </div>

      <!-- Tindak lanjut -->
      <div class="field-row" style="margin-bottom:10px">
        <label class="field-label">Tindak Lanjut yang Disepakati</label>
        <input class="field-input" type="text" id="h-tindak" placeholder="Contoh: Laporkan DPJP, berikan analgesik non-opioid">
      </div>

      <button class="btn-tambah-sesi" onclick="tambahSesi()">✅ Simpan Sesi Ini</button>
    </div>

    <!-- Log List -->
    <div id="h-log-list" class="log-list"></div>

    <!-- EXPORT BUTTONS HUDDLE -->
    <div id="h-export-btns" style="display:none;margin-bottom:10px">
      <div style="font-size:10px;font-weight:800;text-transform:uppercase;letter-spacing:0.5px;color:var(--muted);margin-bottom:6px;text-align:center">📤 Export Data Huddle</div>
      <div style="display:grid;grid-template-columns:1fr 1fr;gap:8px">
        <button onclick="exportHuddleCSV()" style="padding:11px 8px;border-radius:10px;background:linear-gradient(135deg,#27ae60,#1e8449);color:#fff;border:none;font-size:11px;font-weight:800;font-family:inherit;cursor:pointer">
          📊 Export CSV
        </button>
        <button onclick="printHuddle()" style="padding:11px 8px;border-radius:10px;background:linear-gradient(135deg,#1a2a3a,#2e9e6b);color:#fff;border:none;font-size:11px;font-weight:800;font-family:inherit;cursor:pointer">
          🖨️ Cetak Rekap / PDF
        </button>
      </div>
    </div>

    <button class="btn-reset-huddle" onclick="resetHuddle()">🔄 Reset Semua Log Huddle</button>
  </div>

  <!-- REKAP -->
  <div class="info-card" id="h-rekap-card" style="display:none">
    <h3>📊 Rekap Huddle</h3>
    <div id="h-rekap-content"></div>
  </div>

</div>

<!-- =================== HALAMAN 7: MEDIA =================== -->
<div class="page" id="page7">
  <div class="page-title">Media Inovasi</div>
  <div class="page-desc">Infografis &amp; QRG Visual — Pengkajian Nyeri Pediatrik PICU RSHS</div>

  <style>
    /* ===== MEDIA TAB STYLES ===== */
    .media-tabs {
      display: flex; gap: 8px; margin-bottom: 14px;
    }
    .media-tab-btn {
      flex: 1; padding: 10px 8px;
      border-radius: 12px; border: 2px solid transparent;
      font-family: inherit; font-size: 11px; font-weight: 800;
      cursor: pointer; transition: all 0.2s;
      text-align: center; line-height: 1.3;
    }
    .media-tab-btn.mt-active {
      box-shadow: 0 4px 14px rgba(0,0,0,0.15);
      transform: translateY(-1px);
    }
    .media-tab-btn:not(.mt-active) {
      background: #fff; opacity: 0.65;
      box-shadow: 0 2px 6px rgba(0,0,0,0.07);
    }

    .media-panel { display: none; }
    .media-panel.mp-active { display: block; }

    .media-img-wrap {
      border-radius: 14px; overflow: hidden;
      box-shadow: 0 6px 28px rgba(0,0,0,0.15);
      margin-bottom: 12px;
      border: 2px solid rgba(0,0,0,0.06);
    }
    .media-img-wrap img {
      width: 100%; display: block;
    }

    .media-caption {
      border-radius: 12px; padding: 12px 14px;
      margin-bottom: 8px;
    }
    .media-caption h4 { font-size: 13px; font-weight: 900; margin-bottom: 4px; }
    .media-caption p { font-size: 11px; line-height: 1.6; opacity: 0.9; font-weight: 600; }

    .media-tag {
      display: inline-block; border-radius: 50px;
      padding: 3px 10px; font-size: 9.5px; font-weight: 800;
      margin-right: 4px; margin-bottom: 4px;
    }
  </style>

  <!-- MEDIA TOGGLE BUTTONS -->
  <div class="media-tabs">
    <button class="media-tab-btn mt-active"
      id="mt-btn-0"
      onclick="switchMedia(0)"
      style="background:linear-gradient(135deg,#1e6fa8,#1a2a3a);color:#fff;border-color:#1e6fa8">
      🩺 QRG<br>P-CPOT
    </button>
    <button class="media-tab-btn"
      id="mt-btn-1"
      onclick="switchMedia(1)"
      style="background:linear-gradient(135deg,#2e9e6b,#1a3a28);color:#fff;border-color:#2e9e6b">
      💡 Inovasi<br>Digital
    </button>
  </div>

  <!-- PANEL 0: QRG P-CPOT -->
  <div class="media-panel mp-active" id="mp-0">
    <div class="media-caption" style="background:linear-gradient(135deg,#1a2a3a,#1e6fa8);color:#fff">
      <h4>Quick Reference Guide — Instrumen P-CPOT</h4>
      <p>Panduan visual lengkap: APA itu P-CPOT, tabel penilaian 5 domain, interpretasi skor, ambang batas intervensi, dan implementasi di PICU RSHS.</p>
      <div style="margin-top:8px">
        <span class="media-tag" style="background:rgba(255,255,255,0.2);color:#fff">⭐ P-CPOT</span>
        <span class="media-tag" style="background:rgba(255,255,255,0.2);color:#fff">5 Domain</span>
        <span class="media-tag" style="background:rgba(255,255,255,0.2);color:#fff">Threshold ≥ 4</span>
        <span class="media-tag" style="background:rgba(255,255,255,0.2);color:#fff">PICU RSHS</span>
      </div>
    </div>
    <div class="media-img-wrap">
      <img src="data:image/jpeg;base64,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" alt="QRG Instrumen P-CPOT">
    </div>
    <div class="info-card" style="background:#eaf3fb;border-left:4px solid var(--pcpot)">
      <h3>📌 Cara Baca Infografis Ini</h3>
      <p style="font-size:11px;line-height:1.7;color:var(--text)">
        Baca dari atas ke bawah: (1) Pahami apa itu P-CPOT dan keunggulannya, (2) Gunakan tabel 5 domain untuk menilai pasien, (3) Hitung total skor, (4) Cocokkan dengan interpretasi, (5) Lakukan intervensi bila skor &gt; 4.
      </p>
    </div>
  </div>

  <!-- PANEL 1: INOVASI DIGITAL -->
  <div class="media-panel" id="mp-1">
    <div class="media-caption" style="background:linear-gradient(135deg,#1a3a28,#2e9e6b);color:#fff">
      <h4>Inovasi Digital &amp; Instrumen Berbasis Bukti</h4>
      <p>Gambaran lengkap inovasi: QRG Digital berbasis QR Code, alur pemilihan instrumen nyeri per usia, instrumen P-CPOT untuk pasien ventilator, Huddle 5 Menit, dan monitoring dampak Pre vs Post.</p>
      <div style="margin-top:8px">
        <span class="media-tag" style="background:rgba(255,255,255,0.2);color:#fff">📱 QR Code</span>
        <span class="media-tag" style="background:rgba(255,255,255,0.2);color:#fff">🤝 Huddle 5 Menit</span>
        <span class="media-tag" style="background:rgba(255,255,255,0.2);color:#fff">📊 Pre vs Post</span>
        <span class="media-tag" style="background:rgba(255,255,255,0.2);color:#fff">SCCM 2022</span>
      </div>
    </div>
    <div class="media-img-wrap">
      <img src="data:image/jpeg;base64,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" alt="Infografis Inovasi Digital PICU">
    </div>
    <div class="info-card" style="background:#e6f7ef;border-left:4px solid var(--green)">
      <h3>📌 Tentang Infografis Ini</h3>
      <p style="font-size:11px;line-height:1.7;color:var(--text)">
        Infografis ini merangkum seluruh inovasi aktualisasi: dari identifikasi masalah (10/10 dokumentasi masih pakai instrumen dewasa) hingga solusi berupa QRG Digital + Huddle 5 Menit, lengkap dengan target 12 perawat terlatih dan evaluasi dampak konsistensi skor nyeri.
      </p>
    </div>
  </div>

</div>

<footer>
  QRG Digital v3.0 | RSUP Dr. Hasan Sadikin Bandung | Habituasi PICU 2026<br>
  Penyusun: Asep Rizkika Setia, A.Md.Kep
</footer>

<script>
  /* ===== TAB NAV ===== */
  function showPage(n) {
    document.querySelectorAll('.page').forEach(function(p, i) {
      p.classList.toggle('active', i === n);
    });
    document.querySelectorAll('.tab-btn').forEach(function(b, i) {
      b.classList.toggle('active', i === n);
    });
    window.scrollTo(0, 0);
  }

  /* ===== FORM LOGIC ===== */
  var scores = { d1: null, d2: null, d3: null, d4: null, d5: null };
  var ventMode = 'terintubasi';

  // Set datetime default
  (function(){
    var now = new Date();
    var pad = function(n){ return n<10?'0'+n:n; };
    var local = now.getFullYear()+'-'+pad(now.getMonth()+1)+'-'+pad(now.getDate())+'T'+pad(now.getHours())+':'+pad(now.getMinutes());
    document.getElementById('f-waktu').value = local;
  })();

  function setVent(mode) {
    ventMode = mode;
    document.getElementById('vent-ya').classList.toggle('active', mode==='terintubasi');
    document.getElementById('vent-tidak').classList.toggle('active', mode==='tidak');

    if (mode === 'terintubasi') {
      document.getElementById('d3-header').innerHTML = '🫁 Domain 3 — Kepatuhan Ventilator';
      document.getElementById('d3-0').textContent = 'Toleran terhadap ventilator, tidak batuk';
      document.getElementById('d3-1').textContent = 'Batuk tapi masih dapat toleransi';
      document.getElementById('d3-2').textContent = 'Fighting ventilator, melawan / asinkroni';
      document.getElementById('vent-note').textContent = 'Domain 3 aktif: Kepatuhan Ventilator';
    } else {
      document.getElementById('d3-header').innerHTML = '😮 Domain 3 — Vokalisasi';
      document.getElementById('d3-0').textContent = 'Tidak menangis, tenang, bersuara normal';
      document.getElementById('d3-1').textContent = 'Erangan / rengekan pelan';
      document.getElementById('d3-2').textContent = 'Menangis keras / menjerit';
      document.getElementById('vent-note').textContent = 'Domain 3 aktif: Vokalisasi';
    }
    // Reset d3 selection
    scores.d3 = null;
    document.querySelectorAll('#d3 .radio-option').forEach(function(el){
      el.classList.remove('selected','selected-1','selected-2');
    });
    updateScore();
  }

  function selectOption(domain, val, el) {
    scores[domain] = val;
    var container = document.getElementById(domain);
    container.querySelectorAll('.radio-option').forEach(function(opt){
      opt.classList.remove('selected','selected-1','selected-2');
    });
    if (val === 0) el.classList.add('selected');
    else if (val === 1) el.classList.add('selected-1');
    else el.classList.add('selected-2');
    updateScore();
  }

  function updateScore() {
    var total = 0;
    var allFilled = true;
    ['d1','d2','d3','d4','d5'].forEach(function(d){
      if (scores[d] === null) { allFilled = false; }
      else { total += scores[d]; }
    });

    var disp = document.getElementById('score-display');
    var num = document.getElementById('score-num');
    var interp = document.getElementById('score-interp');

    if (!allFilled) {
      num.textContent = '—';
      interp.innerHTML = '<span style="opacity:0.7">Pilih semua domain untuk melihat skor</span>';
      disp.style.background = 'linear-gradient(135deg,#1a2a3a,#1e6fa8)';
      document.getElementById('checklist-section').style.display = 'none';
      return;
    }

    num.textContent = total;
    document.getElementById('checklist-section').style.display = 'block';

    if (total <= 3) {
      disp.style.background = 'linear-gradient(135deg,#27ae60,#1e8449)';
      interp.innerHTML = '🟢 <b>Tidak Ada / Nyeri Ringan</b> — Monitoring setiap <b>8 jam</b> (SOP RSHS)';
      renderChecklist('ringan');
    } else if (total <= 6) {
      disp.style.background = 'linear-gradient(135deg,#f39c12,#d68910)';
      interp.innerHTML = '🟡 <b>Nyeri Sedang</b> — Intervensi + monitoring setiap 2 jam';
      renderChecklist('sedang');
    } else {
      disp.style.background = 'linear-gradient(135deg,#e74c3c,#c0392b)';
      interp.innerHTML = '🔴 <b>Nyeri Berat</b> — Intervensi SEGERA + monitoring setiap 1 jam';
      renderChecklist('berat');
    }
  }

  var checklistDefs = {
    ringan: [
      'Lanjutkan monitoring rutin setiap 8 jam',
      'Pertahankan posisi nyaman pasien',
      'Jaga lingkungan tenang (redupkan lampu, kurangi kebisingan)',
      'Intervensi non-farmakologis: sentuhan lembut, musik, swaddling',
      'Dokumentasikan skor dalam rekam medis / flowchart'
    ],
    sedang: [
      'Laporkan ke dokter / DPJP segera',
      'Berikan analgesik sesuai advis (non-opioid lini pertama)',
      'Intervensi non-farmakologis: reposisi, distraksi, sentuhan',
      'Evaluasi ulang skor P-CPOT setelah 30 menit intervensi',
      'Monitoring ketat setiap 2 jam',
      'Dokumentasikan intervensi, waktu, dan respons pasien'
    ],
    berat: [
      '🚨 Aktifkan protokol nyeri berat PICU — jangan tunda!',
      'Hubungi dokter / DPJP SEGERA',
      'Siapkan opioid IV sesuai advis DPJP (SCCM 2022)',
      'Monitor tanda vital, saturasi, dan efek samping',
      'Evaluasi skor P-CPOT setiap 1 jam hingga skor < 4',
      'Libatkan keluarga untuk menenangkan pasien',
      'Dokumentasikan waktu intervensi, dosis, dan respons'
    ]
  };

  var checkStates = {};

  function renderChecklist(level) {
    var items = checklistDefs[level];
    var container = document.getElementById('checklist-items');
    container.innerHTML = '';
    checkStates = {};
    items.forEach(function(text, i) {
      checkStates[i] = false;
      var div = document.createElement('div');
      div.className = 'check-item';
      div.id = 'ci-' + i;
      div.innerHTML = '<div class="check-box" id="cb-'+i+'"></div><div class="check-text">'+text+'</div>';
      div.onclick = function() { toggleCheck(i); };
      container.appendChild(div);
    });
  }

  function toggleCheck(i) {
    checkStates[i] = !checkStates[i];
    var item = document.getElementById('ci-' + i);
    var box = document.getElementById('cb-' + i);
    if (checkStates[i]) {
      item.classList.add('checked');
      box.textContent = '✓';
    } else {
      item.classList.remove('checked');
      box.textContent = '';
    }
  }

  function saveSummary() {
    var nama = document.getElementById('f-nama').value || '—';
    var rm = document.getElementById('f-rm').value || '—';
    var usia = document.getElementById('f-usia').value || '—';
    var waktu = document.getElementById('f-waktu').value || '—';
    var perawat = document.getElementById('f-perawat').value || '—';
    var catatan = document.getElementById('f-catatan').value || '—';
    var total = document.getElementById('score-num').textContent;
    var interp = document.getElementById('score-interp').textContent;

    var ts = new Date().toLocaleString('id-ID');
    document.getElementById('saved-ts').textContent = '✅ Tersimpan: ' + ts;

    var box = document.getElementById('summary-box');
    box.style.display = 'block';
    box.innerHTML = '<div class="info-card" style="border:2px solid var(--pcpot)">' +
      '<h3>📋 Ringkasan Pengkajian</h3>' +
      '<div class="meta-row"><span class="meta-key">Pasien</span><span class="meta-val">' + nama + '</span></div>' +
      '<div class="meta-row"><span class="meta-key">No. RM</span><span class="meta-val">' + rm + '</span></div>' +
      '<div class="meta-row"><span class="meta-key">Usia</span><span class="meta-val">' + usia + '</span></div>' +
      '<div class="meta-row"><span class="meta-key">Waktu</span><span class="meta-val">' + waktu + '</span></div>' +
      '<div class="meta-row"><span class="meta-key">Status Ventilasi</span><span class="meta-val">' + (ventMode==='terintubasi'?'Terintubasi':'Tidak Terintubasi') + '</span></div>' +
      '<div class="meta-row"><span class="meta-key">D1 Ekspresi Wajah</span><span class="meta-val">' + (scores.d1 !== null ? scores.d1 : '—') + '</span></div>' +
      '<div class="meta-row"><span class="meta-key">D2 Gerakan Tubuh</span><span class="meta-val">' + (scores.d2 !== null ? scores.d2 : '—') + '</span></div>' +
      '<div class="meta-row"><span class="meta-key">D3 ' + (ventMode==='terintubasi'?'Ventilator':'Vokalisasi') + '</span><span class="meta-val">' + (scores.d3 !== null ? scores.d3 : '—') + '</span></div>' +
      '<div class="meta-row"><span class="meta-key">D4 Tegangan Otot</span><span class="meta-val">' + (scores.d4 !== null ? scores.d4 : '—') + '</span></div>' +
      '<div class="meta-row"><span class="meta-key">D5 Konsolabilitas</span><span class="meta-val">' + (scores.d5 !== null ? scores.d5 : '—') + '</span></div>' +
      '<div class="meta-row"><span class="meta-key">Total Skor</span><span class="meta-val" style="font-size:16px;font-weight:900">' + total + ' / 10</span></div>' +
      '<div class="meta-row"><span class="meta-key">Interpretasi</span><span class="meta-val">' + interp + '</span></div>' +
      '<div class="meta-row"><span class="meta-key">Catatan</span><span class="meta-val">' + catatan + '</span></div>' +
      '<div class="meta-row"><span class="meta-key">Perawat</span><span class="meta-val">' + perawat + '</span></div>' +
      '</div>';

    box.scrollIntoView({ behavior: 'smooth' });
  }

  function resetForm() {
    if (!confirm('Reset semua isian formulir?')) return;
    document.getElementById('f-nama').value = '';
    document.getElementById('f-rm').value = '';
    document.getElementById('f-usia').value = '';
    document.getElementById('f-catatan').value = '';
    document.getElementById('f-perawat').value = '';
    // Reset datetime to now
    var now = new Date();
    var pad = function(n){ return n<10?'0'+n:n; };
    var local = now.getFullYear()+'-'+pad(now.getMonth()+1)+'-'+pad(now.getDate())+'T'+pad(now.getHours())+':'+pad(now.getMinutes());
    document.getElementById('f-waktu').value = local;
    scores = { d1: null, d2: null, d3: null, d4: null, d5: null };
    ['d1','d2','d3','d4','d5'].forEach(function(d){
      document.querySelectorAll('#'+d+' .radio-option').forEach(function(el){
        el.classList.remove('selected','selected-1','selected-2');
      });
    });
    document.getElementById('checklist-section').style.display = 'none';
    document.getElementById('summary-box').style.display = 'none';
    document.getElementById('export-lembar-btns').style.display = 'none';
    document.getElementById('saved-ts').textContent = '';
    document.getElementById('score-num').textContent = '—';
    document.getElementById('score-interp').innerHTML = '<span style="opacity:0.7">Pilih semua domain untuk melihat skor</span>';
    document.getElementById('score-display').style.background = 'linear-gradient(135deg,#1a2a3a,#1e6fa8)';
    setVent('terintubasi');
  }
  /* ===== HUDDLE LOGIC ===== */
  var huddleShift = 'pagi-sore';
  var huddleLogs = [];

  // Set datetime default for huddle
  (function(){
    var now = new Date();
    var pad = function(n){ return n<10?'0'+n:n; };
    var local = now.getFullYear()+'-'+pad(now.getMonth()+1)+'-'+pad(now.getDate())+'T'+pad(now.getHours())+':'+pad(now.getMinutes());
    var wEl = document.getElementById('h-waktu');
    if(wEl) wEl.value = local;
  })();

  function setHuddleShift(mode) {
    huddleShift = mode;
    document.getElementById('h-shift-ps').classList.toggle('active', mode==='pagi-sore');
    document.getElementById('h-shift-sm').classList.toggle('active', mode==='sore-malam');
    document.getElementById('h-shift-mp').classList.toggle('active', mode==='malam-pagi');
  }

  function updateSelisih() {
    var a = document.getElementById('h-skor-a').value;
    var b = document.getElementById('h-skor-b').value;
    var el = document.getElementById('h-selisih-info');
    if (a==='' || b==='') { el.style.display='none'; return; }
    var selisih = Math.abs(parseInt(a) - parseInt(b));
    el.style.display = 'block';
    if (selisih === 0) {
      el.style.background = '#e8f5e9'; el.style.color = '#27ae60';
      el.textContent = '✅ Skor sama — tidak ada perbedaan penilaian';
    } else {
      el.style.background = '#fff8e1'; el.style.color = '#e07b00';
      el.textContent = '⚠️ Selisih ' + selisih + ' poin — perlu diskusi domain yang berbeda';
    }
  }

  function tambahSesi() {
    var pasien = document.getElementById('h-pasien').value.trim();
    var bed = document.getElementById('h-bed').value.trim();
    var pwA = document.getElementById('h-pw-selesai').value.trim();
    var pwB = document.getElementById('h-pw-mulai').value.trim();
    var waktu = document.getElementById('h-waktu').value;
    var skorA = document.getElementById('h-skor-a').value;
    var skorB = document.getElementById('h-skor-b').value;
    var skorFinal = document.getElementById('h-skor-final').value;
    var catatan = document.getElementById('h-catatan').value.trim();
    var tindak = document.getElementById('h-tindak').value.trim();

    if (!pasien || skorA==='' || skorB==='' || skorFinal==='') {
      alert('Harap isi: Nama Pasien, Skor A, Skor B, dan Skor Kesepakatan.');
      return;
    }

    var entry = {
      id: Date.now(),
      sesi: huddleLogs.length + 1,
      shift: huddleShift,
      waktu: waktu,
      pasien: pasien, bed: bed,
      pwA: pwA, pwB: pwB,
      skorA: parseInt(skorA), skorB: parseInt(skorB),
      skorFinal: parseInt(skorFinal),
      catatan: catatan, tindak: tindak,
      selisih: Math.abs(parseInt(skorA)-parseInt(skorB))
    };

    huddleLogs.push(entry);
    renderHuddleLogs();
    clearHuddleForm();
  }

  function clearHuddleForm() {
    document.getElementById('h-pasien').value = '';
    document.getElementById('h-bed').value = '';
    document.getElementById('h-pw-selesai').value = '';
    document.getElementById('h-pw-mulai').value = '';
    document.getElementById('h-skor-a').value = '';
    document.getElementById('h-skor-b').value = '';
    document.getElementById('h-skor-final').value = '';
    document.getElementById('h-skor-final-display').textContent = '—';
    document.getElementById('h-catatan').value = '';
    document.getElementById('h-tindak').value = '';
    document.getElementById('h-selisih-info').style.display = 'none';
  }

  function renderHuddleLogs() {
    var count = huddleLogs.length;
    document.getElementById('h-sesi-count').textContent = count;
    var pct = Math.min(count / 10 * 100, 100);
    document.getElementById('h-progress').style.width = pct + '%';

    var container = document.getElementById('h-log-list');
    container.innerHTML = '';

    if (count === 0) return;

    var title = document.createElement('div');
    title.style.cssText = 'font-size:11px;font-weight:800;text-transform:uppercase;letter-spacing:0.5px;color:var(--muted);margin-bottom:8px;margin-top:4px';
    title.textContent = 'Riwayat Sesi';
    container.appendChild(title);

    huddleLogs.slice().reverse().forEach(function(e) {
      var isConsensus = e.selisih === 0;
      var shiftLabel = e.shift === 'pagi-sore' ? '🌅 Pagi→Sore' : e.shift === 'sore-malam' ? '🌙 Sore→Malam' : '🌛 Malam→Pagi';
      var waktuStr = e.waktu ? new Date(e.waktu).toLocaleString('id-ID',{day:'2-digit',month:'short',hour:'2-digit',minute:'2-digit'}) : '—';

      var div = document.createElement('div');
      div.className = 'log-entry ' + (isConsensus ? 'consensus' : 'discrepancy');
      div.innerHTML =
        '<div class="le-top">' +
          '<span class="le-sesi">Sesi ' + e.sesi + ' · ' + shiftLabel + ' · ' + waktuStr + '</span>' +
          '<span class="le-badge ' + (isConsensus ? 'badge-consensus' : 'badge-discrepancy') + '">' +
            (isConsensus ? '✅ Sepakat' : '⚠️ Selisih ' + e.selisih) +
          '</span>' +
        '</div>' +
        '<div class="le-pasien">' + e.pasien + (e.bed ? ' · Bed ' + e.bed : '') + '</div>' +
        '<div class="le-skor">Skor: <b>' + e.skorA + '</b> (selesai) vs <b>' + e.skorB + '</b> (mulai) → Kesepakatan: <b style="color:var(--pcpot)">' + e.skorFinal + '</b>' +
          (e.catatan ? '<br><span style="font-size:10px;opacity:0.8">' + e.catatan + '</span>' : '') +
          (e.tindak ? '<br><span style="font-size:10px;color:#2e9e6b;font-weight:800">→ ' + e.tindak + '</span>' : '') +
        '</div>';
      container.appendChild(div);
    });

    // Rekap
    renderRekap();
  }

  function renderRekap() {
    var card = document.getElementById('h-rekap-card');
    var content = document.getElementById('h-rekap-content');
    if (huddleLogs.length === 0) { card.style.display = 'none'; return; }
    card.style.display = 'block';

    var totalSesi = huddleLogs.length;
    var konsensus = huddleLogs.filter(function(e){ return e.selisih===0; }).length;
    var diskrepansi = totalSesi - konsensus;
    var avgSelisih = (huddleLogs.reduce(function(s,e){ return s+e.selisih; }, 0) / totalSesi).toFixed(1);

    content.innerHTML =
      '<div style="display:grid;grid-template-columns:1fr 1fr;gap:8px">' +
        '<div style="background:#e8f5e9;border-radius:10px;padding:10px;text-align:center">' +
          '<div style="font-size:22px;font-weight:900;color:#27ae60">' + konsensus + '</div>' +
          '<div style="font-size:10px;font-weight:800;color:#27ae60">Sesi Konsensus</div>' +
        '</div>' +
        '<div style="background:#fff8e1;border-radius:10px;padding:10px;text-align:center">' +
          '<div style="font-size:22px;font-weight:900;color:#e07b00">' + diskrepansi + '</div>' +
          '<div style="font-size:10px;font-weight:800;color:#e07b00">Sesi Diskrepansi</div>' +
        '</div>' +
      '</div>' +
      '<div style="margin-top:8px;background:#eaf3fb;border-radius:10px;padding:10px;display:flex;justify-content:space-between;align-items:center">' +
        '<span style="font-size:11px;font-weight:800;color:var(--muted)">Rata-rata Selisih Skor</span>' +
        '<span style="font-size:18px;font-weight:900;color:var(--pcpot)">' + avgSelisih + ' poin</span>' +
      '</div>' +
      (totalSesi >= 10 ?
        '<div style="margin-top:8px;background:linear-gradient(135deg,#1a2a3a,#2e9e6b);border-radius:10px;padding:10px;text-align:center;color:#fff">' +
          '<div style="font-size:14px;font-weight:900">🎉 Target 10 Sesi Tercapai!</div>' +
          '<div style="font-size:10px;opacity:0.85;margin-top:2px">Siap untuk evaluasi dampak QRG Digital &amp; Huddle</div>' +
        '</div>' : '');
  }

  function resetHuddle() {
    if (!confirm('Reset semua log huddle?')) return;
    huddleLogs = [];
    renderHuddleLogs();
    document.getElementById('h-rekap-card').style.display = 'none';
  }

  /* ===== MEDIA TOGGLE ===== */
  function switchMedia(idx) {
    var panels = document.querySelectorAll('.media-panel');
    var btns = document.querySelectorAll('.media-tab-btn');
    var colors = [
      'linear-gradient(135deg,#1e6fa8,#1a2a3a)',
      'linear-gradient(135deg,#2e9e6b,#1a3a28)'
    ];
    var borderColors = ['#1e6fa8', '#2e9e6b'];

    panels.forEach(function(p, i) {
      p.classList.toggle('mp-active', i === idx);
    });
    btns.forEach(function(b, i) {
      if (i === idx) {
        b.classList.add('mt-active');
        b.style.background = colors[i];
        b.style.opacity = '1';
        b.style.transform = 'translateY(-1px)';
        b.style.borderColor = borderColors[i];
      } else {
        b.classList.remove('mt-active');
        b.style.opacity = '0.55';
        b.style.transform = 'none';
        b.style.background = '#fff';
        b.style.color = '#1a2a3a';
      }
    });
  }

  /* ===================================================================
     EXPORT & STORAGE — Lembar Pengkajian
  =================================================================== */

  var lembarRiwayat = [];

  // Load saved records from localStorage on page load
  (function loadStorage() {
    try {
      var saved = localStorage.getItem('qrg_lembar_riwayat');
      if (saved) {
        lembarRiwayat = JSON.parse(saved);
        renderRiwayat();
      }
      var savedHuddle = localStorage.getItem('qrg_huddle_logs');
      if (savedHuddle) {
        huddleLogs = JSON.parse(savedHuddle);
        renderHuddleLogs();
      }
    } catch(e) {}
    updateRiwayatBadge();
  })();

  function saveToStorage() {
    try {
      localStorage.setItem('qrg_lembar_riwayat', JSON.stringify(lembarRiwayat));
      localStorage.setItem('qrg_huddle_logs', JSON.stringify(huddleLogs));
    } catch(e) {}
  }

  function getCurrentLembarData() {
    var nama   = document.getElementById('f-nama').value || '—';
    var rm     = document.getElementById('f-rm').value || '—';
    var usia   = document.getElementById('f-usia').value || '—';
    var waktu  = document.getElementById('f-waktu').value || '—';
    var perawat= document.getElementById('f-perawat').value || '—';
    var catatan= document.getElementById('f-catatan').value || '—';
    var total  = document.getElementById('score-num').textContent;
    var interp = document.getElementById('score-interp').textContent.replace(/<[^>]*>/g,'');
    var ventStr= ventMode === 'terintubasi' ? 'Terintubasi' : 'Tidak Terintubasi';
    var d3lbl  = ventMode === 'terintubasi' ? 'Ventilator' : 'Vokalisasi';
    return {
      id: Date.now(),
      waktu: waktu,
      nama: nama, rm: rm, usia: usia,
      ventilasi: ventStr,
      d1: scores.d1 !== null ? scores.d1 : '—',
      d2: scores.d2 !== null ? scores.d2 : '—',
      d3label: d3lbl,
      d3: scores.d3 !== null ? scores.d3 : '—',
      d4: scores.d4 !== null ? scores.d4 : '—',
      d5: scores.d5 !== null ? scores.d5 : '—',
      total: total,
      interpretasi: interp,
      catatan: catatan,
      perawat: perawat
    };
  }

  // Export satu record saat ini ke CSV
  function exportLembarCSV() {
    var d = getCurrentLembarData();
    var header = ['Waktu Pengkajian','Nama Pasien','No RM','Usia','Status Ventilasi',
      'D1 Ekspresi Wajah','D2 Gerakan Tubuh','D3 ('+d.d3label+')','D4 Tegangan Otot',
      'D5 Konsolabilitas','Total Skor','Interpretasi','Catatan Klinis','Perawat Pengkaji'];
    var row = [d.waktu, d.nama, d.rm, d.usia, d.ventilasi,
      d.d1, d.d2, d.d3, d.d4, d.d5, d.total, d.interpretasi, d.catatan, d.perawat];
    var csv = header.map(csvEsc).join(',') + '\n' + row.map(csvEsc).join(',');
    var ts = new Date().toISOString().slice(0,10);
    downloadCSV('Lembar_PCPOT_' + (d.nama !== '—' ? d.nama.replace(/\s+/g,'_') : 'Pasien') + '_' + ts + '.csv', csv);
  }

  // Simpan record ke riwayat lokal
  function tambahKeRiwayat() {
    if (document.getElementById('score-num').textContent === '—') {
      alert('Harap simpan ringkasan terlebih dahulu sebelum menyimpan ke riwayat.');
      return;
    }
    var d = getCurrentLembarData();
    lembarRiwayat.unshift(d);
    saveToStorage();
    renderRiwayat();
    updateRiwayatBadge();
    // Show panel
    document.getElementById('riwayat-panel').style.display = 'block';
    var ts = new Date().toLocaleString('id-ID');
    document.getElementById('saved-ts').textContent = '✅ Tersimpan ke riwayat: ' + ts;
  }

  function updateRiwayatBadge() {
    var badge = document.getElementById('riwayat-count-badge');
    if (badge) badge.textContent = lembarRiwayat.length;
  }

  function toggleRiwayat() {
    var panel = document.getElementById('riwayat-panel');
    panel.style.display = panel.style.display === 'none' ? 'block' : 'none';
  }

  function renderRiwayat() {
    updateRiwayatBadge();
    var list = document.getElementById('riwayat-list');
    if (!list) return;
    if (lembarRiwayat.length === 0) {
      list.innerHTML = '<div style="text-align:center;font-size:12px;color:var(--muted);padding:12px">Belum ada riwayat tersimpan.</div>';
      return;
    }
    list.innerHTML = '';
    lembarRiwayat.forEach(function(d, i) {
      var interpColor = d.total <= 3 ? '#27ae60' : d.total <= 6 ? '#e07b00' : '#c0392b';
      var wStr = d.waktu && d.waktu !== '—' ? new Date(d.waktu).toLocaleString('id-ID',{day:'2-digit',month:'short',year:'numeric',hour:'2-digit',minute:'2-digit'}) : d.waktu;
      var el = document.createElement('div');
      el.style.cssText = 'background:#f8fafc;border-radius:10px;padding:10px 12px;margin-bottom:8px;border-left:3px solid '+interpColor+';position:relative';
      el.innerHTML =
        '<div style="display:flex;justify-content:space-between;align-items:flex-start;margin-bottom:3px">' +
          '<span style="font-size:12px;font-weight:900;color:var(--text)">' + d.nama + '</span>' +
          '<span style="background:'+interpColor+';color:#fff;border-radius:50px;padding:2px 8px;font-size:10px;font-weight:800">Skor '+d.total+'</span>' +
        '</div>' +
        '<div style="font-size:10px;color:var(--muted);font-weight:700">RM: '+d.rm+' | Usia: '+d.usia+' | '+d.ventilasi+'</div>' +
        '<div style="font-size:10px;color:var(--muted);margin-top:2px">'+wStr+' | '+d.perawat+'</div>' +
        '<div style="display:flex;gap:6px;margin-top:6px">' +
          '<button onclick="exportSingleRiwayat('+i+')" style="flex:1;padding:5px;border-radius:7px;background:linear-gradient(135deg,#27ae60,#1e8449);color:#fff;border:none;font-size:10px;font-weight:800;font-family:inherit;cursor:pointer">📊 CSV</button>' +
          '<button onclick="printSingleRiwayat('+i+')" style="flex:1;padding:5px;border-radius:7px;background:linear-gradient(135deg,#1a2a3a,#1e6fa8);color:#fff;border:none;font-size:10px;font-weight:800;font-family:inherit;cursor:pointer">🖨️ Print</button>' +
          '<button onclick="hapusSatuRiwayat('+i+')" style="padding:5px 8px;border-radius:7px;background:#fdecea;color:#c0392b;border:1px solid #c0392b;font-size:10px;font-weight:800;font-family:inherit;cursor:pointer">🗑️</button>' +
        '</div>';
      list.appendChild(el);
    });
  }

  function hapusSatuRiwayat(i) {
    if (!confirm('Hapus record ini?')) return;
    lembarRiwayat.splice(i, 1);
    saveToStorage();
    renderRiwayat();
  }

  function exportSingleRiwayat(i) {
    var d = lembarRiwayat[i];
    var header = ['Waktu Pengkajian','Nama Pasien','No RM','Usia','Status Ventilasi',
      'D1 Ekspresi Wajah','D2 Gerakan Tubuh','D3 ('+d.d3label+')','D4 Tegangan Otot',
      'D5 Konsolabilitas','Total Skor','Interpretasi','Catatan Klinis','Perawat Pengkaji'];
    var row = [d.waktu, d.nama, d.rm, d.usia, d.ventilasi,
      d.d1, d.d2, d.d3, d.d4, d.d5, d.total, d.interpretasi, d.catatan, d.perawat];
    var csv = header.map(csvEsc).join(',') + '\n' + row.map(csvEsc).join(',');
    downloadCSV('Lembar_' + d.nama.replace(/\s+/g,'_') + '_' + (d.waktu||'').slice(0,10) + '.csv', csv);
  }

  function exportAllLembarCSV() {
    if (lembarRiwayat.length === 0) { alert('Riwayat masih kosong.'); return; }
    var header = ['Waktu Pengkajian','Nama Pasien','No RM','Usia','Status Ventilasi',
      'D1 Ekspresi Wajah','D2 Gerakan Tubuh','D3 Ventilator/Vokalisasi','D4 Tegangan Otot',
      'D5 Konsolabilitas','Total Skor','Interpretasi','Catatan Klinis','Perawat Pengkaji'];
    var rows = lembarRiwayat.map(function(d) {
      return [d.waktu, d.nama, d.rm, d.usia, d.ventilasi,
        d.d1, d.d2, d.d3, d.d4, d.d5, d.total, d.interpretasi, d.catatan, d.perawat].map(csvEsc).join(',');
    });
    var csv = header.map(csvEsc).join(',') + '\n' + rows.join('\n');
    downloadCSV('Riwayat_Lembar_PCPOT_' + new Date().toISOString().slice(0,10) + '.csv', csv);
  }

  function clearRiwayat() {
    if (!confirm('Hapus semua riwayat pengkajian?')) return;
    lembarRiwayat = [];
    saveToStorage();
    renderRiwayat();
  }

  // Print satu lembar
  function printLembar() {
    var d = getCurrentLembarData();
    _printWindow(buildLembarHTML(d), 'Lembar Pengkajian P-CPOT');
  }

  function printSingleRiwayat(i) {
    _printWindow(buildLembarHTML(lembarRiwayat[i]), 'Lembar Pengkajian P-CPOT');
  }

  function buildLembarHTML(d) {
    var interpColor = parseInt(d.total) <= 3 ? '#27ae60' : parseInt(d.total) <= 6 ? '#e07b00' : '#c0392b';
    var interpText  = parseInt(d.total) <= 3 ? 'Tidak Ada / Nyeri Ringan' : parseInt(d.total) <= 6 ? 'Nyeri Sedang' : 'Nyeri Berat';
    var freqText    = parseInt(d.total) <= 3 ? 'Setiap 8 jam' : parseInt(d.total) <= 6 ? 'Setiap 2 jam' : 'Setiap 1 jam';
    var wStr = d.waktu && d.waktu !== '—' ? new Date(d.waktu).toLocaleString('id-ID',{weekday:'long',day:'2-digit',month:'long',year:'numeric',hour:'2-digit',minute:'2-digit'}) : d.waktu;

    var domainRows = [
      ['D1 — Ekspresi Wajah', d.d1, 'Skor 0: Rileks | Skor 1: Tegang | Skor 2: Meringis'],
      ['D2 — Gerakan Tubuh', d.d2, 'Skor 0: Normal | Skor 1: Melindungi | Skor 2: Gelisah/Menarik selang'],
      ['D3 — '+d.d3label, d.d3, d.d3label==='Ventilator' ? 'Skor 0: Toleran | Skor 1: Batuk toleransi | Skor 2: Fighting vent' : 'Skor 0: Tenang | Skor 1: Erangan | Skor 2: Menangis keras'],
      ['D4 — Tegangan Otot', d.d4, 'Skor 0: Relaks | Skor 1: Sedikit kaku | Skor 2: Sangat kaku/fleksi'],
      ['D5 — Konsolabilitas', d.d5, 'Skor 0: Mudah tenang | Skor 1: Tenang dgn sentuhan | Skor 2: Tidak bisa ditenangkan']
    ];

    var dRows = domainRows.map(function(r){
      return '<tr><td style="padding:7px 10px;border:1px solid #e0e8f0;font-weight:700;font-size:12px">'+r[0]+'</td>' +
             '<td style="padding:7px 10px;border:1px solid #e0e8f0;text-align:center;font-size:18px;font-weight:900;color:'+(r[1]=='2'?'#c0392b':r[1]=='1'?'#e07b00':'#27ae60')+'">'+(r[1]!=='—'?r[1]:'—')+'</td>' +
             '<td style="padding:7px 10px;border:1px solid #e0e8f0;font-size:11px;color:#6c7a89">'+r[2]+'</td></tr>';
    }).join('');

    return '<html><head><meta charset="UTF-8"><title>Lembar Pengkajian P-CPOT</title>' +
    '<style>body{font-family:Arial,sans-serif;margin:0;padding:24px;color:#1a2a3a;font-size:13px}' +
    '@media print{body{padding:12px}.no-print{display:none}}' +
    'table{width:100%;border-collapse:collapse}th,td{text-align:left}' +
    '.header-bar{background:linear-gradient(135deg,#1a2a3a,#1e6fa8);color:#fff;border-radius:10px;padding:16px 20px;margin-bottom:16px}' +
    '.section-title{font-size:11px;font-weight:800;text-transform:uppercase;letter-spacing:0.5px;color:#6c7a89;margin:14px 0 6px}' +
    '.score-box{border-radius:10px;padding:14px 20px;color:#fff;display:flex;align-items:center;gap:16px;margin-bottom:12px}' +
    '.tanda-tangan{display:grid;grid-template-columns:1fr 1fr;gap:20px;margin-top:20px}' +
    '.ttd-box{border-top:1.5px solid #dde3ea;padding-top:8px}' +
    '</style></head><body>' +
    '<div class="header-bar">' +
      '<div style="font-size:10px;opacity:0.7;letter-spacing:1px;text-transform:uppercase;margin-bottom:4px">RSUP Dr. Hasan Sadikin Bandung — PICU</div>' +
      '<div style="font-size:20px;font-weight:900;margin-bottom:2px">Lembar Pengkajian Nyeri P-CPOT</div>' +
      '<div style="font-size:11px;opacity:0.85">Pediatric Critical-Care Pain Observation Tool | SOP RSHS 2026</div>' +
    '</div>' +
    '<div class="section-title">Identitas Pasien</div>' +
    '<table style="margin-bottom:10px"><tr>' +
      '<td style="width:50%;padding:4px 0"><b>Nama:</b> '+d.nama+'</td>' +
      '<td style="padding:4px 0"><b>No. RM:</b> '+d.rm+'</td></tr><tr>' +
      '<td style="padding:4px 0"><b>Usia:</b> '+d.usia+'</td>' +
      '<td style="padding:4px 0"><b>Status Ventilasi:</b> '+d.ventilasi+'</td></tr><tr>' +
      '<td colspan="2" style="padding:4px 0"><b>Tanggal &amp; Jam:</b> '+wStr+'</td></tr></table>' +
    '<div class="section-title">Penilaian 5 Domain P-CPOT</div>' +
    '<table style="margin-bottom:12px"><thead><tr>' +
      '<th style="padding:7px 10px;border:1px solid #e0e8f0;background:#f0f4f8;font-size:11px">Domain</th>' +
      '<th style="padding:7px 10px;border:1px solid #e0e8f0;background:#f0f4f8;font-size:11px;width:60px;text-align:center">Skor</th>' +
      '<th style="padding:7px 10px;border:1px solid #e0e8f0;background:#f0f4f8;font-size:11px">Deskripsi</th>' +
    '</tr></thead><tbody>'+dRows+'</tbody></table>' +
    '<div class="score-box" style="background:'+interpColor+'">' +
      '<div style="font-size:48px;font-weight:900;line-height:1">'+d.total+'</div>' +
      '<div><div style="font-size:14px;font-weight:800">'+interpText+'</div>' +
      '<div style="font-size:12px;opacity:0.9;margin-top:2px">Monitoring: <b>'+freqText+'</b> (SOP RSHS)</div></div>' +
    '</div>' +
    (d.catatan && d.catatan !== '—' ? '<div class="section-title">Catatan Klinis</div><div style="background:#f0f4f8;border-radius:8px;padding:10px 12px;font-size:12px;margin-bottom:12px">'+d.catatan+'</div>' : '') +
    '<div class="tanda-tangan">' +
      '<div class="ttd-box"><div style="font-size:11px;color:#6c7a89;margin-bottom:4px">Perawat Pengkaji</div><div style="font-weight:800;font-size:13px">'+d.perawat+'</div><div style="font-size:10px;color:#6c7a89;margin-top:28px">Tanda Tangan: ___________________</div></div>' +
      '<div class="ttd-box"><div style="font-size:11px;color:#6c7a89;margin-bottom:4px">Dicetak</div><div style="font-weight:700;font-size:12px">'+new Date().toLocaleString('id-ID')+'</div><div style="font-size:10px;color:#6c7a89;margin-top:4px">QRG Digital v2.0 | PICU RSHS</div></div>' +
    '</div>' +
    '<div class="no-print" style="margin-top:20px;text-align:center"><button onclick="window.print()" style="padding:10px 24px;background:#1e6fa8;color:#fff;border:none;border-radius:8px;font-size:13px;font-weight:800;cursor:pointer">🖨️ Cetak / Simpan PDF</button></div>' +
    '</body></html>';
  }

  /* ===================================================================
     EXPORT & STORAGE — Huddle 5 Menit
  =================================================================== */

  function exportHuddleCSV() {
    if (huddleLogs.length === 0) { alert('Belum ada sesi huddle yang tersimpan.'); return; }
    var header = ['No Sesi','Shift','Tanggal & Jam','Nama Pasien','No Bed',
      'Perawat Selesai Shift','Perawat Mulai Shift',
      'Skor Perawat Selesai','Skor Perawat Mulai','Selisih',
      'Skor Kesepakatan','Catatan Diskusi','Tindak Lanjut'];
    var shiftLabels = { 'pagi-sore': 'Pagi → Sore', 'sore-malam': 'Sore → Malam', 'malam-pagi': 'Malam → Pagi' };
    var rows = huddleLogs.map(function(e) {
      var wStr = e.waktu ? new Date(e.waktu).toLocaleString('id-ID',{day:'2-digit',month:'short',year:'numeric',hour:'2-digit',minute:'2-digit'}) : '—';
      return [e.sesi, shiftLabels[e.shift]||e.shift, wStr,
        e.pasien, e.bed||'—', e.pwA||'—', e.pwB||'—',
        e.skorA, e.skorB, e.selisih,
        e.skorFinal, e.catatan||'—', e.tindak||'—'].map(csvEsc).join(',');
    });
    var csv = header.map(csvEsc).join(',') + '\n' + rows.join('\n');
    downloadCSV('Log_Huddle_PICU_' + new Date().toISOString().slice(0,10) + '.csv', csv);
  }

  function printHuddle() {
    if (huddleLogs.length === 0) { alert('Belum ada sesi huddle.'); return; }
    var totalSesi  = huddleLogs.length;
    var konsensus  = huddleLogs.filter(function(e){ return e.selisih===0; }).length;
    var diskrepansi= totalSesi - konsensus;
    var avgSelisih = (huddleLogs.reduce(function(s,e){ return s+e.selisih; },0)/totalSesi).toFixed(1);
    var pctKons    = Math.round(konsensus/totalSesi*100);
    var shiftLabels= { 'pagi-sore': '🌅 Pagi → Sore', 'sore-malam': '🌙 Sore → Malam', 'malam-pagi': '🌛 Malam → Pagi' };

    var tableRows = huddleLogs.map(function(e) {
      var wStr = e.waktu ? new Date(e.waktu).toLocaleString('id-ID',{day:'2-digit',month:'short',hour:'2-digit',minute:'2-digit'}) : '—';
      var consColor = e.selisih===0 ? '#27ae60' : '#e07b00';
      var skFColor  = e.skorFinal <= 3 ? '#27ae60' : e.skorFinal <= 6 ? '#e07b00' : '#c0392b';
      return '<tr>' +
        '<td style="padding:6px 8px;border:1px solid #e0e8f0;text-align:center;font-weight:800">'+e.sesi+'</td>' +
        '<td style="padding:6px 8px;border:1px solid #e0e8f0;font-size:11px">'+shiftLabels[e.shift]+'<br><span style="font-size:10px;color:#888">'+wStr+'</span></td>' +
        '<td style="padding:6px 8px;border:1px solid #e0e8f0;font-weight:700">'+e.pasien+(e.bed?' / Bed '+e.bed:'')+'</td>' +
        '<td style="padding:6px 8px;border:1px solid #e0e8f0;text-align:center;font-weight:900;color:#1e6fa8">'+e.skorA+'</td>' +
        '<td style="padding:6px 8px;border:1px solid #e0e8f0;text-align:center;font-weight:900;color:#2e9e6b">'+e.skorB+'</td>' +
        '<td style="padding:6px 8px;border:1px solid #e0e8f0;text-align:center;font-weight:800;color:'+consColor+'">'+e.selisih+'</td>' +
        '<td style="padding:6px 8px;border:1px solid #e0e8f0;text-align:center;font-size:14px;font-weight:900;color:'+skFColor+'">'+e.skorFinal+'</td>' +
        '<td style="padding:6px 8px;border:1px solid #e0e8f0;font-size:11px;color:#555">'+(e.tindak||'—')+'</td>' +
      '</tr>';
    }).join('');

    var html = '<html><head><meta charset="UTF-8"><title>Rekap Huddle PICU</title>' +
    '<style>body{font-family:Arial,sans-serif;margin:0;padding:24px;color:#1a2a3a;font-size:13px}' +
    '@media print{body{padding:12px}.no-print{display:none}}' +
    'table{width:100%;border-collapse:collapse}' +
    '.header-bar{background:linear-gradient(135deg,#1a2a3a,#2e9e6b);color:#fff;border-radius:10px;padding:16px 20px;margin-bottom:16px}' +
    '.stat-grid{display:grid;grid-template-columns:1fr 1fr 1fr 1fr;gap:10px;margin-bottom:16px}' +
    '.stat-box{border-radius:10px;padding:12px;text-align:center;border:1.5px solid}' +
    '</style></head><body>' +
    '<div class="header-bar">' +
      '<div style="font-size:10px;opacity:0.7;letter-spacing:1px;text-transform:uppercase;margin-bottom:4px">RSUP Dr. Hasan Sadikin Bandung — PICU</div>' +
      '<div style="font-size:20px;font-weight:900;margin-bottom:2px">Rekap Log Huddle 5 Menit</div>' +
      '<div style="font-size:11px;opacity:0.85">Validasi Nyeri Antarperawat | Habituasi PICU 2026</div>' +
      '<div style="font-size:11px;opacity:0.75;margin-top:6px">Dicetak: '+new Date().toLocaleString('id-ID')+'</div>' +
    '</div>' +
    '<div class="stat-grid">' +
      '<div class="stat-box" style="background:#f0f4f8;border-color:#dde3ea"><div style="font-size:28px;font-weight:900;color:#1e6fa8">'+totalSesi+'</div><div style="font-size:11px;font-weight:800;color:#6c7a89">Total Sesi</div></div>' +
      '<div class="stat-box" style="background:#e8f5e9;border-color:#27ae60"><div style="font-size:28px;font-weight:900;color:#27ae60">'+konsensus+'</div><div style="font-size:11px;font-weight:800;color:#27ae60">Konsensus</div></div>' +
      '<div class="stat-box" style="background:#fff8e1;border-color:#f39c12"><div style="font-size:28px;font-weight:900;color:#e07b00">'+diskrepansi+'</div><div style="font-size:11px;font-weight:800;color:#e07b00">Diskrepansi</div></div>' +
      '<div class="stat-box" style="background:#eaf3fb;border-color:#1e6fa8"><div style="font-size:28px;font-weight:900;color:#1e6fa8">'+avgSelisih+'</div><div style="font-size:11px;font-weight:800;color:#1e6fa8">Rata Selisih</div></div>' +
    '</div>' +
    '<div style="background:#e8f5e9;border-radius:10px;padding:10px 14px;margin-bottom:14px;display:flex;align-items:center;gap:10px">' +
      '<div style="font-size:22px;font-weight:900;color:#27ae60">'+pctKons+'%</div>' +
      '<div><div style="font-size:13px;font-weight:800;color:#1e8449">Tingkat Konsensus</div>' +
      '<div style="font-size:11px;color:#27ae60">'+(pctKons>=80?'✅ Target tercapai (≥80%)':'⚠️ Target belum tercapai — lanjutkan sesi huddle')+'</div></div>' +
    '</div>' +
    '<table><thead><tr style="background:#f0f4f8">' +
      '<th style="padding:7px 8px;border:1px solid #e0e8f0;font-size:11px;width:40px">#</th>' +
      '<th style="padding:7px 8px;border:1px solid #e0e8f0;font-size:11px">Shift / Waktu</th>' +
      '<th style="padding:7px 8px;border:1px solid #e0e8f0;font-size:11px">Pasien / Bed</th>' +
      '<th style="padding:7px 8px;border:1px solid #e0e8f0;font-size:11px;width:50px;text-align:center">Skor A</th>' +
      '<th style="padding:7px 8px;border:1px solid #e0e8f0;font-size:11px;width:50px;text-align:center">Skor B</th>' +
      '<th style="padding:7px 8px;border:1px solid #e0e8f0;font-size:11px;width:50px;text-align:center">Δ</th>' +
      '<th style="padding:7px 8px;border:1px solid #e0e8f0;font-size:11px;width:55px;text-align:center">Final</th>' +
      '<th style="padding:7px 8px;border:1px solid #e0e8f0;font-size:11px">Tindak Lanjut</th>' +
    '</tr></thead><tbody>'+tableRows+'</tbody></table>' +
    (huddleLogs.some(function(e){return e.catatan;}) ?
      '<div style="margin-top:14px"><div style="font-size:11px;font-weight:800;text-transform:uppercase;color:#6c7a89;margin-bottom:8px">Catatan Diskusi Per Sesi</div>' +
      huddleLogs.filter(function(e){return e.catatan;}).map(function(e){
        return '<div style="background:#f8fafc;border-radius:8px;padding:8px 12px;margin-bottom:6px;border-left:3px solid #1e6fa8">' +
          '<span style="font-size:11px;font-weight:800;color:#1e6fa8">Sesi '+e.sesi+' — '+e.pasien+': </span>' +
          '<span style="font-size:11px;color:#1a2a3a">'+e.catatan+'</span></div>';
      }).join('') + '</div>' : '') +
    '<div style="margin-top:20px;border-top:1px solid #eee;padding-top:12px;display:grid;grid-template-columns:1fr 1fr;gap:20px">' +
      '<div><div style="font-size:11px;color:#6c7a89;margin-bottom:4px">Penanggung Jawab Kegiatan</div><div style="font-weight:800">Asep Rizkika Setia, A.Md.Kep</div><div style="font-size:10px;color:#6c7a89">Perawat Terampil PICU | Habituasi 2026</div><div style="margin-top:28px;font-size:10px;color:#6c7a89">Tanda Tangan: ___________________</div></div>' +
      '<div><div style="font-size:11px;color:#6c7a89;margin-bottom:4px">Mengetahui</div><div style="font-weight:800">Kepala Ruangan / CI PICU</div><div style="margin-top:28px;font-size:10px;color:#6c7a89">Tanda Tangan: ___________________</div></div>' +
    '</div>' +
    '<div class="no-print" style="margin-top:20px;text-align:center"><button onclick="window.print()" style="padding:10px 24px;background:#2e9e6b;color:#fff;border:none;border-radius:8px;font-size:13px;font-weight:800;cursor:pointer">🖨️ Cetak / Simpan PDF</button></div>' +
    '</body></html>';

    _printWindow(html, 'Rekap Huddle PICU');
  }

  /* ===================================================================
     UTILITIES
  =================================================================== */

  function csvEsc(v) {
    var s = (v === null || v === undefined) ? '' : String(v);
    if (s.search(/[",\n\r]/) >= 0) return '"' + s.replace(/"/g,'""') + '"';
    return s;
  }

  function downloadCSV(filename, csv) {
    var bom = '\uFEFF'; // UTF-8 BOM untuk Excel
    var blob = new Blob([bom + csv], { type: 'text/csv;charset=utf-8;' });
    var url  = URL.createObjectURL(blob);
    var a    = document.createElement('a');
    a.href = url; a.download = filename;
    document.body.appendChild(a); a.click();
    document.body.removeChild(a);
    URL.revokeObjectURL(url);
  }

  function _printWindow(html, title) {
    var win = window.open('', '_blank', 'width=800,height=900');
    if (!win) { alert('Aktifkan pop-up untuk mencetak.'); return; }
    win.document.write(html);
    win.document.close();
    win.focus();
    setTimeout(function(){ win.print(); }, 600);
  }

  // saveSummary extended to show export buttons
  var _origSaveSummary = saveSummary;
  saveSummary = function() {
    _origSaveSummary();
    var btn = document.getElementById('export-lembar-btns');
    if (btn) btn.style.display = 'block';
  };

  // tambahSesi extended to save to localStorage and show export
  var _origTambahSesi = tambahSesi;
  tambahSesi = function() {
    _origTambahSesi();
    saveToStorage();
    var btn = document.getElementById('h-export-btns');
    if (btn && huddleLogs.length > 0) btn.style.display = 'block';
  };

  // resetHuddle extended to clear storage
  var _origResetHuddle = resetHuddle;
  resetHuddle = function() {
    _origResetHuddle();
    saveToStorage();
    var btn = document.getElementById('h-export-btns');
    if (btn) btn.style.display = 'none';
  };

  // Load huddle export button visibility
  (function() {
    if (huddleLogs.length > 0) {
      var btn = document.getElementById('h-export-btns');
      if (btn) btn.style.display = 'block';
    }
  })();

</script>
</body>
</html>
