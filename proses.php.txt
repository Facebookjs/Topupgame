<?php
include 'config.php';

if ($_SERVER['REQUEST_METHOD'] === 'POST') {
    $game    = mysqli_real_escape_string($conn, $_POST['game']);
    $user_id = mysqli_real_escape_string($conn, $_POST['user_id']);
    $jumlah  = mysqli_real_escape_string($conn, $_POST['jumlah']);
    $payment = mysqli_real_escape_string($conn, $_POST['payment']);

    $sql = "INSERT INTO orders (game, user_id, jumlah, payment)
            VALUES ('$game', '$user_id', '$jumlah', '$payment')";

    if (mysqli_query($conn, $sql)) {
        echo "<script>alert('Pesanan berhasil dikirim!'); window.location='index.php';</script>";
    } else {
        echo "Gagal: " . mysqli_error($conn);
    }
}
?>