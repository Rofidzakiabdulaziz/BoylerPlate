import React, { useReducer } from 'react';

// Mendefinisikan fungsi reducer untuk mengelola state
// Reducer ini menerima state saat ini dan sebuah action, lalu mengembalikan state baru
function reducer(state, action) {
  switch (action.type) {
    case 'increment': // Jika action.type adalah 'increment'
      return { count: state.count + 1 }; // Tambahkan 1 ke state.count
    case 'decrement': // Jika action.type adalah 'decrement'
      return { count: state.count - 1 }; // Kurangi 1 dari state.count
    default:
      throw new Error(); // Lempar error jika action.type tidak dikenal
  }
}

function Counter() {
  // Menggunakan useReducer untuk mendefinisikan state 'count' dan dispatch function
  // 'state' adalah state saat ini, dan 'dispatch' digunakan untuk mengirim action ke reducer
  const [state, dispatch] = useReducer(reducer, { count: 0 }); // State awal 'count' adalah 0

  return (
    <div>
      <h1>Hitungan: {state.count}</h1> {/* Menampilkan nilai count */}
      {/* Dispatch action 'increment' untuk menambah count */}
      <button onClick={() => dispatch({ type: 'increment' })}>Tambah</button>
      {/* Dispatch action 'decrement' untuk mengurangi count */}
      <button onClick={() => dispatch({ type: 'decrement' })}>Kurangi</button>
    </div>
  );
}

export default Counter; // Mengekspor komponen Counter sebagai default export
