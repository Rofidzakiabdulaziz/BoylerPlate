import React, { useState, useCallback } from 'react';

// Komponen Button menerima properti onClick dan children
function Button({ onClick, children }) {
  console.log('Button dirender'); // Mencetak ke konsol setiap kali komponen Button dirender
  return <button onClick={onClick}>{children}</button>; // Mengembalikan elemen tombol dengan event handler onClick
}

function Counter() {
  // Mendeklarasikan state 'count' dengan nilai awal 0
  const [count, setCount] = useState(0);

  // Menggunakan useCallback untuk memoize fungsi 'increment'
  // Fungsi 'increment' hanya akan dibuat ulang jika 'count' berubah
  const increment = useCallback(() => {
    setCount(count + 1); // Menambah nilai 'count' dengan 1
  }, [count]); // 'count' adalah dependensi dari useCallback

  return (
    <div>
      <h1>Hitungan: {count}</h1> {/* Menampilkan nilai count */}
      {/* Menggunakan komponen Button dengan properti onClick yang diisi dengan fungsi increment */}
      <Button onClick={increment}>Tambah</Button>
    </div>
  );
}

export default Counter; // Mengekspor komponen Counter sebagai default export
