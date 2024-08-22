import React, { useState, useMemo } from 'react';

function ExpensiveComputation({ num }) {
  // Fungsi simulasi untuk menghitung nilai yang memakan waktu
  const compute = (num) => {
    console.log('Menghitung nilai...'); // Mencetak ke konsol saat perhitungan dilakukan
    return num * 2; // Mengembalikan hasil perhitungan
  };

  // Menggunakan useMemo untuk meng-cache hasil perhitungan
  // Hasil perhitungan hanya akan diperbarui jika 'num' berubah
  const result = useMemo(() => compute(num), [num]);

  return (
    <div>
      <h1>Hasil: {result}</h1> {/* Menampilkan hasil perhitungan */}
    </div>
  );
}

function App() {
  // Mendeklarasikan state 'num' dengan nilai awal 1
  const [num, setNum] = useState(1);

  return (
    <div>
      <input
        type="number"
        value={num} // Mengikat nilai input dengan state 'num'
        onChange={(e) => setNum(parseInt(e.target.value))} // Mengubah state 'num' saat input berubah
      />
      {/* Mengirim nilai 'num' sebagai props ke ExpensiveComputation */}
      <ExpensiveComputation num={num} />
    </div>
  );
}

export default App; // Mengekspor komponen App sebagai default export
