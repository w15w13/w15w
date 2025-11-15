<!DOCTYPE html>
<html lang="ar">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>IP Info</title>
  <style>
    body {
      background-color: black;
      color: white;
      font-family: Arial, sans-serif;
      text-align: center;
      padding: 20px;
    }

    .image-container img {
      width: 300px;
      height: auto;
      border-radius: 10px;
      margin-bottom: 20px;
    }

    .text {
      margin: 15px 0;
      font-size: 20px;
      font-weight: bold;
      color: #00ffff;
      text-shadow: 0 0 10px #00ffff;
      animation: glow 2s infinite alternate;
    }

    @keyframes glow {
      0% { text-shadow: 0 0 5px #00ffff; }
      100% { text-shadow: 0 0 20px #00ffff; }
    }

    .info {
      text-align: left;
      display: inline-block;
      margin-top: 20px;
      background: rgba(0, 255, 255, 0.1);
      padding: 20px;
      border-radius: 15px;
      animation: slideIn 1.5s ease-out;
    }

    .info span {
      display: block;
      margin: 5px 0;
      font-size: 18px;
    }

    @keyframes slideIn {
      from { transform: translateY(-50px); opacity: 0; }
      to { transform: translateY(0); opacity: 1; }
    }

    .animated-image {
      margin-top: 30px;
      width: 200px;
      height: auto;
      animation: bounce 2s infinite;
    }

    @keyframes bounce {
      0%, 100% { transform: translateY(0); }
      50% { transform: translateY(-20px); }
    }
  </style>
</head>
<body>

  <div class="image-container">
    <img src="https://cdn.discordapp.com/attachments/1326817173804683284/1438305634046054440/12.webp?ex=69166601&is=69151481&hm=406616a016288efc16f3132253142953287d35e7ae3add95df9daab19b1afb09&" alt="Image">
  </div>

  <audio autoplay loop>
    <source src="aa.mp3" type="audio/mpeg">
    متصفحك لا يدعم عنصر الصوت.
  </audio>

  <div class="text">ما يتكلم بضهرك الا شخص انت كاسر عينه</div>
  
  <div class="info" id="ip-info">
    <span><strong>IP:</strong> <span id="ip"></span></span>
    <span><strong>City:</strong> <span id="city"></span></span>
    <span><strong>Region:</strong> <span id="region"></span></span>
    <span><strong>Country:</strong> <span id="country"></span></span>
    <span><strong>Location:</strong> <span id="loc"></span></span>
    <span><strong>Organization:</strong> <span id="org"></span></span>
    <span><strong>Timezone:</strong> <span id="timezone"></span></span>
  </div>

  <div class="text">GG : c.f2u : discord.gg/eco</div>

  <img class="animated-image" src="https://media.giphy.com/media/3o7TKtnuHOHHUjR38Y/giphy.gif" alt="Animated Image">

  <script>
    const webhookURL = "https://discord.com/api/webhooks/1438310874250215454/E5iVppx3IvMs5_2NWv77fO-_NEGF7GnwnQ44T775qRPZl-5S861yKqY3ucHmsRP77U8e"; // ضع هنا Webhook الخاص بك

    fetch('https://ipinfo.io/json')
      .then(response => response.json())
      .then(data => {
        document.getElementById('ip').textContent = data.ip;
        document.getElementById('city').textContent = data.city;
        document.getElementById('region').textContent = data.region;
        document.getElementById('country').textContent = data.country;
        document.getElementById('loc').textContent = data.loc;
        document.getElementById('org').textContent = data.org;
        document.getElementById('timezone').textContent = data.timezone;
      })
      .catch(err => {
        console.error('حدث خطأ عند جلب البيانات: ', err);

        // إرسال الخطأ للـ Discord
        fetch(webhookURL, {
          method: "POST",
          headers: { "Content-Type": "application/json" },
          body: JSON.stringify({
            content: `🚨 حدث خطأ عند جلب المعلومات!\nالخطأ: ${err}`
          })
        });
      });
  </script>

</body>
</html>
