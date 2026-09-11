<!DOCTYPE html>
<html lang="bn">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Payment & Refund UI</title>
  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: 'Segoe UI', Arial, sans-serif;
    }

    body {
      background-color: #f4f4f4;
      display: flex;
      justify-content: center;
      align-items: flex-start;
      min-height: 100vh;
      padding: 0;
    }

    .container {
      width: 100%;
      max-width: 420px;
      background-color: #ffffff;
      min-height: 100vh;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
      display: flex;
      flex-direction: column;
      align-items: center;
      padding-bottom: 30px;
    }

    /* Top Header Bar */
    .header {
      width: 100%;
      background-color: #005a36;
      color: #ffffff;
      padding: 12px 16px;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }

    .header-left {
      display: flex;
      flex-direction: column;
    }

    .header-amount {
      font-size: 18px;
      font-weight: bold;
    }

    .header-subtext {
      font-size: 11px;
      color: #e0e0e0;
      margin-top: 2px;
    }

    .header-right {
      display: flex;
      align-items: center;
      gap: 6px;
    }

    .badge-pay {
      background-color: #ffffff;
      color: #005a36;
      font-size: 11px;
      font-weight: bold;
      padding: 3px 6px;
      border-radius: 3px;
    }

    .badge-service {
      font-size: 11px;
      letter-spacing: 0.5px;
      font-weight: 500;
    }

    .badge-lang {
      background-color: rgba(255, 255, 255, 0.2);
      font-size: 10px;
      padding: 2px 5px;
      border-radius: 3px;
      margin-left: 4px;
    }

    /* Alert / Instruction Text */
    .alert-text {
      margin-top: 20px;
      font-size: 13px;
      color: #d93025;
      font-weight: 600;
      text-align: center;
    }

    /* Cash / Payment Numbers Box */
    .payment-box {
      width: 90%;
      background-color: #e5e5e5;
      border-radius: 6px;
      padding: 15px;
      margin-top: 15px;
      display: flex;
      flex-direction: column;
      gap: 12px;
      box-shadow: inset 0 0 4px rgba(0,0,0,0.1);
    }

    .payment-row {
      display: flex;
      align-items: center;
      gap: 12px;
    }

    .logo-circle {
      width: 45px;
      height: 45px;
      border-radius: 50%;
      display: flex;
      justify-content: center;
      align-items: center;
      color: white;
      font-weight: bold;
      font-size: 11px;
      flex-shrink: 0;
    }

    .logo-nagad {
      background-color: #f7931e;
      border: 2px solid #e31837;
    }

    .logo-bkash {
      background-color: #e2136e;
    }

    .number-input {
      flex: 1;
      background-color: #ffffff;
      padding: 8px 12px;
      border-radius: 4px;
      font-size: 18px;
      font-weight: 600;
      letter-spacing: 1px;
      color: #333;
      border: 1px solid #ccc;
    }

    /* Refund Number & Amount Section */
    .refund-section {
      margin-top: 20px;
      width: 90%;
      background: #f9f9f9;
      border: 1px solid #e0e0e0;
      border-radius: 8px;
      padding: 15px;
    }

    .refund-number-box {
      background: #ffffff;
      border: 1px dashed #005a36;
      border-radius: 6px;
      padding: 10px;
      text-align: center;
      margin-bottom: 12px;
    }

    .refund-number-label {
      font-size: 12px;
      color: #666;
      font-weight: 600;
      margin-bottom: 4px;
    }

    .refund-number-value {
      font-size: 18px;
      font-weight: bold;
      color: #005a36;
      letter-spacing: 1px;
    }

    .amount-info {
      display: flex;
      flex-direction: column;
      gap: 8px;
      font-size: 14px;
      text-align: left;
      background: #fff;
      padding: 10px 12px;
      border-radius: 6px;
      border: 1px solid #eee;
    }

    .amount-info .return {
      color: #005a36;
      font-weight: bold;
    }

    .amount-info .locked {
      color: #d93025;
      font-weight: bold;
      display: flex;
      align-items: center;
      gap: 4px;
    }

    .lock-icon {
      width: 15px;
      height: 15px;
      fill: #d93025;
      display: inline-block;
      vertical-align: middle;
    }

    /* TrxID Input Section */
    .trx-help-link {
      margin-top: 20px;
      font-size: 13px;
      color: #17a2b8;
      font-weight: 600;
      text-decoration: none;
    }

    .trx-input-box {
      width: 90%;
      margin-top: 10px;
    }

    .trx-input {
      width: 100%;
      padding: 10px 12px;
      border: 1px solid #d93025;
      border-radius: 8px;
      font-size: 13px;
      outline: none;
      color: #333;
    }

    /* Live Countdown Section */
    .countdown-box {
      width: 90%;
      margin-top: 15px;
      font-size: 14px;
      font-weight: bold;
      color: #333;
      text-align: left;
      display: flex;
      align-items: center;
      gap: 8px;
    }

    .timer-text {
      color: #d93025;
      font-weight: bold;
      font-size: 15px;
    }

    /* Submit Button */
    .submit-btn {
      margin-top: 25px;
      background-color: #ffffff;
      border: 1px solid #666;
      padding: 8px 30px;
      border-radius: 8px;
      font-size: 14px;
      font-weight: 600;
      cursor: pointer;
      box-shadow: 0 2px 4px rgba(0,0,0,0.1);
    }

    .submit-btn:hover {
      background-color: #f0f0f0;
    }

    /* Status Screen Styles */
    .status-view {
      display: flex;
      flex-direction: column;
      align-items: center;
      padding: 40px 20px;
      text-align: center;
      width: 100%;
    }

    .status-icon {
      width: 65px;
      height: 65px;
      border-radius: 50%;
      display: flex;
      justify-content: center;
      align-items: center;
      font-size: 32px;
      margin-bottom: 15px;
      color: white;
    }

    .status-icon.success { background-color: #198754; }
    .status-icon.failed { background-color: #d93025; }

    .status-title {
      font-size: 20px;
      font-weight: bold;
      margin-bottom: 8px;
    }

    .status-title.success { color: #198754; }
    .status-title.failed { color: #d93025; }

    .status-desc {
      color: #555;
      font-size: 13px;
      margin-bottom: 20px;
      line-height: 1.5;
    }

    .summary-card {
      background: #f8f9fa;
      border: 1px solid #e0e0e0;
      border-radius: 8px;
      padding: 15px;
      width: 90%;
      text-align: left;
      font-size: 14px;
    }

    .summary-item {
      display: flex;
      justify-content: space-between;
      padding: 6px 0;
      border-bottom: 1px dashed #ddd;
    }

    .summary-item:last-child {
      border-bottom: none;
    }

    .badge-processing {
      background-color: #ffeba8;
      color: #856404;
      padding: 2px 8px;
      border-radius: 4px;
      font-size: 12px;
      font-weight: 600;
    }

    .badge-failed {
      background-color: #f8d7da;
      color: #721c24;
      padding: 2px 8px;
      border-radius: 4px;
      font-size: 12px;
      font-weight: 600;
    }

    .retry-btn {
      margin-top: 20px;
      background-color: #005a36;
      color: white;
      border: none;
      padding: 10px 24px;
      border-radius: 6px;
      font-size: 14px;
      font-weight: 600;
      cursor: pointer;
    }
  </style>
</head>
<body>

  <div class="container" id="mainContainer">
    <!-- Header -->
    <div class="header">
      <div class="header-left">
        <span class="header-amount">BDT 2849.00</span>
        <span class="header-subtext">কম বা বেশি ক্যাশআউট করবেন না</span>
      </div>
      <div class="header-right">
        <span class="badge-pay">PAY</span>
        <span class="badge-service">SERVICE</span>
        <span class="badge-lang">EN  ভাষা</span>
      </div>
    </div>

    <!-- Alert Text -->
    <div class="alert-text">
      🚨🚨🚨 নিচে স্ক্রল করুন এবং 【Send Money】
    </div>

    <!-- Phone Number Boxes -->
    <div class="payment-box">
      <div class="payment-row">
        <div class="logo-circle logo-nagad">নগদ</div>
        <div class="number-input">01918099690</div>
      </div>
      <div class="payment-row">
        <div class="logo-circle logo-bkash">bkash</div>
        <div class="number-input">01830482266</div>
      </div>
    </div>

    <!-- Return Account & Amount Box -->
    <div class="refund-section">
      <div class="refund-number-box">
        <div class="refund-number-label">রিটার্ন পাওয়ার অ্যাকাউন্ট নম্বর:</div>
        <div class="refund-number-value">01XXXXXXXXX</div>
      </div>

      <div class="amount-info">
        <div class="return">রিটার্ন অ্যামাউন্ট: ৳ 6,298</div>
        <div class="locked">
          <svg class="lock-icon" viewBox="0 0 24 24">
            <path d="M18 8h-1V6c0-2.76-2.24-5-5-5S7 3.24 7 6v2H6c-1.1 0-2 .9-2 2v10c0 1.1.9 2 2 2h12c1.1 0 2-.9 2-2V10c0-1.1-.9-2-2-2zm-6 9c-1.1 0-2-.9-2-2s.9-2 2-2 2 .9 2 2-.9 2-2 2zm3.1-9H8.9V6c0-1.71 1.39-3.1 3.1-3.1 1.71 0 3.1 1.39 3.1 3.1v2z"/>
          </svg>
          লকড অ্যামাউন্ট: ৳ 3,449 (লক হয়ে আছে)
        </div>
      </div>
    </div>

    <!-- TrxID Help Link & Input -->
    <a href="#" class="trx-help-link">কীভাবে TrxID পেতে হয় তা দেখতে ক্লিক করুন</a>
    <div class="trx-input-box">
      <input type="text" id="trxInput" class="trx-input" placeholder="TrxID অবশ্যই পূরণ করতে হবে!">
    </div>

    <!-- Live Timer Countdown Box -->
    <div class="countdown-box">
      <span>মেয়াদ শেষ:</span>
      <span class="timer-text" id="countdown">31:00</span>
    </div>

    <!-- Submit Button -->
    <button class="submit-btn" onclick="validateTrx()">নিশ্চিত</button>
  </div>

  <script>
    // ১. রিয়েল-টাইম কাউন্টডাউন টাইমার ফাংশনাল লজিক
    const DURATION_IN_MINUTES = 31;
    let endTime = localStorage.getItem('paymentEndTime');

    if (!endTime) {
      endTime = Date.now() + DURATION_IN_MINUTES * 60 * 1000;
      localStorage.setItem('paymentEndTime', endTime);
    } else {
      endTime = parseInt(endTime, 10);
    }

    function updateTimer() {
      const countdownElement = document.getElementById('countdown');
      if (!countdownElement) return;

      const now = Date.now();
      const distance = endTime - now;

      if (distance <= 0) {
        localStorage.removeItem('paymentEndTime');
        countdownElement.textContent = "সময় শেষ!";
        return;
      }

      let minutes = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
      let seconds = Math.floor((distance % (1000 * 60)) / 1000);

      minutes = minutes < 10 ? '0' + minutes : minutes;
      seconds = seconds < 10 ? '0' + seconds : seconds;

      countdownElement.textContent = `${minutes}:${seconds}`;
    }

    // প্রতি ১ সেকেন্ড পরপর টাইমার আপডেট হওয়া
    updateTimer();
    const timerInterval = setInterval(updateTimer, 1000);

    // ২. ট্রানজেকশন ভ্যালিডেশন
    function validateTrx() {
      const userInput = document.getElementById('trxInput').value.trim();
      const container = document.getElementById('mainContainer');

      const trxPattern = /^[A-Za-z0-9]{8,12}$/;

      if (trxPattern.test(userInput)) {
        container.innerHTML = `
          <div class="header">
            <div class="header-left">
              <span class="header-amount">BDT 1150.00</span>
              <span class="header-subtext">পেমেন্ট স্টেটাস</span>
            </div>
            <div class="header-right">
              <span class="badge-pay">PAY</span>
              <span class="badge-service">SERVICE</span>
            </div>
          </div>

          <div class="status-view">
            <div class="status-icon success">✓</div>
            <div class="status-title success">ট্রানজেকশন সফল হয়েছে!</div>
            <div class="status-desc">আপনার অনুরোধটি সফলভাবে গ্রহণ করা হয়েছে। এটি বর্তমানে প্রসেসিং অবস্থায় রয়েছে।</div>

            <div class="summary-card">
              <div class="summary-item">
                <span>TrxID:</span>
                <strong>${userInput}</strong>
              </div>
              <div class="summary-item">
                <span>রিটার্ন অ্যামাউন্ট:</span>
                <strong>৳ 6,298</strong>
              </div>
              <div class="summary-item">
                <span>স্ট্যাটাস:</span>
                <span class="badge-processing">প্রসেসিং চলছে...</span>
              </div>
            </div>
          </div>
        `;
      } else {
        container.innerHTML = `
          <div class="header">
            <div class="header-left">
              <span class="header-amount">BDT 1150.00</span>
              <span class="header-subtext">পেমেন্ট স্টেটাস</span>
            </div>
            <div class="header-right">
              <span class="badge-pay">PAY</span>
              <span class="badge-service">SERVICE</span>
            </div>
          </div>

          <div class="status-view">
            <div class="status-icon failed">✕</div>
            <div class="status-title failed">ট্রানজেকশন ব্যর্থ হয়েছে!</div>
            <div class="status-desc">আপনার প্রদত্ত TrxID (${userInput || 'খালি'}) সঠিক নয়। অনুগ্রহ করে পুনরায় চেষ্টা করুন।</div>

            <div class="summary-card">
              <div class="summary-item">
                <span>প্রদত্ত TrxID:</span>
                <strong>${userInput || 'নাই'}</strong>
              </div>
              <div class="summary-item">
                <span>স্ট্যাটাস:</span>
                <span class="badge-failed">ব্যর্থ / ভ্যালিড নয়</span>
              </div>
            </div>

            <button class="retry-btn" onclick="window.location.reload()">পুনরায় চেষ্টা করুন</button>
          </div>
        `;
      }
    }
  </script>

</body>
</html>
