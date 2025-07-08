<!DOCTYPE html>
<html lang="th">
<head>
  <meta charset="UTF-8">
  <title>ร่วมทำบุญอุปสมบทหมู่</title>
  <link href="https://fonts.googleapis.com/css2?family=Prompt:wght@300;500;700&display=swap" rel="stylesheet">
  <style>
    body {
      font-family: 'Prompt', sans-serif;
      background: linear-gradient(to bottom right, #fffbe6, #ffe3d3);
      margin: 0;
      padding: 0;
    }

    header {
      background: #c62828;
      color: white;
      padding: 30px 20px;
      text-align: center;
      border-bottom: 5px solid gold;
    }

    header h1 {
      margin: 0;
      font-size: 26px;
    }

    header p {
      font-size: 18px;
      margin-top: 10px;
    }

    .form-container {
      background: white;
      max-width: 600px;
      margin: 40px auto;
      padding: 30px;
      border-radius: 15px;
      box-shadow: 0 8px 30px rgba(0,0,0,0.15);
    }

    h2 {
      text-align: center;
      color: #b71c1c;
      margin-bottom: 30px;
    }

    label {
      font-weight: 500;
      margin-bottom: 6px;
      display: block;
    }

    input[type="text"], input[type="number"], input[type="file"] {
      width: 100%;
      padding: 10px;
      margin-bottom: 20px;
      border: 1px solid #ccc;
      border-radius: 8px;
      box-sizing: border-box;
      font-size: 16px;
    }

    button {
      width: 100%;
      background: #c62828;
      color: white;
      padding: 12px;
      border: none;
      border-radius: 8px;
      font-size: 16px;
      cursor: pointer;
      transition: background 0.3s ease;
    }

    button:hover {
      background: #b71c1c;
    }

    #response {
      text-align: center;
      color: green;
      margin-top: 20px;
    }

    footer {
      text-align: center;
      font-size: 14px;
      color: #888;
      margin-bottom: 30px;
    }
  </style>
</head>
<body>

  <header>
    <h1>โครงการอุปสมบทบวชพระหมู่ เฉลิมพระเกียรติ</h1>
    <p>
      พระบาทสมเด็จพระเจ้าอยู่หัว เนื่องในโอกาสเฉลิมพระชนมพรรษา 73 พรรษา<br>
      ณ วัดสะแก ต.บางเลน อ.บางใหญ่ จ.นนทบุรี<br>
      วันที่ 10 กรกฎาคม 2568
    </p>
  </header>

  <div class="form-container">
    <h2>ร่วมทำบุญแล้วส่งสลิปการโอน</h2>
    <form id="donationForm">
      <label>ชื่อ</label>
      <input type="text" name="fname" required>

      <label>นามสกุล</label>
      <input type="text" name="lname" required>

      <label>จำนวนเงิน (บาท)</label>
      <input type="number" name="amount" required>

      <label>แนบสลิปการโอน</label>
      <input type="file" name="slip" accept="image/*,.pdf" required>

      <button type="submit">ส่งข้อมูล</button>
    </form>
    <p id="response"></p>
  </div>

  <footer>
    ขออนุโมทนาบุญทุกท่านที่ร่วมสืบสานพระพุทธศาสนา
  </footer>

  <script>
    const form = document.getElementById('donationForm');
    form.addEventListener('submit', async (e) => {
      e.preventDefault();
      const formData = new FormData(form);
      document.getElementById('response').innerText = "กำลังส่งข้อมูล...";

      const res = await fetch("https://script.google.com/macros/s/AKfycbyiJT0e_DK-iUQ6Evn4or57bTVedMa0vlTzyePm3KA70qMud2hOCdM3wrcAXNikJ2Nw/exec", {
        method: "POST",
        body: formData,
      });

      const result = await res.text();
      document.getElementById('response').innerText = result;
      form.reset();
    });
  </script>

</body>
</html>
