<!DOCTYPE HTML>
<html lang="id">
<head>
  <meta charset="utf-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Voltsketch - Portal Pembelajaran &amp; Simulasi Rangkaian Listrik DC</title>
  
  <!-- FontAwesome & Google Fonts -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap" rel="stylesheet">

  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      font-family: 'Poppins', sans-serif;
      background-color: #f4f7f6;
      color: #333;
      display: flex;
      flex-direction: column;
      min-height: 100vh;
    }

    /* Header Navigasi */
    header {
      background: linear-gradient(135deg, #1e3c72, #2a5298);
      color: white;
      padding: 1rem 2rem;
      display: flex;
      justify-content: space-between;
      align-items: center;
      box-shadow: 0 4px 6px rgba(0,0,0,0.1);
      position: sticky;
      top: 0;
      z-index: 1000;
    }

    .logo {
      font-size: 1.5rem;
      font-weight: 700;
      display: flex;
      align-items: center;
      gap: 10px;
      letter-spacing: 0.5px;
    }

    .logo i {
      color: #ffeb3b;
    }

    nav ul {
      display: flex;
      list-style: none;
      gap: 1rem;
    }

    nav a {
      color: white;
      text-decoration: none;
      font-weight: 500;
      padding: 0.5rem 1rem;
      border-radius: 6px;
      transition: background 0.3s;
      cursor: pointer;
    }

    nav a:hover, nav a.active {
      background-color: rgba(255, 255, 255, 0.2);
    }

    /* Layout Utama */
    main {
      flex: 1;
      display: flex;
      flex-direction: column;
    }

    .page-section {
      display: none;
      width: 100%;
    }

    .page-section.active {
      display: block;
    }

    /* Hero Section Beranda */
    .hero {
      background: linear-gradient(rgba(30, 60, 114, 0.85), rgba(42, 82, 152, 0.85)), url('https://images.unsplash.com/photo-1517077304055-6e89abbf09b0?auto=format&fit=crop&w=1350&q=80');
      background-size: cover;
      background-position: center;
      color: white;
      text-align: center;
      padding: 4rem 1rem;
    }

    .hero h1 {
      font-size: 2.4rem;
      margin-bottom: 0.8rem;
    }

    .hero p {
      font-size: 1.1rem;
      max-width: 650px;
      margin: 0 auto;
      opacity: 0.95;
    }

    /* Cards Grid Beranda */
    .features-container {
      max-width: 1100px;
      margin: 3rem auto;
      padding: 0 1.5rem;
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 2rem;
    }

    .card {
      background: white;
      border-radius: 12px;
      box-shadow: 0 4px 15px rgba(0,0,0,0.06);
      padding: 2.5rem 1.5rem;
      text-align: center;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: space-between;
      transition: transform 0.3s, box-shadow 0.3s;
    }

    .card:hover {
      transform: translateY(-5px);
      box-shadow: 0 8px 25px rgba(0,0,0,0.12);
    }

    .card-icon {
      margin-bottom: 1.2rem;
    }

    .card h3 {
      font-size: 1.3rem;
      margin-bottom: 0.8rem;
      color: #1e3c72;
    }

    .card p {
      color: #666;
      font-size: 0.95rem;
      margin-bottom: 1.8rem;
      line-height: 1.6;
    }

    /* Tombol Kustom */
    .btn {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 8px;
      padding: 0.75rem 1.6rem;
      border-radius: 25px;
      font-weight: 600;
      text-decoration: none;
      border: none;
      cursor: pointer;
      transition: all 0.3s ease;
      font-size: 0.95rem;
      box-shadow: 0 3px 8px rgba(0,0,0,0.12);
    }

    .btn-materi {
      background-color: #007bff;
      color: white;
    }
    .btn-materi:hover {
      background-color: #0056b3;
    }

    .btn-play-blue {
      background-color: #00a8ff;
      color: white;
      width: 58px;
      height: 58px;
      border-radius: 50%;
      padding: 0;
      font-size: 1.3rem;
      box-shadow: 0 4px 12px rgba(0, 168, 255, 0.4);
    }
    .btn-play-blue:hover {
      background-color: #0088cc;
      transform: scale(1.08);
    }

    .btn-simulasi {
      background-color: #28a745;
      color: white;
    }
    .btn-simulasi:hover {
      background-color: #1e7e34;
    }

    /* Style Konten Halaman Materi */
    .materi-container {
      max-width: 950px;
      margin: 2.5rem auto;
      padding: 0 1.5rem;
    }

    .materi-card {
      background: white;
      border-radius: 12px;
      padding: 2.5rem;
      box-shadow: 0 4px 15px rgba(0,0,0,0.05);
      margin-bottom: 2rem;
    }

    .materi-title {
      color: #1e3c72;
      font-size: 1.8rem;
      margin-bottom: 0.5rem;
      border-bottom: 3px solid #007bff;
      padding-bottom: 0.5rem;
      display: inline-block;
    }

    .materi-subtitle {
      color: #555;
      font-size: 1.05rem;
      margin-bottom: 1.5rem;
      font-style: italic;
    }

    .section-title {
      color: #2a5298;
      font-size: 1.3rem;
      margin: 1.8rem 0 1rem 0;
      display: flex;
      align-items: center;
      gap: 8px;
    }

    .tujuan-list {
      background: #eef5ff;
      border-left: 4px solid #007bff;
      padding: 1.2rem 1.5rem;
      border-radius: 0 8px 8px 0;
      margin-bottom: 1.5rem;
    }

    .tujuan-list ul {
      padding-left: 1.2rem;
    }

    .tujuan-list li {
      margin-bottom: 0.5rem;
      line-height: 1.5;
    }

    /* Tabel Komponen */
    .custom-table {
      width: 100%;
      border-collapse: collapse;
      margin: 1rem 0;
      background: white;
    }

    .custom-table th, .custom-table td {
      border: 1px solid #e0e0e0;
      padding: 12px 15px;
      text-align: left;
    }

    .custom-table th {
      background-color: #1e3c72;
      color: white;
    }

    .custom-table tr:nth-child(even) {
      background-color: #f9f9f9;
    }

    /* Box Info & Diagram */
    .info-box {
      background: #f8f9fa;
      border: 1px solid #ddd;
      border-radius: 8px;
      padding: 1.2rem;
      margin: 1rem 0;
    }

    .grid-2col {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
      gap: 1.5rem;
      margin: 1rem 0;
    }

    .flow-card {
      border-radius: 8px;
      padding: 1.2rem;
      text-align: center;
      font-weight: 500;
    }

    .flow-konvensional {
      background-color: #e3f2fd;
      border: 2px solid #2196f3;
      color: #0d47a1;
    }

    .flow-elektron {
      background-color: #ffebee;
      border: 2px solid #ef5350;
      color: #b71c1c;
    }

    .alert-box {
      background-color: #ffebee;
      border: 2px solid #ff1744;
      color: #c62828;
      padding: 1.2rem;
      border-radius: 8px;
      margin: 1.5rem 0;
    }

    .alert-box h4 {
      display: flex;
      align-items: center;
      gap: 8px;
      margin-bottom: 0.5rem;
    }

    /* Halaman Simulator */
    #simulator-section {
      height: calc(100vh - 70px);
      width: 100%;
    }

    iframe {
      width: 100%;
      height: 100%;
      border: none;
    }

    footer {
      background-color: #1e3c72;
      color: white;
      text-align: center;
      padding: 1.2rem;
      font-size: 0.9rem;
    }
  </style>
</head>
<body>

  <!-- Header Navigasi -->
  <header>
    <div class="logo">
      <i class="fa-solid fa-bolt"></i> Voltsketch
    </div>
    <nav>
      <ul>
        <li><a id="nav-beranda" class="active" onclick="switchTab('beranda')">Beranda</a></li>
        <li><a id="nav-materi" onclick="switchTab('materi')">Materi</a></li>
        <li><a id="nav-ritme" onclick="switchTab('ritme')">Belajar Mandiri</a></li>
        <li><a id="nav-simulator" onclick="switchTab('simulator')">Simulator DC</a></li>
      </ul>
    </nav>
  </header>

  <main>
    <!-- 1. BERANDA -->
    <section id="beranda-section" class="page-section active">
      <div class="hero">
        <h1>Selamat Datang di Voltsketch</h1>
        <p>Platform laboratorium visual dan interaktif untuk mempelajari konsep Rangkaian Listrik Arus Searah (DC) dengan mudah.</p>
      </div>

      <div class="features-container">
        <!-- Card 1: Materi -->
        <div class="card">
          <div class="card-icon">
            <i class="fa-solid fa-book-open-reader fa-3x" style="color: #007bff;"></i>
          </div>
          <h3>Akses Materi Lengkap</h3>
          <p>Pelajari komponen, Hukum Ohm, Hukum Kirchhoff, serta skema rangkaian seri-paralel secara komprehensif.</p>
          <button class="btn btn-materi" onclick="switchTab('materi')">
            <i class="fa-solid fa-book"></i> Tombol Materi
          </button>
        </div>

        <!-- Card 2: Ritme Belajar -->
        <div class="card">
          <div class="card-icon">
            <i class="fa-solid fa-clock-rotate-left fa-3x" style="color: #00a8ff;"></i>
          </div>
          <h3>Belajar Sesuai Ritme</h3>
          <p>Atur kecepatan eksplorasi dan pemahaman mandiri Anda melalui modul panduan berbasis eksperimen visual.</p>
          <button class="btn btn-play-blue" title="Mulai Belajar Mandiri" onclick="switchTab('ritme')">
            <i class="fa-solid fa-play"></i>
          </button>
        </div>

        <!-- Card 3: Simulasi -->
        <div class="card">
          <div class="card-icon">
            <i class="fa-solid fa-microchip fa-3x" style="color: #28a745;"></i>
          </div>
          <h3>Simulasi Interaktif</h3>
          <p>Rakit sirkuit listrik DC secara praktis dan aman di dalam simulator virtual interactive real-time.</p>
          <button class="btn btn-simulasi" onclick="switchTab('simulator')">
            <i class="fa-solid fa-flask"></i> Tombol Simulasi
          </button>
        </div>
      </div>
    </section>

    <!-- 2. MATERI (Diintegrasikan dari Dokumen Rangkaian Listrik Arus Searah DC Visual) -->
    <section id="materi-section" class="page-section">
      <div class="materi-container">
        <div class="materi-card">
          <h1 class="materi-title">RANGKAIAN LISTRIK ARUS SEARAH (DC)</h1>
          <p class="materi-subtitle">Panduan Interaktif &amp; Visual untuk Eksperimen Simulasi Virtual Fisika Dasar</p>

          <!-- Tujuan Pembelajaran -->
          <div class="tujuan-list">
            <h3><i class="fa-solid fa-bullseye" style="color: #007bff;"></i> TUJUAN PEMBELAJARAN</h3>
            <ul style="margin-top: 0.8rem;">
              <li>Mengidentifikasi komponen-komponen dasar rangkaian listrik DC beserta fungsinya (Baterai, Kabel, Resistor, Lampu, Saklar).</li>
              <li>Membedakan antara arus elektron dan arus konvensional serta arah aliran keduanya yang sebenarnya.</li>
              <li>Membuktikan Hukum Ohm secara empiris dengan mengamati perubahan arus ketika tegangan atau hambatan diubah.</li>
              <li>Menghitung tegangan dan arus pada Rangkaian Seri dan Rangkaian Paralel.</li>
              <li>Menerapkan Hukum Kirchhoff dengan menghitung tegangan dan arus pada titik-titik tertentu menggunakan Voltmeter.</li>
              <li>Menganalisis fenomena kelistrikan sehari-hari, seperti kecerahan lampu dan bahaya korsleting (short circuit).</li>
            </ul>
          </div>

          <!-- A. Komponen Dasar -->
          <h2 class="section-title"><i class="fa-solid fa-cubes"></i> A. Komponen Dasar Rangkaian Listrik</h2>
          <p>Di dalam simulasi virtual, terdapat beberapa komponen utama yang memegang peranan penting:</p>
          
          <table class="custom-table">
            <thead>
              <tr>
                <th>Komponen</th>
                <th>Fungsi Utama</th>
                <th>Karakteristik dalam Simulasi</th>
              </tr>
            </thead>
            <tbody>
              <tr>
                <td><strong>Baterai</strong></td>
                <td>Sumber energi listrik yang 'memompa' muatan elektron.</td>
                <td>Memiliki kutub positif (+) dan negatif (-). Beda potensial menentukan daya dorong.</td>
              </tr>
              <tr>
                <td><strong>Kabel</strong></td>
                <td>Jalur penghantar muatan dari satu titik ke titik lain.</td>
                <td>Dalam teori ideal, hambatan kabel dianggap nol (R = 0).</td>
              </tr>
              <tr>
                <td><strong>Resistor</strong></td>
                <td>Komponen penahan/penghambat arus listrik.</td>
                <td>Semakin besar nilai resistansi, semakin kecil arus listrik yang mengalir.</td>
              </tr>
              <tr>
                <td><strong>Lampu</strong></td>
                <td>Mengubah energi listrik menjadi energi cahaya &amp; panas.</td>
                <td>Memiliki hambatan dalam. Kecerahannya menggambarkan besarnya daya listrik.</td>
              </tr>
              <tr>
                <td><strong>Saklar</strong></td>
                <td>Penyambung atau pemutus aliran arus listrik.</td>
                <td>Tertutup = Rangkaian terhubung (ON), Terbuka = Rangkaian terputus (OFF).</td>
              </tr>
            </tbody>
          </table>

          <!-- B. Besaran Pokok -->
          <h2 class="section-title"><i class="fa-solid fa-sliders"></i> B. Besaran Pokok Kelistrikan</h2>
          <div class="info-box">
            <ul>
              <li><strong>Tegangan (Beda Potensial) [V]:</strong> Energi yang dibutuhkan untuk memindahkan muatan listrik. Diukur dalam Volt (V) menggunakan Voltmeter yang dipasang secara paralel.</li>
              <li style="margin-top: 0.5rem;"><strong>Arus Listrik [I]:</strong> Banyaknya muatan listrik yang mengalir tiap satuan waktu. Diukur dalam Ampere (A) menggunakan Amperemeter yang dipasang secara seri.</li>
              <li style="margin-top: 0.5rem;"><strong>Hambatan (Resistansi) [R]:</strong> Sifat bahan yang menghambat arus listrik. Diukur dalam satuan Ohm (&Omega;).</li>
            </ul>
          </div>

          <!-- C. Arah Aliran Arus -->
          <h2 class="section-title"><i class="fa-solid fa-arrows-left-right"></i> C. Arah Aliran Arus Listrik</h2>
          <p>Dalam fisika, terdapat dua konsep arah aliran yang berbeda namun saling berkaitan:</p>
          <div class="grid-2col">
            <div class="flow-card flow-konvensional">
              <h4>ARUS KONVENSIONAL</h4>
              <p style="font-size: 0.85rem; margin: 4px 0;">(Teori Standar)</p>
              <strong>Kutub (+) &rarr; Kutub (-)</strong>
            </div>
            <div class="flow-card flow-elektron">
              <h4>ALIRAN ELEKTRON</h4>
              <p style="font-size: 0.85rem; margin: 4px 0;">(Realita Fisika)</p>
              <strong>Kutub (-) &rarr; Kutub (+)</strong>
            </div>
          </div>

          <!-- D. Hukum-Hukum Dasar -->
          <h2 class="section-title"><i class="fa-solid fa-square-root-variable"></i> D. Hukum-Hukum Dasar Kelistrikan</h2>
          
          <h3 style="color: #1e3c72; margin-top: 1rem;">1. Hukum Ohm</h3>
          <p>Hukum Ohm menyatakan bahwa arus listrik (I) berbanding lurus dengan tegangan (V) dan berbanding terbalik dengan hambatan (R).</p>
          <div class="info-box" style="text-align: center; font-size: 1.2rem; font-weight: 600; color: #007bff;">
            V = I &times; R &nbsp;|&nbsp; I = V / R &nbsp;|&nbsp; R = V / I
          </div>

          <h3 style="color: #1e3c72; margin-top: 1.2rem;">2. Hukum Kirchhoff I &amp; II</h3>
          <div class="info-box">
            <p><strong>&bull; Hukum Kirchhoff I (Arus / Titik Cabang):</strong> Jumlah arus listrik yang masuk ke suatu titik percabangan sama dengan jumlah arus yang keluar.<br>
            <em>Rumus: &sum; I_masuk = &sum; I_keluar</em></p>
            <hr style="margin: 0.8rem 0; border: 0; border-top: 1px dashed #ccc;">
            <p><strong>&bull; Hukum Kirchhoff II (Tegangan / Loop Tertutup):</strong> Jumlah aljabar perubahan potensial (tegangan) dalam satu loop tertutup adalah nol.<br>
            <em>Rumus: &sum; V = 0</em></p>
          </div>

          <!-- E. Jenis Rangkaian Listrik -->
          <h2 class="section-title"><i class="fa-solid fa-diagram-project"></i> E. Jenis Rangkaian Listrik</h2>
          <div class="grid-2col">
            <div class="info-box">
              <h3 style="color: #1e3c72; border-bottom: 2px solid #1e3c72; padding-bottom: 5px;">Rangkaian Seri</h3>
              <p style="margin-top: 8px;"><em>(Arus Sama, Tegangan Terbagi)</em></p>
              <ul style="margin-top: 8px; padding-left: 1.2rem;">
                <li>I<sub>total</sub> = I<sub>1</sub> = I<sub>2</sub></li>
                <li>V<sub>total</sub> = V<sub>1</sub> + V<sub>2</sub></li>
                <li>R<sub>total</sub> = R<sub>1</sub> + R<sub>2</sub></li>
              </ul>
            </div>
            <div class="info-box">
              <h3 style="color: #1e3c72; border-bottom: 2px solid #1e3c72; padding-bottom: 5px;">Rangkaian Paralel</h3>
              <p style="margin-top: 8px;"><em>(Tegangan Sama, Arus Terbagi)</em></p>
              <ul style="margin-top: 8px; padding-left: 1.2rem;">
                <li>I<sub>total</sub> = I<sub>1</sub> + I<sub>2</sub></li>
                <li>V<sub>total</sub> = V<sub>1</sub> = V<sub>2</sub></li>
                <li>1/R<sub>total</sub> = 1/R<sub>1</sub> + 1/R<sub>2</sub></li>
              </ul>
            </div>
          </div>

          <!-- F. Fenomena Kelistrikan -->
          <h2 class="section-title"><i class="fa-solid fa-bolt-lightning"></i> F. Fenomena Kelistrikan Tambahan</h2>
          <p><strong>1. Daya Listrik (P):</strong> Laju perpindahan energi listrik. Pada lampu, daya menentukan kecerahan nyalanya.<br>
          <em>Rumus: P = V &times; I &nbsp;atau&nbsp; P = I&sup2; &times; R &nbsp;(Satuan: Watt / W)</em></p>

          <div class="alert-box">
            <h4><i class="fa-solid fa-triangle-exclamation"></i> 2. Korsleting (Short Circuit)</h4>
            <p>Kondisi ketika arus mengalir langsung dari kutub (+) ke (-) Baterai tanpa hambatan (R = 0), menyebabkan melonjaknya arus secara ekstrem &rarr; <strong>Risiko Panas Tinggi, Kerusakan Alat &amp; Kebakaran!</strong></p>
          </div>
        </div>
      </div>
    </section>

    <!-- 3. RITME / BELAJAR MANDIRI -->
    <section id="ritme-section" class="page-section">
      <div class="materi-container">
        <div class="materi-card">
          <h2 style="color: #1e3c72; margin-bottom: 1rem;"><i class="fa-solid fa-clock-rotate-left"></i> Modul Belajar Mandiri</h2>
          <hr style="margin-bottom: 1.5rem; border: 0; border-top: 1px solid #eee;">
          <p>Ikuti latihan interaktif step-by-step dan panduan praktik mandiri untuk memperdalam pemahaman materi listrik DC di Voltsketch.</p>
        </div>
      </div>
    </section>

    <!-- 4. SIMULATOR (PhET Kit Rangkaian DC) -->
    <section id="simulator-section" class="page-section">
      <iframe src="https://phet.colorado.edu/sims/html/circuit-construction-kit-dc/latest/circuit-construction-kit-dc_all.html?locale=id" title="Simulasi Rangkaian Listrik DC PhET" allowfullscreen></iframe>
    </section>
  </main>

  <footer>
    <p>&copy; 2026 Voltsketch | Media Pembelajaran Listrik DC Virtual</p>
  </footer>

  <script>
    // Tab Switching Logic
    function switchTab(tabName) {
      const sections = document.querySelectorAll('.page-section');
      sections.forEach(sec => sec.classList.remove('active'));

      const navLinks = document.querySelectorAll('nav a');
      navLinks.forEach(link => link.classList.remove('active'));

      document.getElementById(tabName + '-section').classList.add('active');
      document.getElementById('nav-' + tabName).classList.add('active');

      window.scrollTo({ top: 0, behavior: 'smooth' });
    }
  </script>
</body>
</html>
