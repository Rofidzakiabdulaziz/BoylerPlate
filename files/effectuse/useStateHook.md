import React, { useState } from 'react';

function Counter() {
  // Menggunakan useState untuk mendefinisikan state 'count' dengan nilai awal 0
  const [count, setCount] = useState(0);

  // Fungsi untuk menambah nilai count ketika tombol ditekan
  const increment = () => {
    setCount(count + 1); // Mengubah nilai count dengan menambah 1
  };

  return (
    <div>
      <h1>Hitungan: {count}</h1> {/* Menampilkan nilai count saat ini */}
      {/* Menambahkan event handler onClick yang memanggil fungsi increment */}
      <button onClick={increment}>Tambah</button>
    </div>
  );
}

export default Counter; // Mengekspor komponen Counter sebagai default export
