<template>
  <div class="app">
    <!-- Elemen HTML yang berbeda -->
    <h1 :class="{ 'red-text': isRed }">Website Interaktif Vue</h1>
    <p v-if="showParagraph">Ini adalah sebuah paragraf.</p>
    
    <!-- Elemen input teks -->
    <input 
      type="text" 
      v-model="inputText" 
      placeholder="Masukkan teks"
      @keyup.enter="saveText"
    >
    
    <!-- Output yang menampilkan teks yang tersimpan -->
    <div v-for="(text, index) in savedTexts" :key="index">
      <p>{{ text }}</p>
      <button @click="deleteText(index)">Delete</button>
    </div>
    
    <!-- Output yang menampilkan teks yang sedang diketik secara real-time -->
    <p>{{ inputText }}</p>
    
    <!-- Elemen dengan class dan style bindings -->
    <div 
      :class="{ 'blue-box': isBlue }" 
      :style="{ fontSize: fontSize + 'px', border: borderStyle }"
    >
      Elemen dengan class dan style bindings
    </div>
    
    <!-- Tombol untuk mengubah data Vue -->
    <button @click="toggleColor">Ubah Warna</button>
    <button @click="toggleParagraph">Tampilkan/sembunyikan Paragraf</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isRed: false,
      showParagraph: true,
      inputText: '',
      isBlue: false,
      fontSize: 20,
      borderStyle: '1px solid black',
      savedTexts: [] // Menggunakan array untuk menyimpan output-output
    };
  },
  methods: {
    toggleColor() {
      this.isRed = !this.isRed;
    },
    toggleParagraph() {
      this.showParagraph = !this.showParagraph;
    },
    saveText() {
      if (this.inputText.trim() !== '') { // Menyimpan teks hanya jika tidak kosong
        this.savedTexts.push(this.inputText);
        this.inputText = ''; // Bersihkan input setelah disimpan
      }
    },
    deleteText(index) {
      this.savedTexts.splice(index, 1); // Menghapus teks dari array berdasarkan index
    }
  }
};
</script>

<style scoped>
.app {
  text-align: center;
  margin-top: 50px;
}

.red-text {
  color: red;
}

.blue-box {
  background-color: blue;
  color: white;
  padding: 10px;
}
</style>
