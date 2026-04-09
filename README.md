<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>For Angel</title>
  <style>
    :root {
      --bg: #050505;
      --panel: rgba(255,255,255,0.06);
      --panel-strong: rgba(255,255,255,0.1);
      --text: #f5f5f5;
      --muted: #bdbdbd;
      --line: rgba(255,255,255,0.12);
      --accent: #ffffff;
      --shadow: 0 20px 50px rgba(0,0,0,0.45);
      --radius: 24px;
    }

    * { box-sizing: border-box; }
    html { scroll-behavior: smooth; }
    body {
      margin: 0;
      font-family: Inter, Arial, Helvetica, sans-serif;
      background:
        radial-gradient(circle at top right, rgba(255,255,255,0.08), transparent 20%),
        radial-gradient(circle at bottom left, rgba(255,255,255,0.06), transparent 24%),
        var(--bg);
      color: var(--text);
      min-height: 100vh;
      overflow-x: hidden;
    }

    .noise {
      position: fixed;
      inset: 0;
      pointer-events: none;
      opacity: 0.04;
      background-image: radial-gradient(#fff 0.5px, transparent 0.5px);
      background-size: 14px 14px;
      mix-blend-mode: soft-light;
    }

    .container {
      width: min(1100px, calc(100% - 32px));
      margin: 0 auto;
    }

    .hero {
      min-height: 100vh;
      display: flex;
      align-items: center;
      position: relative;
      padding: 40px 0;
    }

    .hero-grid {
      display: grid;
      grid-template-columns: 1.2fr 0.8fr;
      gap: 28px;
      align-items: stretch;
      width: 100%;
    }

    .card {
      background: var(--panel);
      border: 1px solid var(--line);
      border-radius: var(--radius);
      box-shadow: var(--shadow);
      backdrop-filter: blur(10px);
    }

    .hero-main {
      padding: 42px;
      display: flex;
      flex-direction: column;
      justify-content: center;
    }

    .eyebrow {
      letter-spacing: 0.18em;
      text-transform: uppercase;
      font-size: 12px;
      color: var(--muted);
      margin-bottom: 16px;
    }

    h1 {
      margin: 0;
      font-size: clamp(42px, 7vw, 84px);
      line-height: 0.95;
      letter-spacing: -0.04em;
    }

    .typing-wrap {
      margin-top: 20px;
      min-height: 80px;
    }

    .typing {
      font-size: clamp(18px, 2.2vw, 24px);
      line-height: 1.6;
      color: #ececec;
      max-width: 720px;
    }

    .cursor {
      display: inline-block;
      width: 10px;
      animation: blink 0.8s infinite;
    }

    @keyframes blink {
      0%, 49% { opacity: 1; }
      50%, 100% { opacity: 0; }
    }

    .hero-actions {
      margin-top: 30px;
      display: flex;
      flex-wrap: wrap;
      gap: 14px;
    }

    button, .link-btn {
      appearance: none;
      border: none;
      outline: none;
      cursor: pointer;
      transition: 0.25s ease;
      font: inherit;
    }

    .btn-primary {
      background: #fff;
      color: #000;
      padding: 14px 22px;
      border-radius: 999px;
      font-weight: 700;
      box-shadow: 0 10px 24px rgba(255,255,255,0.16);
    }

    .btn-primary:hover {
      transform: translateY(-2px) scale(1.01);
    }

    .btn-secondary {
      background: transparent;
      color: #fff;
      padding: 14px 22px;
      border-radius: 999px;
      border: 1px solid rgba(255,255,255,0.16);
    }

    .btn-secondary:hover {
      background: rgba(255,255,255,0.08);
      transform: translateY(-2px);
    }

    .hero-side {
      padding: 24px;
      display: grid;
      gap: 16px;
      align-content: center;
    }

    .mini-box {
      padding: 20px;
      border-radius: 22px;
      background: rgba(255,255,255,0.04);
      border: 1px solid rgba(255,255,255,0.1);
      transition: transform 0.25s ease, background 0.25s ease;
    }

    .mini-box:hover {
      transform: translateY(-4px);
      background: rgba(255,255,255,0.07);
    }

    .mini-label {
      color: var(--muted);
      font-size: 12px;
      text-transform: uppercase;
      letter-spacing: 0.15em;
      margin-bottom: 10px;
    }

    .mini-value {
      font-size: 22px;
      font-weight: 700;
      line-height: 1.4;
    }

    section {
      padding: 18px 0 90px;
    }

    .section-head {
      display: flex;
      align-items: end;
      justify-content: space-between;
      gap: 16px;
      margin-bottom: 26px;
    }

    .section-head h2 {
      margin: 0;
      font-size: clamp(26px, 4vw, 44px);
      letter-spacing: -0.03em;
    }

    .section-head p {
      margin: 0;
      color: var(--muted);
      max-width: 640px;
      line-height: 1.7;
    }

    .reasons {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 18px;
    }

    .reason-card {
      padding: 24px;
      min-height: 220px;
      position: relative;
      overflow: hidden;
    }

    .reason-card::after {
      content: "";
      position: absolute;
      inset: auto -40px -40px auto;
      width: 140px;
      height: 140px;
      border-radius: 50%;
      background: radial-gradient(circle, rgba(255,255,255,0.15), transparent 70%);
      filter: blur(10px);
    }

    .reason-number {
      font-size: 13px;
      color: var(--muted);
      letter-spacing: 0.18em;
      text-transform: uppercase;
      margin-bottom: 18px;
    }

    .reason-card h3 {
      margin: 0 0 12px;
      font-size: 24px;
    }

    .reason-card p {
      margin: 0;
      line-height: 1.7;
      color: #d7d7d7;
    }

    .moments-wrap {
      display: grid;
      grid-template-columns: 0.9fr 1.1fr;
      gap: 18px;
    }

    .note-box,
    .timeline-box,
    .confess-box {
      padding: 28px;
    }

    .note-box p,
    .timeline-item p,
    .confess-box p {
      color: #d8d8d8;
      line-height: 1.8;
    }

    .timeline {
      display: grid;
      gap: 18px;
      margin-top: 8px;
    }

    .timeline-item {
      padding: 18px;
      border-radius: 18px;
      background: rgba(255,255,255,0.04);
      border: 1px solid rgba(255,255,255,0.08);
    }

    .timeline-item span {
      font-size: 12px;
      color: var(--muted);
      text-transform: uppercase;
      letter-spacing: 0.14em;
    }

    .timeline-item h4 {
      margin: 8px 0 8px;
      font-size: 18px;
    }

    .confess-box {
      text-align: center;
      position: relative;
      overflow: hidden;
    }

    .big-line {
      font-size: clamp(30px, 5vw, 52px);
      line-height: 1.1;
      margin: 10px 0 16px;
      letter-spacing: -0.04em;
      font-weight: 800;
    }

    .choice-area {
      margin-top: 28px;
      display: flex;
      justify-content: center;
      flex-wrap: wrap;
      gap: 14px;
      min-height: 120px;
      position: relative;
    }

    .btn-yes {
      background: #fff;
      color: #000;
      padding: 14px 24px;
      border-radius: 999px;
      font-weight: 700;
      position: relative;
    }

    .btn-think {
      background: rgba(255,255,255,0.08);
      color: #fff;
      padding: 14px 24px;
      border-radius: 999px;
      border: 1px solid rgba(255,255,255,0.14);
      position: relative;
    }

    .hidden-message {
      margin-top: 24px;
      font-size: 18px;
      color: #f0f0f0;
      display: none;
      animation: fadeUp 0.5s ease forwards;
    }

    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(10px); }
      to { opacity: 1; transform: translateY(0); }
    }

    .floating-heart {
      position: fixed;
      bottom: -20px;
      font-size: 20px;
      animation: floatUp linear forwards;
      pointer-events: none;
      opacity: 0.9;
    }

    @keyframes floatUp {
      from { transform: translateY(0) scale(0.8); opacity: 0; }
      15% { opacity: 0.9; }
      to { transform: translateY(-110vh) scale(1.4); opacity: 0; }
    }

    .footer {
      padding: 22px 0 40px;
      color: var(--muted);
      text-align: center;
      font-size: 14px;
    }

    .reveal {
      opacity: 0;
      transform: translateY(24px);
      transition: 0.8s ease;
    }

    .reveal.show {
      opacity: 1;
      transform: translateY(0);
    }

    @media (max-width: 900px) {
      .hero-grid,
      .reasons,
      .moments-wrap {
        grid-template-columns: 1fr;
      }

      .hero-main,
      .hero-side,
      .note-box,
      .timeline-box,
      .confess-box,
      .reason-card {
        padding: 24px;
      }

      .section-head {
        flex-direction: column;
        align-items: start;
      }
    }
  </style>
</head>
<body>
  <div class="noise"></div>

  <main>
    <section class="hero">
      <div class="container hero-grid">
        <div class="card hero-main reveal show">
          <div class="eyebrow">A small website for Angel</div>
          <h1> Brigitha Angel Kaunang.</h1>
          <div class="typing-wrap">
            <div class="typing" id="typingText"></div><span class="cursor">|</span>
          </div>
          <div class="hero-actions">
            <button class="btn-primary" onclick="scrollToSection('reasons')">Lihat alasannya</button>
            <button class="btn-secondary" onclick="scrollToSection('confession')">Aku punya sesuatu untukmu</button>
          </div>
        </div>

        <div class="card hero-side reveal">
          <div class="mini-box">
            <div class="mini-label">Tentang kamu</div>
            <div class="mini-value">Cantik, Perduli, Gak Ribet</div>
          </div>
          <div class="mini-box">
            <div class="mini-label">Tempat beraktivitas</div>
            <div class="mini-value">Tzu Chi Hospital</div>
          </div>
          <div class="mini-box">
            <div class="mini-label">Warna favorit</div>
            <div class="mini-value">Hitam mungkin?</div>
          </div>
        </div>
      </div>
    </section>

    <section id="reasons">
      <div class="container">
        <div class="section-head reveal">
          <h2>Hal yang bikin aku tertarik</h2>
          <p>
            Bukan karena aneh, bukan karena berlebihan. Justru karena ada sesuatu yang beda, indah, dan tulus dari dirimu.
          </p>
        </div>

        <div class="reasons">
          <div class="card reason-card reveal">
            <div class="reason-number">01</div>
            <h3>Looks</h3>
            <p>
              Ini normal, setiap orang pasti melihat dari fisik, bagiku kamu lebih dari cantik, aku juga suka cara kamu berpakaian, simpel tapi dress well, caramu memakai make up juga tidak terlalu norak, cantik natural.
            </p>
          </div>
          <div class="card reason-card reveal">
            <div class="reason-number">02</div>
            <h3>Personality</h3>
            <p>
              Aku suka act of service dari kamu, cara kamu perduliin aku, cara kamu perhatiin aku, cara kamu berpikir, cara kamu mengambil keputusan, walaupun kalau ngobrol suka lambat dikit HAHAHA, tapi gapapa itu unik.
            </p>
          </div>
          <div class="card reason-card reveal">
            <div class="reason-number">03</div>
            <h3>How do you think</h3>
            <p>
              Fakta bahwa kamu bekerja di Tzu Chi Hospital membuatku melihat sisi peduli yang tidak semua orang punya, membantu yang mungkin orang yang gak kamu kenal hahaha, dan dengan cara kamu bekerja itu salah satu kalau kamu mampu untuk dirimu sendiri, lebih bisa mengerti bagaimana cara manage, ngga cuma menye menye banyak mau atau banyak minta kaya cewe cewe standar tiktok lainnya... WKWKWK
            </p>
          </div>
        </div>
      </div>
    </section>

    <section>
      <div class="container moments-wrap">
        <div class="card note-box reveal">
          <div class="section-head" style="margin-bottom: 12px;">
            <h2 style="font-size: clamp(24px, 4vw, 34px);">Satu catatan kecil</h2>
          </div>
          <p>
            Website ini tidak dibuat untuk sesuatu yang berlebihan. Aku cuma ingin menyampaikan satu hal dengan cara yang sederhana, jujur, dan mungkin sedikit berbeda.
          </p>
          <p>
            Kalau hitam adalah warna yang kamu suka, maka aku ingin semuanya di sini terasa dekat dengan itu: minimalis, tenang, dan tidak terlalu banyak bicara atau repot. Tetapi cukup untuk membuatmu tahu bahwa kamu spesial.
          </p>
        </div>

        <div class="card timeline-box reveal">
          <div class="section-head" style="margin-bottom: 10px;">
            <h2 style="font-size: clamp(24px, 4vw, 34px);">Yang ingin aku mulai</h2>
          </div>
          <div class="timeline">
            <div class="timeline-item">
              <span>Langkah 1</span>
              <h4>Kenal lebih jauh</h4>
              <p>Bukan tergesa-gesa, cukup mulai dari percakapan yang nyaman hingga mengetahui semua tentangmu langsung dari kamu yang mau jujur terbuka.</p>
            </div>
            <div class="timeline-item">
              <span>Langkah 2</span>
              <h4>Beri ruang yang tulus</h4>
              <p>Aku tidak ingin memaksa. Aku hanya ingin hadir tanpa paksaan yang bukan hak ku untuk mengaturmu.</p>
            </div>
            <div class="timeline-item">
              <span>Langkah 3</span>
              <h4>Jujur tentang perasaan</h4>
              <p>Dan itu alasan utama website ini dibuat untukmu.</p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <section id="confession">
      <div class="container">
        <div class="card confess-box reveal">
          <div class="eyebrow" style="margin-bottom: 8px;">You're My Favorite Notification.</div>
          <div class="big-line">I totally Fallen For u, Angel.</div>
          <p>
            Aku ingin kenal kamu lebih dekat, tanpa drama, tanpa berlebihan, cukup dengan saling dan perasaan yang jujur.
          </p>

          <div class="choice-area" id="choiceArea">
            <button class="btn-yes" id="yesBtn">Aku mau</button>
            <button class="btn-think" id="thinkBtn">Kasih aku waktu dulu</button>
          </div>

          <div class="hidden-message" id="responseMessage"></div>
        </div>
      </div>
    </section>
  </main>

  <div class="footer">Made with a simple heart for Angel.</div>

  <script>
    const text = "Aku membuat halaman ini karena ada sesuatu yang ingin aku bilang ke kamu, Angel. Sesuatu yang sederhana, tapi dengan cara berbeda.";
    const typingTarget = document.getElementById('typingText');
    let i = 0;

    function typeWriter() {
      if (i < text.length) {
        typingTarget.textContent += text.charAt(i);
        i++;
        setTimeout(typeWriter, 28);
      }
    }
    typeWriter();

    function scrollToSection(id) {
      document.getElementById(id).scrollIntoView({ behavior: 'smooth' });
    }

    const observer = new IntersectionObserver((entries) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          entry.target.classList.add('show');
        }
      });
    }, { threshold: 0.15 });

    document.querySelectorAll('.reveal').forEach(el => observer.observe(el));

    const yesBtn = document.getElementById('yesBtn');
    const thinkBtn = document.getElementById('thinkBtn');
    const responseMessage = document.getElementById('responseMessage');
    const choiceArea = document.getElementById('choiceArea');
    let dodgeCount = 0;

    yesBtn.addEventListener('click', () => {
      responseMessage.style.display = 'block';
      responseMessage.textContent = 'Makasih, Angel. Aku akan jaga kesempatan ini dengan baik. ♡';
      launchHearts(18);
      yesBtn.disabled = true;
      thinkBtn.disabled = true;
      yesBtn.style.opacity = '0.8';
      thinkBtn.style.opacity = '0.5';
    });

    thinkBtn.addEventListener('mouseenter', () => {
      if (window.innerWidth < 768) return;
      dodgeButton();
    });

    thinkBtn.addEventListener('click', () => {
      dodgeCount++;
      if (dodgeCount < 2) {
        responseMessage.style.display = 'block';
        responseMessage.textContent = 'Tidak apa-apa, aku bisa menunggu jawaban yang datang dengan nyaman.';
      } else {
        responseMessage.style.display = 'block';
        responseMessage.textContent = 'Tenang, tidak harus sekarang. Yang penting kamu tahu perasaanku.';
      }
    });

    function dodgeButton() {
      const area = choiceArea.getBoundingClientRect();
      const maxX = area.width - thinkBtn.offsetWidth;
      const maxY = area.height - thinkBtn.offsetHeight;
      const x = Math.max(0, Math.random() * maxX);
      const y = Math.max(0, Math.random() * maxY);
      thinkBtn.style.position = 'absolute';
      thinkBtn.style.left = `${x}px`;
      thinkBtn.style.top = `${y}px`;
    }

    function launchHearts(count) {
      for (let i = 0; i < count; i++) {
        const heart = document.createElement('div');
        heart.className = 'floating-heart';
        heart.textContent = Math.random() > 0.5 ? '♡' : '♥';
        heart.style.left = Math.random() * 100 + 'vw';
        heart.style.animationDuration = (3 + Math.random() * 3) + 's';
        heart.style.fontSize = (16 + Math.random() * 20) + 'px';
        document.body.appendChild(heart);
        setTimeout(() => heart.remove(), 6500);
      }
    }
  </script>
</body>
</html>
