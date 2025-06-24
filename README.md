<!DOCTYPE html>
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
    .payment-info {
      margin-top: 30px;
      font-size: 18px;
    }
    .payment-info strong {
      color: #00e0ff;
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

      <select id="pembayaran" required>
        <option value="">Pilih Metode Pembayaran</option>
        <option value="DANA (0895-1837-1444)">DANA (0895-1837-1444)</option>
        <option value="Cash di Tempat">Cash di Tempat</option>
      </select>

      <button class="btn" onclick="kirimBooking()">Kirim Reservasi via WhatsApp</button>
    </div>

    <div class="payment-info">
      <p>Pembayaran bisa melalui:</p>
      <p><strong>DANA: 0895-1837-1444</strong> atau <strong>Cash di tempat</strong></p>
    </div>
  </div>

  <script>
    function kirimBooking() {
      const nama = document.getElementById('nama').value;
      const tanggal = document.getElementById('tanggal').value;
      const jam = document.getElementById('jam').value;
      const pembayaran = document.getElementById('pembayaran').value;

      if (!nama || !tanggal || !jam || !pembayaran) {
        alert("Harap lengkapi semua data booking!");
        return;
      }

      const noWa = "6289518371444";
      const pesan = `Halo HB Barbershop! Saya ingin reservasi potong rambut:\n\n👤 Nama: ${nama}\n📅 Tanggal: ${tanggal}\n🕒 Jam: ${jam}\n💳 Metode Pembayaran: ${pembayaran}\n\nTerima kasih!`;
      const url = `https://wa.me/${noWa}?text=${encodeURIComponent(pesan)}`;

      window.open(url, '_blank');
    }
  </script>
</body>
</html>

