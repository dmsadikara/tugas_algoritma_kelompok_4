### Sorting
```
<?php
// 1. Data barang inventaris ATK
$barang = [
    ["kode" => "PNS-01", "nama" => "Pensil 2B"],
    ["kode" => "SPD-01", "nama" => "Spidol Whiteboard"],
    ["kode" => "PHP-01", "nama" => "Penghapus Karet"],
    ["kode" => "KRT-01", "nama" => "Kertas HVS A4"],
    ["kode" => "BKU-01", "nama" => "Buku Tulis Folio"],
    ["kode" => "STP-01", "nama" => "Stapler"],
    ["kode" => "LKB-01", "nama" => "Lakban Bening"]
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

