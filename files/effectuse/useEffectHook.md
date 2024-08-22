import React, { useState, useEffect } from 'react';

function DataFetcher() {
  // State untuk menyimpan data yang di-fetch dan status loading
  const [data, setData] = useState(null); // State untuk menyimpan data
  const [loading, setLoading] = useState(true); // State untuk mengindikasikan status loading

  // Menggunakan useEffect untuk fetch data ketika komponen dimounting
  useEffect(() => {
    fetch('https://api.example.com/data') // Fetch data dari API
      .then(response => response.json()) // Mengonversi response menjadi JSON
      .then(data => {
        setData(data); // Menyimpan data ke state
        setLoading(false); // Mengatur loading ke false setelah data berhasil di-fetch
      });
  }, []); // Array kosong [] sebagai dependency array agar effect hanya berjalan sekali saat komponen dimount

  if (loading) {
    return <div>Loading...</div>; // Menampilkan loading state jika data masih di-fetch
  }

  return (
    <div>
      <h1>Data yang di-fetch:</h1>
      {/* Menampilkan data yang telah di-fetch dalam format JSON */}
      <pre>{JSON.stringify(data, null, 2)}</pre>
    </div>
  );
}

export default DataFetcher; // Mengekspor komponen DataFetcher sebagai default export
