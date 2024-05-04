<template>
  <div class="background">
  <img src="https://wallpapercave.com/wp/wp2866857.jpg" />

  <div>
    <h1 :class="{ 'custom-class': true }">Login</h1>
    <input v-model="username" placeholder="Masukkan nama" :style="{ backgroundColor: inputBackground }" @input="updateInputBackground">
    <button @click="login" :class="{ 'btn-primary': true, 'btn-disabled': !username }">Login</button>
    <p v-if="loggedIn" :style="{ color: textColor }">Halo, {{ username }}!</p>
  </div>
</div>
</template>

<script>
import { ref } from 'vue';

export default {
  setup() {
    const username = ref('');
    const loggedIn = ref(false);
    const inputBackground = ref('#ffffff');
    const textColor = ref('#000000');

    const login = () => {

      if (username.value) {
        loggedIn.value = true;
        inputBackground.value = '#c8e6c9'; 
        textColor.value = '#1976d2'; 
      }
    }

    const updateInputBackground = () => {
      // Mengubah warna latar belakang input saat pengguna memasukkan teks
      inputBackground.value = '#007bff'; // Contoh pengaturan warna latar belakang input saat pengguna memasukkan teks
    }

    return { username, loggedIn, login, inputBackground, textColor, updateInputBackground };
  }
};
</script>

<style scoped>
/* Gaya tampilan halaman login */
h1 {
  font-size: 24px;
  margin-bottom: 16px;
}

input {
  padding: 8px;
  margin-bottom: 16px;
}

button {
  border: none;
  padding: 8px 16px;
  cursor: pointer;
}

.btn-primary {
  background-color: #007bff;
  color: #fff;
}

.btn-disabled {
  background-color: #ccc;
  cursor: not-allowed;
}

.custom-class {
  /* Gaya tambahan untuk judul */
}

.background img{
  position: fixed;
  top: 0;
  left: 0;
  min-height: 90%;
  min-width: 1500px;
  width: 100%;
  height: 100%;
  overflow: hidden;
  z-index: -2;
  object-fit: cover;
  -webkit-background-size:cover; -moz-background-size:cover; -o-background-size:cover; background-size: cover;
  filter: brightness(0.8);
}
</style>