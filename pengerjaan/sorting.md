### Sorting
```
<?php
// 1. Data barang inventaris ATK
$barang = [
    ["kode" => "PNS-01", "nama" => "Pensil 2B"],
    ["kode" => "SPD-01", "nama" => "Spidol Hitam"],
    ["kode" => "PNG-01", "nama" => "Penghapus"],
    ["kode" => "KRT-01", "nama" => "Kertas HVS A4"],
    ["kode" => "KRT-02", "nama" => "Kertas Folio"],
    ["kode" => "STP-01", "nama" => "Stapler"],
    ["kode" => "SLT-01", "nama" => "Selotip"],
    ["kode" => "STC-01", "nama" => "Sticky Notes"],
    ["kode" => "GNT-01", "nama" => "Gunting"],
    ["kode" => "MPK-01", "nama" => "Map Kertas"],

];

// 2. Ambil pilihan algoritma dari form
$metode = $_GET["metode"] ?? "";
$hasil = $barang;

// 3. Bubble Sort
if ($metode == "bubble") {
    $n = count($hasil);

    for ($i = 0; $i < $n - 1; $i++) {
        for ($j = 0; $j < $n - 1; $j++) {

            if (strcasecmp(
                $hasil[$j]["nama"]
                $hasil[$j + 1]["nama"]
            ) > 0) {

                // Tuker dua barang bersebelahan
                $temp = $hasil[$j];
                $hasil[$j] = $hasil[$j + 1];
                $hasil[$j + 1] = $temp;
            }
        }
    }
}

// 4. Selection Sort
elseif ($metode === "selection") {
    $n = count($hasil);

    for ($i = 0; $i < $n - 1; $i++) {
        $min = $i;

        // Cari nama terkecil di sisa data
        for ($j = $i + 1; $j < $n; $j++) {
            if (strcasecmp(
                $hasil[$j]["nama"],
                $hasil[$min]["nama"]
            ) < 0) {
                $min = $j;
            }
        }

        // Tukar posisi saat ini
        $temp = $hasil[$i];
        $hasil[$i] = $hasil[$min];
        $hasil[$min] = $temp;
    }
}
?>

<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <title>Inventaris ATK Kantor</title>
</head>
<body>

    <h2>Inventaris ATK Kantor</h2>

    <h3>Sorting / Pengurutuan Barang</h3>

    <form method="GET">
        <label>Pilih metode sorting:</label>

        <select name="metode">
            <option value="">Data awal</option>
            <option value="bubble"
                <? $metode == "bubble" ? "selected" : "" ?>>
                Bubble sort
            </option>
            <option value="selection"
                <?= $metode == "selection" ? "selected" : "" ?>>
                Selection Sort
            </option>
        </select>

        <button type="submit">Urutkan</button>
    </form>

    <br>

    <table border="1" cellpadding="10"
            cellspacing="0">
        <tr>
            <th>No.</th>
            <th>Kode Barang</th>
            <th>Nama Barang</th>
        <tr>

        <?php foreach ($hasil as $i => $item): ?>
        <tr>
            <td><?= $i + 1 ?></td>
            <td><?= htmlspecialchars($item["kode"]) ?></td>
            <td><?= htmlspecialchars($item["nama"]) ?></td
        </tr>
        <?php endforeach; ?>
    </table>

</body>
</html>


