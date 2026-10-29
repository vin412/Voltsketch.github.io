<!doctype html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>VOLTSKETCH — Belajar Kelistrikan</title>
  <link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600;700&family=Fraunces:opsz,wght@9..144,600;9..144,700&display=swap" rel="stylesheet">
  <script src="https://cdn.tailwindcss.com/3.4.17"></script>
  <style>
    :root { --navy:#102b3a; --cream:#f5f3e9; --yellow:#f4c84b; --ink:#17313c; --muted:#52636a; }
    * { box-sizing: border-box; }
    body { font-family: "DM Sans", sans-serif; color: var(--ink); margin: 0; background: var(--cream); }
    h1, h2, h3 { font-family: "Fraunces", serif; }
    
    /* Pengaturan Multi-Halaman (SPA) */
    .page { display: none; min-height: calc(100vh - 120px); }
    .page.active { display: block; }
    
    .hero { background-color: var(--navy); background-image: radial-gradient(circle at 80% 20%, #335460 0, transparent 38%), radial-gradient(circle at 10% 90%, #1b4854 0, transparent 35%); }
    .eyebrow { letter-spacing: .16em; text-transform: uppercase; }
    .circuit { position: relative; width: min(100%, 280px); aspect-ratio: 1; margin: auto; border: 2px solid rgba(244, 200, 75, .66); border-radius: 32px; transform: rotate(-7deg); }
    .circuit:before, .circuit:after { content: ""; position: absolute; background: var(--yellow); box-shadow: 0 0 25px rgba(244, 200, 75, .45); }
    .circuit:before { width: 28px; height: 28px; border-radius: 50%; top: -15px; left: 19%; }
    .circuit:after { width: 18px; height: 18px; border-radius: 50%; bottom: -10px; right: 21%; }
    .bulb { position: absolute; inset: 22%; border-radius: 50%; display: grid; place-items: center; background: radial-gradient(circle, #ffeaa0 0, #f4c84b 42%, #b18e32 78%); box-shadow: 0 0 65px #f4c84b88; font-size: 60px; transform: rotate(7deg); }
    .card { border: 1px solid #dbe1db; transition: transform .2s, box-shadow .2s; }
    .card:hover { transform: translateY(-3px); box-shadow: 0 14px 32px #17313c14; }
    .nav-btn { cursor: pointer; transition: all 0.2s; }
    .step { display: none; } 
    .step.active { display: block; }
    [hidden] { display: none !important; }

    /* Efek Menarik untuk Banner Simulasi */
    .sim-banner {
      background: linear-gradient(135deg, #102b3a 0%, #1e4c5a 100%);
      box-shadow: 0 10px 30px rgba(16, 43, 58, 0.25);
      transition: all 0.3s ease;
    }
    .sim-banner:hover {
      transform: translateY(-4px);
      box-shadow: 0 15px 35px rgba(244, 200, 75, 0.3);
    }
  </style>
</head>
<body class="w-full min-h-screen flex flex-col justify-between">

  <!-- HEADER GLOBAL -->
  <header class="w-full bg-[#f5f3e9] border-b border-[#dbe1db] sticky top-0 z-50">
    <div class="max-w-6xl mx-auto px-5 py-4 flex flex-wrap items-center justify-between gap-4">
      <button onclick="navigateTo('hal1')" class="font-bold text-[#102b3a] text-xl tracking-tight flex items-center gap-2">
        ⚡ VOLTSKETCH
      </button>
      <nav class="flex flex-wrap gap-x-6 gap-y-2 text-sm font-semibold">
        <button onclick="navigateTo('hal1')" class="nav-btn text-[#102b3a] hover:underline">Beranda</button>
        <button onclick="navigateTo('hal2')" class="nav-btn text-[#102b3a] hover:underline">Materi</button>
        <button onclick="navigateTo('hal3')" class="nav-btn text-[#102b3a] hover:underline">Video</button>
        <button onclick="navigateTo('hal4')" class="nav-btn text-[#102b3a] hover:underline">Simulasi</button>
        <button onclick="navigateTo('hal5')" class="nav-btn text-[#102b3a] hover:underline">Tanya Asisten</button>
      </nav>
    </div>
  </header>

  <main class="flex-grow">
    
    <!-- HALAMAN 1 / BERANDA -->
    <div id="hal1" class="page active">
      <section class="hero w-full text-white overflow-hidden py-12 md:py-16">
        <div class="max-w-6xl mx-auto px-5 grid md:grid-cols-2 items-center gap-10">
          <div>
            <p class="eyebrow text-[#f4c84b] font-bold text-sm mb-4">LAB BELAJAR KELISTRIKAN</p>
            <h1 class="font-bold leading-tight mb-6 text-3xl md:text-4xl">Nyalakan rasa ingin tahumu tentang listrik.</h1>
            <p class="text-[#dbe7e6] leading-relaxed max-w-xl mb-8">Pelajari konsepnya, temukan inspirasi video, lalu coba rangkaian virtual selangkah demi selangkah. Pilih menu pembelajaran di bawah untuk memulai.</p>
          </div>
          <div class="py-4" aria-hidden="true">
            <div class="circuit">
              <div class="bulb">⚡</div>
            </div>
          </div>
        </div>
      </section>

      <!-- MENU PADA HALAMAN 1 -->
      <section class="max-w-6xl mx-auto px-5 py-16">
        <h2 class="font-bold text-2xl text-[#102b3a] mb-8 text-center">Pilih Menu Pembelajaran</h2>
        <div class="grid sm:grid-cols-2 lg:grid-cols-4 gap-6">
          
          <div onclick="navigateTo('hal2')" class="card bg-white rounded-2xl p-6 cursor-pointer text-center hover:border-[#f4c84b]">
            <div class="text-4xl mb-4">📖</div>
            <h3 class="font-bold text-xl mb-2 text-[#102b3a]">Materi</h3>
            <p class="text-[#52636a] text-sm mb-4">Pahami konsep dasar arus, tegangan, hingga Hukum Ohm.</p>
            <button class="bg-[#102b3a] text-white px-4 py-2 rounded-full text-sm font-bold w-full">Buka Materi →</button>
          </div>

          <div onclick="navigateTo('hal3')" class="card bg-white rounded-2xl p-6 cursor-pointer text-center hover:border-[#f4c84b]">
            <div class="text-4xl mb-4">🎬</div>
            <h3 class="font-bold text-xl mb-2 text-[#102b3a]">Video</h3>
            <p class="text-[#52636a] text-sm mb-4">Temukan rekomendasi video animasi dan tutorial fisika.</p>
            <button class="bg-[#102b3a] text-white px-4 py-2 rounded-full text-sm font-bold w-full">Tonton Video →</button>
          </div>

          <div onclick="navigateTo('hal4')" class="card bg-white rounded-2xl p-6 cursor-pointer text-center hover:border-[#f4c84b]">
            <div class="text-4xl mb-4">⚡</div>
            <h3 class="font-bold text-xl mb-2 text-[#102b3a]">Simulasi</h3>
            <p class="text-[#52636a] text-sm mb-4">Coba praktikum virtual merangkai listrik & Kalkulator.</p>
            <button class="bg-[#102b3a] text-white px-4 py-2 rounded-full text-sm font-bold w-full">Coba Simulasi →</button>
          </div>

          <div onclick="navigateTo('hal5')" class="card bg-white rounded-2xl p-6 cursor-pointer text-center hover:border-[#f4c84b]">
            <div class="text-4xl mb-4">🤖</div>
            <h3 class="font-bold text-xl mb-2 text-[#102b3a]">Tanya Asisten</h3>
            <p class="text-[#52636a] text-sm mb-4">Ajukan pertanyaan seputar kelistrikan ke Asisten VOLTSKETCH.</p>
            <button class="bg-[#102b3a] text-white px-4 py-2 rounded-full text-sm font-bold w-full">Tanya Asisten →</button>
          </div>

        </div>
      </section>
    </div>

    <!-- HALAMAN 2 / MATERI -->
    <div id="hal2" class="page">
      <section class="max-w-6xl mx-auto px-5 py-12">
        <div class="flex justify-between items-center mb-8 border-b pb-4 border-[#dbe1db]">
          <div>
            <p class="eyebrow text-[#ae7521] font-bold text-sm mb-1">HALAMAN 2 / MATERI</p>
            <h2 class="font-bold text-2xl text-[#102b3a]">Materi Kelistrikan</h2>
          </div>
          <button onclick="navigateTo('hal1')" class="bg-[#f4c84b] text-[#102b3a] px-5 py-2 rounded-full font-bold hover:brightness-95">🏠 Home / Beranda</button>
        </div>

        <div class="grid sm:grid-cols-2 lg:grid-cols-3 gap-5">
          <article class="card bg-white rounded-2xl p-6">
            <span class="text-3xl">〰️</span>
            <h3 class="font-bold mt-4 mb-2 text-lg">Arus Listrik</h3>
            <p class="text-[#52636a] mb-4 text-sm">Aliran muatan listrik dalam suatu rangkaian.</p>
            <button type="button" class="font-bold text-[#126276] underline text-sm" data-toggle="detail-arus">Lihat penjelasan</button>
            <p id="detail-arus" class="mt-4 pt-4 border-t text-sm leading-relaxed" hidden>Bayangkan air mengalir melalui pipa: arus menggambarkan banyaknya muatan yang lewat setiap detik. Satuannya ampere (A).</p>
          </article>

          <article class="card bg-white rounded-2xl p-6">
            <span class="text-3xl">🔋</span>
            <h3 class="font-bold mt-4 mb-2 text-lg">Tegangan</h3>
            <p class="text-[#52636a] mb-4 text-sm">Dorongan yang memungkinkan muatan bergerak.</p>
            <button type="button" class="font-bold text-[#126276] underline text-sm" data-toggle="detail-tegangan">Lihat penjelasan</button>
            <p id="detail-tegangan" class="mt-4 pt-4 border-t text-sm leading-relaxed" hidden>Tegangan adalah beda potensial antara dua titik. Satuannya volt (V).</p>
          </article>

          <article class="card bg-white rounded-2xl p-6">
            <span class="text-3xl">🧱</span>
            <h3 class="font-bold mt-4 mb-2 text-lg">Hambatan</h3>
            <p class="text-[#52636a] mb-4 text-sm">Ukuran seberapa sulit arus mengalir.</p>
            <button type="button" class="font-bold text-[#126276] underline text-sm" data-toggle="detail-hambatan">Lihat penjelasan</button>
            <p id="detail-hambatan" class="mt-4 pt-4 border-t text-sm leading-relaxed" hidden>Hambatan membatasi arus. Resistor adalah komponen penyedia hambatan. Satuannya ohm (Ω).</p>
          </article>
        </div>
      </section>
    </div>

    <!-- HALAMAN 3 / VIDEO -->
    <div id="hal3" class="page">
      <section class="max-w-6xl mx-auto px-5 py-12">
        <div class="flex justify-between items-center mb-8 border-b pb-4 border-[#dbe1db]">
          <div>
            <p class="eyebrow text-[#ae7521] font-bold text-sm mb-1">HALAMAN 3 / VIDEO</p>
            <h2 class="font-bold text-2xl text-[#102b3a]">Rekomendasi Video</h2>
          </div>
          <button onclick="navigateTo('hal1')" class="bg-[#f4c84b] text-[#102b3a] px-5 py-2 rounded-full font-bold hover:brightness-95">🏠 Home / Beranda</button>
        </div>

        <div class="grid md:grid-cols-3 gap-6">
          <article class="bg-white rounded-2xl p-6 card">
            <span class="text-3xl">▶</span>
            <h3 class="font-bold mt-4 mb-2 text-lg">Arus, Tegangan & Hambatan</h3>
            <a class="text-[#126276] font-bold underline text-sm" href="https://www.youtube.com/results?search_query=arus+tegangan+hambatan+fisika+dasar" target="_blank">Cari video di YouTube ↗</a>
          </article>
          <article class="bg-white rounded-2xl p-6 card">
            <span class="text-3xl">▶</span>
            <h3 class="font-bold mt-4 mb-2 text-lg">Hukum Ohm & Contoh Soal</h3>
            <a class="text-[#126276] font-bold underline text-sm" href="https://www.youtube.com/results?search_query=hukum+ohm+contoh+soal+fisika" target="_blank">Cari video di YouTube ↗</a>
          </article>
        </div>
      </section>
    </div>

    <!-- HALAMAN 4 / SIMULASI & MERANGKAI LISTRIK -->
    <div id="hal4" class="page">
      <section class="max-w-6xl mx-auto px-5 py-12">
        <div class="flex justify-between items-center mb-8 border-b pb-4 border-[#dbe1db]">
          <div>
            <p class="eyebrow text-[#ae7521] font-bold text-sm mb-1">HALAMAN 4 / SIMULASI</p>
            <h2 class="font-bold text-2xl text-[#102b3a]">Simulasi & Kalkulator</h2>
          </div>
          <button onclick="navigateTo('hal1')" class="bg-[#f4c84b] text-[#102b3a] px-5 py-2 rounded-full font-bold hover:brightness-95">🏠 Home / Beranda</button>
        </div>

        <!-- TOMBOL / BANNER UTAMA MERANGKAI LISTRIK YANG BESAR & MENARIK -->
        <div class="mb-8">
          <a href="https://phet.colorado.edu/id/simulations/circuit-construction-kit-dc" target="_blank" rel="noopener noreferrer" 
             class="sim-banner block rounded-3xl p-8 md:p-10 text-white border-2 border-[#f4c84b] relative overflow-hidden group">
            <div class="absolute -right-6 -bottom-6 text-9xl opacity-15 select-none group-hover:scale-110 transition-transform">💡</div>
            <div class="relative z-10 max-w-2xl">
              <span class="bg-[#f4c84b] text-[#102b3a] font-bold text-xs px-3 py-1 rounded-full uppercase tracking-wider">Praktikum Interaktif</span>
              <h3 class="font-bold text-2xl md:text-3xl mt-3 mb-2 flex items-center gap-3">
                <span>⚡ Simulasi Merangkai Listrik Virtual</span>
              </h3>
              <p class="text-[#dbe7e6] text-sm md:text-base leading-relaxed mb-6">
                Klik di sini untuk langsung merangkai baterai, kabel, lampu, dan sakelar secara interaktif di lab virtual! Uji coba rangkaian seri dan paralel langsung di browser kamu.
              </p>
              <span class="inline-flex items-center gap-2 bg-[#f4c84b] text-[#102b3a] font-bold px-6 py-3 rounded-full text-sm group-hover:bg-white transition-colors">
                Mulai Merangkai Sekarang ↗
              </span>
            </div>
          </a>
        </div>

        <div class="grid lg:grid-cols-2 gap-6">
          <!-- Panduan Langkah Praktikum -->
          <div class="bg-[#102b3a] text-white rounded-3xl p-6 md:p-8 shadow-md">
            <p class="eyebrow text-[#f4c84b] font-bold text-xs">PANDUAN PRAKTIK MERANGKAI</p>
            <p id="step-counter" class="text-xs text-[#c2d7d8] mt-2" aria-live="polite">Langkah 1 dari 4</p>
            
            <div class="min-h-36 mt-4">
              <div class="step active" data-step="0">
                <h3 class="font-bold mb-2 text-lg">1. Siapkan ruang eksperimen</h3>
                <p class="leading-relaxed text-sm text-[#dbe7e6]">Buka simulasi di atas, pilih menu lab/rangkaian, lalu kenali komponen baterai, kabel, dan lampu.</p>
              </div>
              <div class="step" data-step="1">
                <h3 class="font-bold mb-2 text-lg">2. Bangun lintasan tertutup</h3>
                <p class="leading-relaxed text-sm text-[#dbe7e6]">Tarik satu baterai dan satu lampu ke area kerja. Hubungkan dengan kabel hingga membentuk lingkaran.</p>
              </div>
              <div class="step" data-step="2">
                <h3 class="font-bold mb-2 text-lg">3. Uji rangkaian seri</h3>
                <p class="leading-relaxed text-sm text-[#dbe7e6]">Tambahkan lampu kedua pada jalur yang sama. Amati perubahan nyala lampunya.</p>
              </div>
              <div class="step" data-step="3">
                <h3 class="font-bold mb-2 text-lg">4. Bandingkan dengan paralel</h3>
                <p class="leading-relaxed text-sm text-[#dbe7e6]">Buat dua cabang jalur terpisah, masing-masing berisi satu lampu dan bandingkan hasilnya.</p>
              </div>
            </div>

            <div class="flex flex-wrap gap-3 mt-4">
              <button id="prev-step" type="button" disabled class="rounded-full border border-white/50 px-4 py-1.5 text-sm disabled:opacity-40">← Sebelumnya</button>
              <button id="next-step" type="button" class="rounded-full bg-[#f4c84b] text-[#102b3a] font-bold px-4 py-1.5 text-sm">Berikutnya →</button>
            </div>
          </div>

          <!-- Kalkulator Hukum Ohm -->
          <div class="bg-white border border-[#dbe1db] rounded-3xl p-6 md:p-8">
            <h3 class="font-bold mb-2 text-lg text-[#102b3a]">Kalkulator Hukum Ohm</h3>
            <p class="text-[#52636a] text-sm mb-6">Masukkan tegangan dan hambatan untuk mencari besar arus (I = V ÷ R).</p>
            <form id="ohm-form" class="space-y-4">
              <div>
                <label for="voltage" class="block font-semibold text-sm mb-1">Tegangan (V)</label>
                <input id="voltage" class="w-full rounded-xl border border-[#9baead] px-4 py-2.5 text-sm" type="number" min="0" step="any" required placeholder="Contoh: 12">
              </div>
              <div>
                <label for="resistance" class="block font-semibold text-sm mb-1">Hambatan (Ω)</label>
                <input id="resistance" class="w-full rounded-xl border border-[#9baead] px-4 py-2.5 text-sm" type="number" min="0.000001" step="any" required placeholder="Contoh: 4">
              </div>
              <button type="submit" class="rounded-full bg-[#f4c84b] text-[#102b3a] font-bold px-6 py-2.5 text-sm hover:brightness-95">Hitung Arus</button>
            </form>
            <p id="ohm-result" role="status" aria-live="polite" class="mt-4 font-bold text-[#126276] text-sm min-h-6"></p>
          </div>
        </div>
      </section>
    </div>

    <!-- HALAMAN 5 / TANYA ASISTEN -->
    <div id="hal5" class="page">
      <section class="max-w-4xl mx-auto px-5 py-12">
        <div class="flex justify-between items-center mb-8 border-b pb-4 border-[#dbe1db]">
          <div>
            <p class="eyebrow text-[#ae7521] font-bold text-sm mb-1">HALAMAN 5 / TANYA ASISTEN</p>
            <h2 class="font-bold text-2xl text-[#102b3a]">Tanya Asisten VOLTSKETCH</h2>
          </div>
          <button onclick="navigateTo('hal1')" class="bg-[#f4c84b] text-[#102b3a] px-5 py-2 rounded-full font-bold hover:brightness-95">🏠 Home / Beranda</button>
        </div>

        <div class="bg-white rounded-3xl p-6 shadow-sm">
          <form id="question-form">
            <div class="flex gap-3">
              <input id="question" type="text" required class="flex-1 rounded-xl border px-4 py-2 text-sm" placeholder="Misal: apa itu Hukum Ohm?">
              <button type="submit" class="rounded-xl bg-[#102b3a] text-white font-bold px-6 py-2 text-sm">Tanyakan</button>
            </div>
          </form>
          <div id="answer-box" class="mt-6 rounded-xl bg-[#f5f3e9] p-5">
            <p id="answer-content" class="text-sm text-[#102b3a]">Jawaban akan muncul di sini.</p>
          </div>
        </div>
      </section>
    </div>

  </main>

  <!-- FOOTER GLOBAL -->
  <footer class="bg-[#102b3a] text-[#dbe7e6] w-full py-6 mt-12">
    <div class="max-w-6xl mx-auto px-5 text-center text-sm">
      ⚡ VOLTSKETCH · Belajar, mencoba, dan memahami listrik selangkah demi selangkah.
    </div>
  </footer>

  <script>
    // Fungsi Pindah Halaman
    function navigateTo(pageId) {
      document.querySelectorAll('.page').forEach(page => page.classList.remove('active'));
      const targetPage = document.getElementById(pageId);
      if (targetPage) {
        targetPage.classList.add('active');
        window.scrollTo({ top: 0, behavior: 'smooth' });
      }
    }

    // Toggle Detail Penjelasan
    document.querySelectorAll('[data-toggle]').forEach(button => {
      button.addEventListener('click', () => {
        const detail = document.getElementById(button.dataset.toggle);
        detail.hidden = !detail.hidden;
      });
    });

    // Step Simulator
    const steps = [...document.querySelectorAll('.step')];
    let currentStep = 0;
    function showStep(index) {
      steps[currentStep].classList.remove('active');
      currentStep = index;
      steps[currentStep].classList.add('active');
      document.getElementById('step-counter').textContent = `Langkah ${currentStep + 1} dari ${steps.length}`;
      document.getElementById('prev-step').disabled = currentStep === 0;
      document.getElementById('next-step').disabled = currentStep === steps.length - 1;
    }
    document.getElementById('prev-step').addEventListener('click', () => { if (currentStep > 0) showStep(currentStep - 1); });
    document.getElementById('next-step').addEventListener('click', () => { if (currentStep < steps.length - 1) showStep(currentStep + 1); });

    // Kalkulator Ohm
    document.getElementById('ohm-form').addEventListener('submit', event => {
      event.preventDefault();
      const voltage = Number(document.getElementById('voltage').value);
      const resistance = Number(document.getElementById('resistance').value);
      const output = document.getElementById('ohm-result');
      if (voltage >= 0 && resistance > 0) {
        output.textContent = `Arus (I) =
