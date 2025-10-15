
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>LTO Kiosk Portal</title>
<style>
  body {
    margin: 0;
    font-family: 'Segoe UI', sans-serif;
    background: url('https://portal.lto.gov.ph/ords/r/lto_theme/files/static/v1200/banner-bg.jpg') no-repeat center center fixed;
    background-size: cover;
    overflow: hidden;
  }

  .banner {
    background: rgba(0, 45, 98, 0.85);
    color: white;
    text-align: center;
    padding: 40px 0;
    font-size: 2em;
    font-weight: bold;
    letter-spacing: 1px;
    backdrop-filter: blur(6px);
  }

  .container {
    display: flex;
    width: 100%;
    height: 75vh;
    align-items: center;
    justify-content: center;
    padding: 0 30px;
    box-sizing: border-box;
  }

  /* LEFT VERTICAL MENU */
  .left-menu {
    width: 200px;
    background: rgba(0, 45, 98, 0.85);
    color: white;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: flex-start;
    padding: 15px 10px;
    margin-left: 20px; /* ✅ offset from screen edge */
    border-radius: 15px;
    backdrop-filter: blur(6px);
    height: 85%;
    margin-top: auto;
    margin-bottom: auto;
  }

  .menu-item {
    width: 160px;
    background: white;
    color: #002d62;
    margin: 10px;
    padding: 15px;
    border-radius: 10px;
    text-align: center;
    font-weight: bold;
    text-decoration: none;
    transition: 0.3s;
    cursor: pointer;
    box-shadow: 0 2px 8px rgba(0,0,0,0.2);
  }

  .menu-item:hover, .menu-item.active {
    background: #f2b600;
    color: #002d62;
    transform: scale(1.1);
  }

  /* RIGHT MAIN SLIDER */
  .main-slider-wrapper {
    position: relative;
    flex-grow: 1;
    overflow: hidden;
    margin-left: 40px;
    border-radius: 15px;
    background: rgba(255,255,255,0.7);
    backdrop-filter: blur(4px);
    box-shadow: 0 4px 20px rgba(0,0,0,0.2);
  }

  .main-slider {
    display: flex;
    transition: transform 0.7s cubic-bezier(0.68, -0.55, 0.27, 1.55);
    height: 100%;
  }

  .slide {
    min-width: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    text-align: center;
    color: #002d62;
    font-size: 1.5em;
    font-weight: bold;
    background: linear-gradient(to bottom right, rgba(255,255,255,0.7), rgba(230,235,255,0.9));
    cursor: pointer;
    transition: transform 0.3s;
  }

  .slide:hover {
    transform: scale(1.03);
  }

  .slide img {
    width: 120px;
    margin-bottom: 20px;
  }

  footer {
    background: rgba(0, 33, 77, 0.9);
    color: white;
    padding: 20px;
    text-align: center;
    font-size: 0.9em;
    backdrop-filter: blur(6px);
  }
</style>
</head>
<body>

<div class="banner">Land Transportation Office - Interactive Kiosk Portal</div>

<div class="container">
  <!-- LEFT MENU -->
  <div class="left-menu" id="menu">
    <div class="menu-item active" onclick="showSlide(0)">Citizen’s Charter</div>
    <div class="menu-item" onclick="showSlide(1)">DLS</div>
    <div class="menu-item" onclick="showSlide(2)">MVIRS</div>
    <div class="menu-item" onclick="showSlide(3)">LETAS</div>
    <div class="menu-item" onclick="showSlide(4)">LTO Portal</div>
    <div class="menu-item" onclick="showSlide(5)">Plate Tracker</div>
    <div class="menu-item" onclick="showSlide(6)">eGov.ph</div>
  </div>

  <!-- RIGHT SLIDER -->
  <div class="main-slider-wrapper">
    <div class="main-slider" id="slider">
      <div class="slide" onclick="openLink('https://lto.gov.ph/fixed-transaction.html')">
        <img src="https://upload.wikimedia.org/wikipedia/commons/6/6d/LTO_Logo_2022.png" alt="LTO Logo">
        Citizen’s Charter Overview
      </div>
      <div class="slide" onclick="openLink('https://portal.lto.gov.ph/ords/f?p=1200:HOME::::::')">
        <img src="https://cdn-icons-png.flaticon.com/512/3106/3106921.png" alt="DLS">
        Driver’s Licensing System (DLS)
      </div>
      <div class="slide" onclick="openLink('https://portal.lto.gov.ph/ords/f?p=1300:LOGIN_DESKTOP::::::')">
        <img src="https://cdn-icons-png.flaticon.com/512/3208/3208727.png" alt="MVIRS">
        Motor Vehicle Information & Registration System (MVIRS)
      </div>
      <div class="slide" onclick="openLink('https://portal.lto.gov.ph/ords/f?p=1400:LOGIN_DESKTOP::::::')">
        <img src="https://cdn-icons-png.flaticon.com/512/639/639365.png" alt="LETAS">
        Law Enforcement Ticketing App System (LETAS)
      </div>
      <div class="slide" onclick="openLink('https://portal.lto.gov.ph/')">
        <img src="https://cdn-icons-png.flaticon.com/512/639/639375.png" alt="Portal">
        LTO Main Portal
      </div>
      <div class="slide" onclick="openLink('https://lto.gov.ph/plate-inquiry.html')">
        <img src="https://cdn-icons-png.flaticon.com/512/3106/3106924.png" alt="Plate Tracker">
        Plate Tracker System
      </div>
      <div class="slide" onclick="openLink('https://egov.ph/')">
        <img src="https://cdn-icons-png.flaticon.com/512/1828/1828859.png" alt="eGov">
        Download eGov.ph App
      </div>
    </div>
  </div>
</div>

<footer>
  © 2025 Land Transportation Office. All Rights Reserved.<br>
  Republic of the Philippines - Official Government Website
</footer>

<script>
  let currentSlide = 0;
  function showSlide(index) {
    const slider = document.getElementById('slider');
    const menuItems = document.querySelectorAll('.menu-item');
    currentSlide = index;
    slider.style.transform = `translateX(-${index * 100}%)`;
    menuItems.forEach((item, i) => {
      item.classList.toggle('active', i === index);
    });
  }

  // ✅ Opens links in a smaller popup window (for kiosk use)
  function openLink(url) {
    window.open(
      url,
      '_blank',
      'width=1024,height=700,menubar=no,toolbar=no,location=no,status=no,resizable=yes,scrollbars=yes'
    );
  }
</script>

</body>
</html>
