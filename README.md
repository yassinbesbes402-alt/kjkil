<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>نسمة بلاي</title>
  <style>
    * {
      margin: 0; padding: 0; box-sizing: border-box;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    }
    body {
      background-color: #000; color: #fff;
      overflow-x: hidden;
    }
    header {
      background: rgba(0, 0, 0, 0.85);
      backdrop-filter: blur(8px);
      padding: 15px 30px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      position: sticky; top: 0; z-index: 100;
      border-bottom: 1px solid #222;
    }
    .logo { 
      font-size: 28px; 
      font-weight: bold; 
      color: #e50914; 
      text-shadow: 0 0 8px rgba(229, 9, 20, 0.4);
    }
    nav a { 
      color: #fff; 
      text-decoration: none; 
      margin-left: 20px; 
      font-size: 16px; 
      font-weight: 500;
      transition: color 0.2s;
    }
    nav a:hover { 
      color: #e50914; 
    }

    .hero {
      height: 60vh;
      min-height: 400px;
      max-height: 600px;
      background: 
        linear-gradient(to bottom, rgba(0,0,0,0.4) 0%, rgba(0,0,0,0.9) 100%),
        url('https://i.imgur.com/9JZQe1H.jpg') no-repeat center center/cover;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      padding: 0 20px;
      text-align: center;
      color: white;
    }
    .hero h1 {
      font-size: 48px;
      font-weight: bold;
      color: #ffd700;
      text-shadow: 2px 2px 8px #000;
      margin-bottom: 15px;
      font-family: 'Amiri', serif;
    }
    .hero p {
      font-size: 18px;
      max-width: 600px;
      margin-bottom: 25px;
      color: #eee;
      text-shadow: 1px 1px 3px #000;
      line-height: 1.6;
    }
    .btn {
      display: inline-block;
      background: #e50914;
      color: white;
      padding: 12px 30px;
      border-radius: 30px;
      text-decoration: none;
      font-weight: bold;
      transition: all 0.3s ease;
      box-shadow: 0 4px 12px rgba(229, 9, 20, 0.4);
    }
    .btn:hover {
      background: #f40612;
      transform: translateY(-2px);
      box-shadow: 0 6px 16px rgba(229, 9, 20, 0.6);
    }

    .section-title {
      padding: 30px 80px 15px;
      font-size: 26px;
      font-weight: bold;
      color: #fff;
      position: relative;
    }
    .section-title::after {
      content: '';
      position: absolute;
      bottom: 0;
      right: 80px;
      width: 60px;
      height: 3px;
      background: #e50914;
      border-radius: 3px;
    }

    .carousel {
      display: flex;
      overflow-x: auto;
      padding: 0 80px 30px;
      gap: 20px;
      scrollbar-width: none;
    }
    .carousel::-webkit-scrollbar { display: none; }
    .show-card {
      min-width: 180px;
      height: 250px;
      border-radius: 12px;
      overflow: hidden;
      cursor: pointer;
      position: relative;
      transition: transform 0.3s, box-shadow 0.3s;
    }
    .show-card:hover {
      transform: scale(1.05);
      box-shadow: 0 8px 20px rgba(0, 0, 0, 0.6);
      z-index: 2;
    }
    .show-card img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }
    .show-card::after {
      content: '▶';
      position: absolute;
      top: 0; left: 0;
      width: 100%; height: 100%;
      background: rgba(0, 0, 0, 0.6);
      display: flex;
      align-items: center;
      justify-content: center;
      color: white;
      font-size: 32px;
      opacity: 0;
      transition: opacity 0.3s;
    }
    .show-card:hover::after {
      opacity: 1;
    }

    /* نافذة الإعلان */
    #ad-modal {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0,0,0,0.95);
      z-index: 2000;
      justify-content: center;
      align-items: center;
    }
    #ad-content {
      background: #111;
      width: 95%;
      max-width: 800px;
      border-radius: 16px;
      padding: 20px;
      position: relative;
      color: white;
      box-shadow: 0 10px 40px rgba(0, 0, 0, 0.8);
      border: 1px solid #333;
    }
    #close-ad {
      position: absolute;
      top: 15px;
      left: 15px;
      background: #e50914;
      color: white;
      border: none;
      width: 32px;
      height: 32px;
      border-radius: 50%;
      cursor: pointer;
      font-size: 18px;
      font-weight: bold;
      display: flex;
      align-items: center;
      justify-content: center;
    }

    /* نوافذ النظام */
    #settings-modal,
    #subscription-modal,
    #sms-modal,
    #modal {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0,0,0,0.95);
      z-index: 1000;
      justify-content: center;
      align-items: center;
    }
    #settings-content,
    #subscription-content,
    #sms-content {
      background: #1a1a1a;
      width: 95%;
      max-width: 500px;
      border-radius: 16px;
      padding: 25px;
      color: white;
      text-align: center;
      box-shadow: 0 10px 30px rgba(0,0,0,0.8);
    }
    #subscription-content { max-width: 1000px; }

    #modal-content {
      background: #111;
      width: 95%;
      max-width: 900px;
      border-radius: 16px;
      padding: 25px;
      position: relative;
      color: white;
      overflow-y: auto;
      max-height: 90vh;
      box-shadow: 0 10px 40px rgba(0, 0, 0, 0.8);
      border: 1px solid #333;
      text-align: initial;
    }

    .cancel-subscription {
      display: block;
      width: 100%;
      background: #b00000;
      color: white;
      padding: 12px;
      border-radius: 20px;
      border: none;
      font-weight: bold;
      cursor: pointer;
      margin-top: 15px;
      transition: background 0.3s;
    }
    .cancel-subscription:hover { background: #800000; }

    .plans-container {
      display: flex;
      flex-wrap: wrap;
      gap: 15px;
      justify-content: center;
      margin: 20px 0;
    }
    .plan-card {
      min-width: 220px;
      background: #222;
      border-radius: 12px;
      padding: 18px;
      text-align: center;
      cursor: pointer;
      transition: transform 0.2s, box-shadow 0.2s;
      box-shadow: 0 4px 10px rgba(0,0,0,0.3);
    }
    .plan-card:hover { transform: translateY(-5px); box-shadow: 0 6px 15px rgba(0,0,0,0.4); }
    .plan-header {
      background: #b00000;
      color: white;
      padding: 10px;
      border-radius: 10px 10px 0 0;
      font-weight: bold;
      margin: -18px -18px 18px;
      font-size: 18px;
    }
    .plan-price {
      font-size: 28px;
      font-weight: bold;
      color: #ffd700;
      margin: 15px 0;
    }
    .plan-btn {
      display: block;
      width: 100%;
      background: #e50914;
      color: white;
      padding: 12px;
      border-radius: 20px;
      text-decoration: none;
      font-weight: bold;
      text-align: center;
      margin-top: 12px;
      transition: background 0.3s;
    }
    .plan-btn:hover { background: #f40612; }

    .sms-input {
      width: 100%;
      padding: 12px;
      border-radius: 20px;
      border: none;
      background: #222;
      color: white;
      font-size: 16px;
      margin: 15px 0;
      text-align: center;
    }
    .sms-btn {
      width: 100%;
      background: #e50914;
      color: white;
      padding: 12px;
      border-radius: 20px;
      border: none;
      font-weight: bold;
      cursor: pointer;
      transition: background 0.3s;
    }
    .sms-btn:hover { background: #f40612; }
    .change-offer {
      color: #ff3333;
      text-decoration: underline;
      cursor: pointer;
      margin-top: 15px;
      font-size: 14px;
      display: inline-block;
    }
    .offer-details {
      margin-top: 20px;
      font-size: 16px;
      color: #ccc;
      line-height: 1.6;
    }

    #close-modal {
      position: absolute;
      top: 15px;
      left: 15px;
      background: #e50914;
      color: white;
      border: none;
      width: 32px;
      height: 32px;
      border-radius: 50%;
      cursor: pointer;
      font-size: 18px;
      font-weight: bold;
      display: flex;
      align-items: center;
      justify-content: center;
    }

    .episode-list {
      list-style: none;
      margin-top: 20px;
      display: flex;
      flex-wrap: wrap;
      gap: 10px;
      justify-content: center;
    }
    .episode-item {
      padding: 10px 16px;
      background: #2a2a2a;
      border-radius: 8px;
      cursor: pointer;
      transition: all 0.2s;
      text-align: center;
      font-size: 16px;
      font-weight: bold;
      min-width: 50px;
      border: 2px solid transparent;
    }
    .episode-item.active {
      background: #e50914;
      color: white;
      border-color: #ff4d4d;
      transform: scale(1.05);
    }

    footer {
      text-align: center;
      padding: 25px;
      color: #666;
      background: #0a0a0a;
      margin-top: 20px;
      border-top: 1px solid #222;
    }

    @media (max-width: 768px) {
      .hero h1 { font-size: 34px; }
      .hero p { font-size: 16px; max-width: 90%; }
      .section-title, .carousel { padding-left: 20px; padding-right: 20px; }
      .section-title::after { right: 20px; }
      .show-card { min-width: 140px; height: 200px; }
      nav a { margin-left: 12px; font-size: 14px; }
      .btn { padding: 10px 24px; font-size: 16px; }
      .plans-container { gap: 10px; }
      .plan-card { min-width: 180px; padding: 14px; }
    }
  </style>
  <link href="https://fonts.googleapis.com/css2?family=Amiri:wght@700&display=swap" rel="stylesheet">
</head>
<body>

  <header>
    <div class="logo">نسمة بلاي</div>
    <nav>
      <a href="#home">الرئيسية</a>
      <a href="#new">جديد</a>
      <a href="#popular">الأكثر مشاهدة</a>
      <a href="#" onclick="openSettings()">الإعدادات</a>
    </nav>
  </header>

  <section class="hero">
    <h1>طبيب المعجزة</h1>
    <p>قصة طبيب شاب يمتلك موهبة استثنائية في تشخيص الأمراض المستعصية.</p>
    <a href="#" class="btn" onclick="openAd()">شاهد الآن</a>
  </section>

  <h2 class="section-title">أحدث المسلسلات</h2>
  <div class="carousel">
    <div class="show-card" onclick="checkSubscription()">
      <img src="https://i.imgur.com/9JZQe1H.jpg" alt="طبيب المعجزة">
    </div>
  </div>

  <!-- نافذة الإعلان (مجاني) -->
  <div id="ad-modal">
    <div id="ad-content">
      <button id="close-ad" onclick="closeAd()">×</button>
      <h3 style="text-align:center; margin-bottom:15px; color:#ffd700;">الإعلان الرسمي</h3>
      <div style="position: relative; padding-bottom: 56.25%; height: 0; overflow: hidden; border-radius: 12px;">
        <iframe 
          src="https://player.vimeo.com/video/1128597220?badge=0&autopause=0&player_id=0&app_id=58479" 
          frameborder="0" 
          allow="autoplay; fullscreen; picture-in-picture; clipboard-write; encrypted-media; web-share" 
          referrerpolicy="strict-origin-when-cross-origin" 
          style="position:absolute;top:0;left:0;width:100%;height:100%;"
          title="الاعلان الرسمي">
        </iframe>
      </div>
    </div>
  </div>

  <!-- نظام الاشتراك -->
  <div id="settings-modal">
    <div id="settings-content">
      <h2>الإعدادات</h2>
      <button class="cancel-subscription" onclick="cancelSubscription()">إلغاء الاشتراك</button>
    </div>
  </div>

  <div id="subscription-modal">
    <div id="subscription-content">
      <button id="close-modal" onclick="closeSubscription()">×</button>
      <h2 style="color: #ffd700;">اختر خطة الاشتراك</h2>
      <div class="plans-container">
        <div class="plan-card" onclick="startSmsPlan(1000, 1)">
          <div class="plan-header">1 jour</div>
          <div class="plan-icon">📱</div>
          <div class="plan-payment">SMS</div>
          <div class="plan-price">1,000 TND <span style="font-size:14px;color:#ccc">TTC</span></div>
          <a href="#" class="plan-btn" onclick="startSmsPlan(1000, 1); return false;">S'abonner maintenant</a>
        </div>
        <div class="plan-card" onclick="startSmsPlan(2500, 7)">
          <div class="plan-header">7 jours</div>
          <div class="plan-icon">📱</div>
          <div class="plan-payment">SMS</div>
          <div class="plan-price">2,500 TND <span style="font-size:14px;color:#ccc">TTC</span></div>
          <a href="#" class="plan-btn" onclick="startSmsPlan(2500, 7); return false;">S'abonner maintenant</a>
        </div>
        <div class="plan-card" onclick="startSmsPlan(7500, 30)">
          <div class="plan-header">30 jours</div>
          <div class="plan-icon">📱</div>
          <div class="plan-payment">SMS</div>
          <div class="plan-price">7,500 TND <span style="font-size:14px;color:#ccc">TTC</span></div>
          <a href="#" class="plan-btn" onclick="startSmsPlan(7500, 30); return false;">S'abonner maintenant</a>
        </div>
        <div class="plan-card" onclick="startCardPlan(10900, 90)">
          <div class="plan-header">90 jours</div>
          <div class="plan-icon">💳</div>
          <div class="plan-payment">Carte bancaire</div>
          <div class="plan-price">10,900 TND <span style="font-size:14px;color:#ccc">TTC</span></div>
          <a href="#" class="plan-btn" onclick="startCardPlan(10900, 90); return false;">S'abonner maintenant</a>
        </div>
        <div class="plan-card" onclick="startCardPlan(17900, 180)">
          <div class="plan-header">180 jours</div>
          <div class="plan-icon">💳</div>
          <div class="plan-payment">Carte bancaire</div>
          <div class="plan-price">17,900 TND <span style="font-size:14px;color:#ccc">TTC</span></div>
          <a href="#" class="plan-btn" onclick="startCardPlan(17900, 180); return false;">S'abonner maintenant</a>
        </div>
      </div>
    </div>
  </div>

  <div id="sms-modal">
    <div id="sms-content">
      <button id="close-modal" onclick="closeSmsModal()">×</button>
      <h2>Abonnement SMS</h2>
      <p style="color: #ccc; font-size: 20px; font-weight: bold;">94285710</p>
      <p style="margin: 5px 0; color: #ddd; font-size: 16px;">ارسل للرقم</p>
      <p style="margin: 5px 0 15px; color: #ffd700; font-weight: bold; font-size: 18px;">OK</p>
      <input type="text" class="sms-input" id="sms-code" placeholder="أدخل الكود الذي استلمته عبر SMS" maxlength="6">
      <button class="sms-btn" id="confirm-btn" onclick="validateCode()">تأكيد</button>
      <div class="change-offer" onclick="backToPlans()">تغيير الخطة</div>
      <div class="offer-details">
        خطتك المختارة: <strong id="selected-offer">7 أيام</strong><br>
        السعر: <strong id="selected-price">2,500</strong> <span style="color:#ff3333">TND</span>
      </div>
    </div>
  </div>

  <!-- نافذة الحلقات -->
  <div id="modal">
    <div id="modal-content">
      <button id="close-modal" onclick="closeModal()">×</button>
      <h2 id="modal-title" style="text-align:center; color:#ffd700;">الحلقة 17</h2>
      <div id="video-container" style="width: 100%; height: 0; padding-bottom: 56.25%; position: relative; margin: 20px 0; background: #000; border-radius: 12px; overflow: hidden;"></div>
      <h3 style="margin: 20px 0 10px; text-align: center; color: #ddd;">قائمة الحلقات:</h3>
      <ul class="episode-list" id="episodes-list"></ul>
    </div>
  </div>

  <footer>
    © 2025 نسمة بلاي. جميع الحقوق محفوظة.
  </footer>

  <script>
    const episodes = {
      15: "https://player.vimeo.com/video/1128573436?badge=0&autopause=0&player_id=0&app_id=58479",
      16: "https://player.vimeo.com/video/1128576593?badge=0&autopause=0&player_id=0&app_id=58479",
      17: "https://player.vimeo.com/video/1128597885?badge=0&autopause=0&player_id=0&app_id=58479"
    };

    // === الإعلان (مجاني) ===
    function openAd() {
      document.getElementById('ad-modal').style.display = 'flex';
    }
    function closeAd() {
      document.getElementById('ad-modal').style.display = 'none';
    }

    // === الفيديو (بالاشتراك) ===
    function loadVideo(episode) {
      const container = document.getElementById('video-container');
      const iframe = document.createElement('iframe');
      iframe.src = episodes[episode];
      iframe.frameBorder = "0";
      iframe.allow = "autoplay; fullscreen; picture-in-picture; clipboard-write; encrypted-media; web-share";
      iframe.referrerPolicy = "strict-origin-when-cross-origin";
      iframe.title = `الحلقة ${episode}`;
      iframe.style = "position:absolute;top:0;left:0;width:100%;height:100%;";
      container.innerHTML = '';
      container.appendChild(iframe);
      document.getElementById('modal-title').textContent = `الحلقة ${String(episode).padStart(2, '0')}`;
    }

    function generateEpisodeList() {
      const list = document.getElementById('episodes-list');
      list.innerHTML = '';
      [15, 16, 17].forEach(i => {
        const li = document.createElement('li');
        li.className = 'episode-item';
        li.textContent = String(i).padStart(2, '0');
        li.onclick = function() {
          document.querySelectorAll('.episode-item').forEach(item => item.classList.remove('active'));
          this.classList.add('active');
          loadVideo(i);
        };
        list.appendChild(li);
      });
      list.children[2].classList.add('active');
      loadVideo(17);
    }

    function openVideo() {
      document.getElementById('modal').style.display = 'flex';
      generateEpisodeList();
    }

    function closeModal() {
      document.getElementById('modal').style.display = 'none';
    }

    // === نظام الاشتراك (يعمل 100%) ===
    function checkSubscription() {
      const subscription = JSON.parse(localStorage.getItem('subscription')) || {};
      const now = new Date().getTime();
      if (subscription.expires && now < subscription.expires) {
        openVideo();
      } else {
        document.getElementById('subscription-modal').style.display = 'flex';
      }
    }

    function closeSubscription() { document.getElementById('subscription-modal').style.display = 'none'; }
    function closeSmsModal() { document.getElementById('sms-modal').style.display = 'none'; }
    function backToPlans() {
      document.getElementById('sms-modal').style.display = 'none';
      document.getElementById('subscription-modal').style.display = 'flex';
    }
    function openSettings() { document.getElementById('settings-modal').style.display = 'flex'; }

    let selectedPrice = 0;
    let selectedDays = 0;

    function startSmsPlan(price, days) {
      selectedPrice = price;
      selectedDays = days;
      document.getElementById('selected-price').textContent = formatPrice(price);
      document.getElementById('selected-offer').textContent = getOfferName(days);
      closeSubscription();
      document.getElementById('sms-modal').style.display = 'flex';
    }

    function startCardPlan(price, days) {
      selectedPrice = price;
      selectedDays = days;
      document.getElementById('selected-price').textContent = formatPrice(price);
      document.getElementById('selected-offer').textContent = getOfferName(days);
      closeSubscription();
      document.getElementById('sms-modal').style.display = 'flex';
    }

    function formatPrice(price) {
      return price.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",") + ' TND';
    }

    function getOfferName(days) {
      return `${days} أيام`;
    }

    function validateCode() {
      const codeInput = document.getElementById('sms-code').value.trim();
      if (!codeInput) {
        showErrorMessage("الرجاء إدخال كود التحقق.");
        return;
      }

      const validCodes = {
        1000: ['123456', '654321', '111111', '222222'],
        2500: ['470012', '046580', '874000', '624302'],
        7500: ['114031', '637051', '040442', '640125']
      };

      const usedCodes = JSON.parse(localStorage.getItem('used_codes')) || [];

      if (usedCodes.includes(codeInput)) {
        showErrorMessage(`الكود ${codeInput} تم استخدامه مسبقًا.`);
        return;
      }

      const planPrice = selectedPrice;
      const allowedCodes = validCodes[planPrice] || [];

      if (!allowedCodes.includes(codeInput)) {
        showErrorMessage(`الكود غير صالح.`);
        return;
      }

      usedCodes.push(codeInput);
      localStorage.setItem('used_codes', JSON.stringify(usedCodes));

      const expires = new Date().getTime() + (selectedDays * 24 * 60 * 60 * 1000);
      localStorage.setItem('subscription', JSON.stringify({
        expires: expires,
        price: selectedPrice,
        days: selectedDays,
        code: codeInput
      }));

      showSuccessMessage();

      setTimeout(() => {
        document.getElementById('sms-modal').style.display = 'none';
        openVideo();
      }, 5000);
    }

    function showErrorMessage(message) {
      const errorModal = document.createElement('div');
      errorModal.id = 'feedback-modal';
      errorModal.style.cssText = `
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: rgba(0,0,0,0.95);
        z-index: 1005;
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
      `;
      errorModal.innerHTML = `
        <div style="background: #222; padding: 30px; border-radius: 16px; text-align: center; color: white; max-width: 320px; box-shadow: 0 10px 30px rgba(0,0,0,0.7);">
          <div style="font-size: 50px; color: #ff5555; margin-bottom: 15px;">✖</div>
          <h3 style="margin: 10px 0; font-size: 24px; color: #ffd700;">خطأ</h3>
          <p style="margin: 15px 0; font-size: 16px; color: #ccc; line-height: 1.5;">${message}</p>
          <button id="feedback-ok-btn" style="width: 100%; background: #e50914; color: white; padding: 12px; border-radius: 20px; border: none; font-weight: bold; cursor: pointer; margin-top: 15px;">OK</button>
        </div>
      `;
      document.body.appendChild(errorModal);
      const close = () => {
        if (document.body.contains(errorModal)) document.body.removeChild(errorModal);
      };
      document.getElementById('feedback-ok-btn').addEventListener('click', close);
      setTimeout(close, 5000);
    }

    function showSuccessMessage() {
      const successModal = document.createElement('div');
      successModal.id = 'feedback-modal';
      successModal.style.cssText = `
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: rgba(0,0,0,0.95);
        z-index: 1005;
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
      `;
      successModal.innerHTML = `
        <div style="background: #222; padding: 30px; border-radius: 16px; text-align: center; color: white; max-width: 320px; box-shadow: 0 10px 30px rgba(0,0,0,0.7);">
          <div style="font-size: 50px; color: #00ff00; margin-bottom: 15px;">✓</div>
          <h3 style="margin: 10px 0; font-size: 24px; color: #ffd700;">مرحبا</h3>
          <button id="success-ok-btn" style="width: 100%; background: #00aa00; color: white; padding: 12px; border-radius: 20px; border: none; font-weight: bold; cursor: pointer; margin-top: 20px;">OK</button>
        </div>
      `;
      document.body.appendChild(successModal);
      const close = () => {
        if (document.body.contains(successModal)) document.body.removeChild(successModal);
      };
      document.getElementById('success-ok-btn').addEventListener('click', close);
      setTimeout(close, 5000);
    }

    function cancelSubscription() {
      localStorage.removeItem('subscription');
      localStorage.removeItem('used_codes');
      alert("تم إلغاء اشتراكك بنجاح.");
      document.getElementById('settings-modal').style.display = 'none';
      if (document.getElementById('modal').style.display === 'flex') closeModal();
    }

    window.onclick = function(e) {
      if (e.target.id === 'ad-modal') closeAd();
      if (e.target.id === 'subscription-modal') closeSubscription();
      if (e.target.id === 'sms-modal') closeSmsModal();
      if (e.target.id === 'modal') closeModal();
      if (e.target.id === 'settings-modal') document.getElementById('settings-modal').style.display = 'none';
    };

    document.addEventListener('keydown', function(e) {
      if (e.key === 'Escape') {
        closeAd();
        closeModal();
        closeSubscription();
        closeSmsModal();
        document.getElementById('settings-modal').style.display = 'none';
      }
    });
  </script>
</body>
</html>
