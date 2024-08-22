import React, { useRef } from 'react';

function FocusInput() {
  // Membuat ref dengan useRef yang akan di-attach ke elemen input
  const inputRef = useRef(null);

  // Fungsi untuk memfokuskan input ketika tombol ditekan
  const focusInput = () => {
    inputRef.current.focus(); // Memfokuskan input menggunakan ref
  };

  return (
    <div>
      {/* Menghubungkan ref dengan elemen input */}
      <input ref={inputRef} type="text" />
      {/* Menambahkan event handler onClick untuk fokus pada input */}
      <button onClick={focusInput}>Fokuskan Input</button>
    </div>
  );
}

export default FocusInput; // Mengekspor komponen FocusInput sebagai default export
