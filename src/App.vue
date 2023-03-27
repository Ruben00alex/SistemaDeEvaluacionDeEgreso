<script setup>
import HelloWorld from "./components/HelloWorld.vue";

const handleFileUpload = (e) => {
  const file = e.target.files[0];
  const reader = new FileReader();
  reader.readAsDataURL(file);
  reader.onload = () => {
    console.log(reader.result);
  };
  reader.onerror = (error) => {
    console.log("Error: ", error);
  };
};
</script>

<template>
  <div>
    <h1>hola</h1>
    <p>ingrese un nuevo archivo:</p>
    <input
      type="file"
      id="file"
      name="file"
      accept=".pdf"
      @change="handleFileUpload"
    />
    <button @click="uploadFile">Subir</button>
  </div>

  <!-- pdf viewer of the loaded file -->
  <div class="pdf-container">
    <pdf
      v-if="pdf"
      :src="pdf"
      
    />
  </div>

  

  

</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
