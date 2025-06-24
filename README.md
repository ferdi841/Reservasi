<!DOCTYPE html>/* Tambahkan di bagian <style> */
.logo-container {
  perspective: 1000px;
  width: 150px;
  height: 150px;
  margin: 0 auto 20px;
}

.logo-flip {
  width: 100%;
  height: 100%;
  position: relative;
  transform-style: preserve-3d;
  animation: flip 5s infinite linear;
}

.logo-flip img {
  width: 100%;
  height: 100%;
  position: absolute;
  border-radius: 50%;
  backface-visibility: hidden;
}

.logo-front {
  transform: rotateY(0deg);
}

.logo-back {
  transform: rotateY(180deg);
  opacity: 0.8;
}

@keyframes flip {
  0% { transform: rotateY(0deg); }
  100% { transform: rotateY(360deg); }
}

<html lang="id">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>HB Barbershop</title>
  <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@700&family=Open+Sans&display=swap" rel="stylesheet">
  <style>
    * {
      margin: 0; padding: 0;
      box-sizing: border-box;
    }
    body {
      font-family: 'Open Sans', sans-serif;
      background: url('IMG_2048.png') no-repeat center center fixed;
      background-size: cover;
      color: white;
    }
    .overlay {
      background: rgba(0, 0, 0, 0.85);
      min-height: 100vh;
      padding: 60px 20px;
      text-align: center;
    }
    .logo {
      max-width: 120px;
      margin-bottom: 20px;
    }
    h1 {
      font-family: 'Playfair Display', serif;
      font-size: 42px;
      margin-bottom: 10px;
    }
    .tagline {
      font-size: 18px;
      color: #ccc;
      margin-bottom: 30px;
    }
    .form-box {
      background: rgba(255,255,255,0.1);
      border-radius: 12px;
      padding: 25px;
      max-width: 400px;
      margin: 0 auto;
    }
    input, select {
      width: 100%;
      padding: 12px;
      margin: 10px 0;
      border: none;
      border-radius: 8px;
      font-size: 16px;
    }
    .btn {
      background: #25d366;
      color: white;
      padding: 15px;
      width: 100%;
      font-size: 18px;
      border: none;
      border-radius: 50px;
      cursor: pointer;
      transition: 0.3s;
    }
    .btn:hover {
      background: #1eba5a;
    }
  </style>
</head>
<body>
  <div class="overlay">
    <img src="IMG_2048.png" alt="Logo HB Barbershop" class="logo" />
    <h1>HB Barbershop</h1>
    <p class="tagline">Booking Gaya Potong Kamu Sekarang</p>

    <div class="form-box">
      <input type="text" id="nama" placeholder="Nama Lengkap" required />
      <input type="date" id="tanggal" required />
      <input type="time" id="jam" required />
      <button class="btn" onclick="kirimBooking()">Kirim Reservasi via WhatsApp</button>
    </div>
  </div>

  <script>
    function kirimBooking() {
      const nama = document.getElementById('nama').value;
      const tanggal = document.getElementById('tanggal').value;
      const jam = document.getElementById('jam').value;

      if (!nama || !tanggal || !jam) {
        alert("Harap lengkapi semua data booking!");
        return;
      }

      const noWa = "6289518371444";
      const pesan = `Halo HB Barbershop! Saya ingin reservasi potong rambut:\n\n👤 Nama: ${nama}\n📅 Tanggal: ${tanggal}\n🕒 Jam: ${jam}\n\nTerima kasih!`;
      const url = `https://wa.me/${noWa}?text=${encodeURIComponent(pesan)}`;

      window.open(url, '_blank');
    }
  </script>
</body>
</html>
