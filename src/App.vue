<template>
  <div class="container d-flex align-items-center justify-content-center" style="height: 100vh;">
    <div>
      <h1>{{ pageTitle }}</h1>
      <div class="form-group">
        <label for="textInput">Masukkan Teks:</label>
        <input type="text" class="form-control" id="textInput" v-model="inputText" @input="handleChange">
      </div>
      <div class="form-group">
        <label for="textLength">Panjang Teks:</label>
        <p id="textLength">{{ inputText.length }}</p>
      </div>
      <div :class="{ 'alert': showAlert, 'alert-danger': isError, 'alert-success': !isError }" role="alert">
        {{ alertMessage }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      pageTitle: 'Halaman Web Sederhana',
      inputText: '',
      isError: false,
      alertMessage: '',
      showAlert: false
    };
  },
  methods: {
    handleChange() {
      // Menghitung panjang teks
      const textLength = this.inputText.length;

      // Mengubah pesan alert berdasarkan panjang teks
      if (textLength === 0) {
        this.alertMessage = 'Teks tidak boleh kosong!';
        this.isError = true;
        this.showAlert = true;
      } else if (textLength <= 5) {
        this.alertMessage = 'Teks terlalu pendek!';
        this.isError = true;
        this.showAlert = true;
      } else if (textLength >= 20) {
        this.alertMessage = 'Teks terlalu panjang!';
        this.isError = true;
        this.showAlert = true;
      } else {
        this.showAlert = false;
      }
    }
  }
};
</script>

<style scoped>
.container {
  text-align: center;
}
</style>
