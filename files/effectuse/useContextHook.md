import React, { useContext } from 'react';

// Membuat Context bernama ThemeContext dengan nilai default 'light'
const ThemeContext = React.createContext('light');

function ThemedComponent() {
  // Menggunakan useContext untuk mengakses nilai dari ThemeContext
  const theme = useContext(ThemeContext);

  // Menentukan gaya berdasarkan nilai tema yang didapat dari context
  const style = {
    backgroundColor: theme === 'light' ? '#fff' : '#333', // Warna latar belakang berdasarkan tema
    color: theme === 'light' ? '#000' : '#fff', // Warna teks berdasarkan tema
    padding: '10px',
    textAlign: 'center'
  };

  return (
    <div style={style}>
      Tema saat ini: {theme} {/* Menampilkan tema yang sedang digunakan */}
    </div>
  );
}

function App() {
  return (
    // Menyediakan nilai 'dark' untuk ThemeContext, menggantikan nilai default 'light'
    <ThemeContext.Provider value="dark">
      <ThemedComponent /> {/* Menggunakan komponen yang menerima tema dari context */}
    </ThemeContext.Provider>
  );
}

export default App; // Mengekspor komponen App sebagai default export
