import React, { useState, useEffect } from 'react';

// Custom Hook untuk fetch data
function useFetch(url) {
  // State untuk menyimpan data yang di-fetch dan status loading
  const [data, setData] = useState(null); // State untuk menyimpan data
  const [loading, setLoading] = useState(true); // State untuk mengindikasikan status loading

  useEffect(() => {
    fetch(url) // Melakukan fetch data dari URL yang diberikan
      .then(response => response.json()) // Mengonversi response menjadi JSON
      .then(data => {
        setData(data); // Menyimpan data ke state
        setLoading(false); // Mengatur loading ke false setelah data berhasil di-fetch
      });
  }, [url]); // Array dependency berisi 'url' agar fetch dijalankan setiap kali 'url' berubah

  return { data, loading }; // Mengembalikan data dan status loading dari custom hook
}

function App() {
  // Menggunakan custom hook useFetch untuk fetch data dari API
  const { data, loading } = useFetch('https://api.example.com/data');

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

export default App; // Mengekspor komponen App sebagai default export
