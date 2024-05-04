<template>
  <div>
    <!-- Teks Hello everyone berada di paling atas dan ditengah -->
    <h1 style="text-align: center; margin-top: 50px;">Hello everyone</h1>

    <!-- Elemen input teks -->
    <input v-model="inputText" placeholder="Masukkan teks di sini" style="margin-bottom: 30px;" />

    <!-- Dropdown untuk memilih warna -->
    <select v-model="selectedColor" style="margin-bottom: 25px;">
      <option value="black">Default (Hitam)</option>
      <option value="red">Merah</option>
      <option value="blue">Biru</option>
      <option value="green">Hijau</option>
    </select>

    <!-- Penggunaan class bindings dan style bindings -->
    <div :style="{ color: selectedColor, textAlign: 'center' }">
      {{ inputText }}
    </div>

    <!-- Interaksi dinamis dengan event listener -->
    <button @click="changeText" style="display: block; margin: 0 auto; margin-bottom: 20px;">Change Text to default</button>
    <button @click="sayHi" style="display: block; margin: 0 auto;">click</button> <!-- Tombol dipindahkan ke bawah -->
  </div>
</template>

<script>

export default {
  data() {
    return {
      inputText: '',
      dynamicText: 'Teks ini akan berubah!',
      selectedColor: 'black',
      colorMappings: {
        merah: 'red',
        biru: 'blue',
        hijau: 'green'
      }
    };
  },
  methods: {
    changeText() {
      if (this.inputText.toLowerCase() in this.colorMappings) {
        // Jika warna yang dimasukkan pengguna ada dalam mapping, gunakan warna tersebut
        this.selectedColor = this.colorMappings[this.inputText.toLowerCase()];
        this.dynamicText = `Teks telah diubah menjadi ${this.inputText.toLowerCase()}`;
      } else {
        // Jika tidak, kembalikan ke warna default
        this.selectedColor = 'black';
        this.dynamicText = 'Teks ini akan berubah!';
      }
    },
    sayHi() {
      alert("Hello,how are you doing today?");
      this.dynamicText = "Hi, selamat datang!";
    },
  },
}
</script>

<style scoped>
</style>
