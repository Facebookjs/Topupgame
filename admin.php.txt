<?php include 'config.php'; ?>

<!DOCTYPE html>
<html>
<head>
    <title>Admin - Daftar Pesanan</title>
    <link href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css" rel="stylesheet">
</head>
<body class="bg-gray-100 p-6">
    <div class="max-w-6xl mx-auto bg-white p-6 rounded shadow">
        <h2 class="text-2xl font-bold mb-4">Daftar Pesanan Top Up</h2>
        <table class="min-w-full table-auto border-collapse">
            <thead>
                <tr class="bg-gray-200">
                    <th class="p-2 border">ID</th>
                    <th class="p-2 border">Game</th>
                    <th class="p-2 border">User ID</th>
                    <th class="p-2 border">Jumlah</th>
                    <th class="p-2 border">Pembayaran</th>
                    <th class="p-2 border">Tanggal</th>
                </tr>
            </thead>
            <tbody>
                <?php
                $result = mysqli_query($conn, "SELECT * FROM orders ORDER BY created_at DESC");
                while ($row = mysqli_fetch_assoc($result)):
                ?>
                <tr class="hover:bg-gray-50">
                    <td class="p-2 border text-center"><?= $row['id'] ?></td>
                    <td class="p-2 border"><?= htmlspecialchars($row['game']) ?></td>
                    <td class="p-2 border"><?= htmlspecialchars($row['user_id']) ?></td>
                    <td class="p-2 border"><?= htmlspecialchars($row['jumlah']) ?></td>
                    <td class="p-2 border"><?= htmlspecialchars($row['payment']) ?></td>
                    <td class="p-2 border text-sm"><?= $row['created_at'] ?></td>
                </tr>
                <?php endwhile; ?>
            </tbody>
        </table>
    </div>
</body>
</html>