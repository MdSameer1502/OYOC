<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>ofyourownchoice</title>

  <!-- Fonts -->
  <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;700&family=Great+Vibes&family=Montserrat:wght@400;500&display=swap" rel="stylesheet">

  <style>
    * { box-sizing: border-box; margin: 0; padding: 0; }
    html, body { height: 100%; font-family: 'Playfair Display', serif; }

    body {
      background: url('oyoc.jpg') no-repeat center 60%/cover;
      background-attachment: fixed;
      color: #fff;
      min-height: 100vh;
      overflow-x: hidden;
    }

    header {
      width: 100%;
      background: #fff;
      color: #000;
      padding: 16px 5%;
      display: flex;
      justify-content: space-between;
      align-items: center;
      position: fixed;
      top: 0;
      z-index: 100;
      box-shadow: 0 2px 8px rgba(0,0,0,0.05);
    }

    .left { display:flex; align-items:center; gap:18px; }
    .menu-toggle { display:flex; flex-direction:column; gap:4px; cursor:pointer; }
    .menu-toggle span { width:22px; height:2px; background:#000; border-radius:2px; }

    nav {
      display:flex; align-items:center; gap:18px; font-family:'Montserrat',sans-serif; font-size:13px; letter-spacing:0.6px;
    }
    nav a { color:#000; text-decoration:none; font-weight:500; }
    nav .divider { color:#999; margin:0 6px; }

    .search-icon { font-size:18px; cursor:pointer; }

    .hero { height: 100vh; position: relative; }

    .hero-content {
      position: absolute;
      left: 50%;
      transform: translateX(-50%);
      top: 10%;
      width: min(920px, 92%);
      text-align: center;
      z-index: 20;
    }

    .brand {
      font-family: 'Great Vibes', cursive;
      font-size: 34px;
      color: white;
      margin-bottom: 8px;
    }

    .headline {
      font-family: 'Playfair Display', serif;
      font-size: 56px;
      line-height: 1.06;
      color: white;
      margin-bottom: 12px;
      font-weight:700;
    }

    .sub {
      font-family: 'Montserrat', sans-serif;
      color: #fff;
      font-size: 16px;
      margin-bottom: 22px;
      opacity: 0.95;
    }

    .btn {
      display: inline-block;
      background: #f7f1e9;
      color: #000;
      padding: 14px 34px;
      border-radius: 32px;
      border: none;
      font-weight: 600;
      cursor: pointer;
      box-shadow: 0 10px 18px rgba(0,0,0,0.12);
      transition: transform .18s;
    }
    .btn:hover { transform: translateY(-3px); }

    .mobile-nav {
      display: none;
      position: absolute;
      top: 64px;
      left: 0;
      width: 100%;
      background: #fff;
      padding: 12px 5%;
      box-shadow: 0 6px 20px rgba(0,0,0,0.08);
      z-index: 95;
      flex-direction: column;
      gap: 8px;
    }
    .mobile-nav a { color:#000; text-decoration:none; padding:8px 0; }

    /* MODAL STYLES */
    .modal {
      display: none;
      position: fixed;
      z-index: 200;
      left: 0;
      top: 0;
      width: 100%;
      height: 100%;
      background: rgba(0,0,0,0.6);
      justify-content: center;
      align-items: center;
    }

    .modal-content {
      background: #fff;
      color: #000;
      padding: 28px 36px;
      border-radius: 16px;
      width: min(400px, 90%);
      box-shadow: 0 12px 28px rgba(0,0,0,0.2);
      font-family: 'Montserrat', sans-serif;
      text-align: center;
      position: relative;
      animation: fadeIn .3s ease;
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: scale(0.9); }
      to { opacity: 1; transform: scale(1); }
    }

    .modal-content h2 {
      font-family: 'Playfair Display', serif;
      margin-bottom: 16px;
      font-size: 24px;
    }

    .modal-content label {
      display: block;
      text-align: left;
      margin-top: 10px;
      font-size: 14px;
      font-weight: 600;
      color: #333;
    }

    .modal-content input {
      width: 100%;
      padding: 10px 12px;
      margin-top: 4px;
      border: 1px solid #ccc;
      border-radius: 8px;
      font-size: 14px;
    }

    .modal-content button {
      margin-top: 16px;
      padding: 12px 20px;
      background: #000;
      color: #fff;
      border: none;
      border-radius: 24px;
      font-weight: 600;
      cursor: pointer;
    }

    .close-btn {
      position: absolute;
      top: 10px;
      right: 14px;
      font-size: 22px;
      cursor: pointer;
      color: #666;
    }

    @media (max-width: 900px) {
      nav { display:none; }
      .menu-toggle { display:flex; }
      .hero-content { top: 8%; width: 94%; }
      .headline { font-size: 36px; }
      .brand { font-size: 28px; margin-bottom: 4px; }
    }
    @media (min-width: 1200px) {
      .headline { font-size: 72px; }
      .brand { font-size: 40px; }
    }
  </style>
</head>
<body>

  <header>
    <div class="left">
      <div class="menu-toggle" id="menuToggle">
        <span></span><span></span><span></span>
      </div>

      <nav class="desktop-nav" id="desktopNav">
        <a href="oyoc.html">HOME</a><span class="divider">|</span>
        <a href="aboutus.html">ABOUT</a><span class="divider">|</span>
        <a href="howitworks2.html">HOW IT WORKS</a><span class="divider">|</span>
        <a href="https://ideogram.ai/" target="_blank">CREATE</a><span class="divider">|</span>
        <a href="#" id="uploadNavLink">UPLOAD</a><span class="divider">|</span>
        <a href="contact1.html">CONTACT</a>
      </nav>
    </div>

    <div class="right">
      <div class="search-icon" title="Search">🔍</div>
    </div>

    <div class="mobile-nav" id="mobileNav">
      <a href="oyoc.html">HOME</a>
      <a href="aboutus.html">ABOUT</a>
      <a href="howitworks2.html">HOW IT WORKS</a>
      <a href="https://ideogram.ai/" target="_blank">CREATE</a>
      <a href="#" id="mobileUploadLink">UPLOAD</a>
      <a href="contact1.html">CONTACT</a>
    </div>
  </header>

  <main>
    <section class="hero">
      <div class="hero-content">
        <div class="brand">ofyourownchoice</div>
        <div class="headline">Design clothes<br>that are truly yours.</div>
        <div class="sub">Upload your photo or idea — we'll turn it into a real outfit.</div>
        <button class="btn" id="uploadBtn">Upload | your photo / design</button>
      </div>
    </section>
  </main>

  <!-- Upload Modal -->
  <div class="modal" id="uploadModal">
    <div class="modal-content">
      <span class="close-btn" id="closeModal">&times;</span>
      <h2>Enter your details</h2>
      <form id="uploadForm">
        <label for="name">Full Name</label>
        <input type="text" id="name" required>

        <label for="email">Email</label>
        <input type="email" id="email" required>

        <label for="mobile">Mobile / WhatsApp</label>
        <input type="tel" id="mobile" required>

        <label for="uploadInput">Upload Image / Design</label>
        <input type="file" id="uploadInput" accept="image/*" required>

        <button type="submit">Submit</button>
      </form>
    </div>
  </div>

  <script>

  // Mobile nav toggle
  const menuToggle = document.getElementById('menuToggle');
  const mobileNav = document.getElementById('mobileNav');
  menuToggle.addEventListener('click', () => {
    const open = mobileNav.style.display === 'flex';
    mobileNav.style.display = open ? 'none' : 'flex';
  });

  // Modal handling
  const uploadBtn = document.getElementById('uploadBtn');
  const uploadNavLink = document.getElementById('uploadNavLink');
  const mobileUploadLink = document.getElementById('mobileUploadLink');
  const modal = document.getElementById('uploadModal');
  const closeModal = document.getElementById('closeModal');

  function openModal(e) {
    e.preventDefault();
    modal.style.display = 'flex';
    if (window.innerWidth <= 900) mobileNav.style.display = 'none';
  }

  [uploadBtn, uploadNavLink, mobileUploadLink].forEach(el => {
    if (el) el.addEventListener('click', openModal);
  });

  closeModal.addEventListener('click', () => modal.style.display = 'none');
  window.addEventListener('click', (e) => {
    if (e.target === modal) modal.style.display = 'none';
  });

  // ====== FORM SUBMIT TO BACKEND ======
  const form = document.getElementById('uploadForm');
  form.addEventListener('submit', async (e) => {
    e.preventDefault();

    const formData = new FormData();
    formData.append('name', document.getElementById('name').value);
    formData.append('email', document.getElementById('email').value);
    formData.append('mobile', document.getElementById('mobile').value);
    formData.append('image', document.getElementById('uploadInput').files[0]);

    const response = await fetch('http://localhost:5000/upload', {
      method: 'POST',
      body: formData
    });

    const data = await response.text();
    alert(data);
    modal.style.display = 'none';
    form.reset();
  });
</script>


</body>
</html>
