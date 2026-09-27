<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pilihan Paket Item</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background-color: #121212;
            color: #ffffff;
            display: flex;
            justify-content: center;
            padding: 20px;
        }
        .container {
            max-width: 500px;
            width: 100%;
            background: #1e1e1e;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.5);
        }
        h2 {
            text-align: center;
            color: #00d2d3;
        }
        .grid-options {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 10px;
            margin-top: 20px;
        }
        .option-card {
            background: #2d2d2d;
            border: 2px solid transparent;
            padding: 15px;
            border-radius: 8px;
            text-align: center;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        .option-card:hover, .option-card.selected {
            border-color: #00d2d3;
            background: #3a3a3a;
        }
        .amount {
            font-size: 1.2em;
            font-weight: bold;
        }
        .price {
            font-size: 0.9em;
            color: #aaa;
            margin-top: 5px;
        }
        button {
            width: 100%;
            padding: 12px;
            margin-top: 20px;
            background-color: #00d2d3;
            border: none;
            border-radius: 6px;
            color: #121212;
            font-weight: bold;
            font-size: 1em;
            cursor: pointer;
        }
        button:disabled {
            background-color: #555;
            cursor: not-allowed;
        }
    </style>
</head>
<body>

<div class="container">
    <h2>Pilih Paket Diamond</h2>
    <div class="grid-options">
        <div class="option-card" onclick="selectOption(this, 100, 20000)">
            <div class="amount">100 Diamond</div>
            <div class="price">Rp 20.000</div>
        </div>
        <div class="option-card" onclick="selectOption(this, 250, 50000)">
            <div class="amount">250 Diamond</div>
            <div class="price">Rp 50.000</div>
        </div>
        <div class="option-card" onclick="selectOption(this, 500, 100000)">
            <div class="amount">500 Diamond</div>
            <div class="price">Rp 100.000</div>
        </div>
        <div class="option-card" onclick="selectOption(this, 1000, 190000)">
            <div class="amount">1000 Diamond</div>
            <div class="price">Rp 190.000</div>
        </div>
    </div>

    <button id="btn-submit" disabled onclick="processSelection()">Lanjut Pembelian</button>
</div>

<script>
    let selectedPackage = null;

    function selectOption(element, amount, price) {
        // Hapus kelas 'selected' dari semua pilihan
        document.querySelectorAll('.option-card').forEach(card => {
            card.classList.remove('selected');
        });

        // Tambahkan kelas 'selected' pada pilihan yang diklik
        element.classList.add('selected');

        // Simpan data pilihan
        selectedPackage = { amount, price };

        // Aktifkan tombol
        document.getElementById('btn-submit').disabled = false;
    }

    function processSelection() {
        if (selectedPackage) {
            alert(`Anda memilih ${selectedPackage.amount} Diamond seharga Rp ${selectedPackage.price.toLocaleString('id-ID')}`);
        }
    }
</script>

</body>
</html>
