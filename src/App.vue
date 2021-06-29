<template>
  <div id="app">
    <div class="container">
      <div>
        <Navbar />  
      </div>
      <div class="py-4">
        <UploadImage />
      </div>
      <hr/>
      <div>
        <GalleryView />
      </div>
    </div>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import Navbar from './components/Navbar.vue'
import UploadImage from './components/UploadImage.vue'
import GalleryView from './components/GalleryView.vue'

export default {
  name: 'App',
  components: {
    // HelloWorld,
    Navbar,
    UploadImage,
    GalleryView
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

</style>
