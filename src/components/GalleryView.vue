<template>
  <div class="container">
    <div class="grid">
        <div v-for="item in items" v-bind:key="item">{{item}}</div>
    </div>    
  </div>
</template>

<script>
export default {
    name: 'GalleryView',
    data: function() {
        return {
            items: ["Jeans", "Tshirt","Kurta","Blazer"]
        }
    }
}
</script>

<style scoped>
/* .grid {
    display: grid;
    grid-auto-columns: repeat(3, 1fr);
    grid-gap: 2vw;
}

.grid > div {
  font-size: 5vw;
  padding: .5em;
  background: gold;
  text-align: center;
} */
.grid { 
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  grid-gap: 20px;
  align-items: stretch;
  min-height: 600px;
  }
.grid div {
  border: 1px solid #ccc;
  box-shadow: 2px 2px 6px 0px  rgba(0,0,0,0.3);
  max-width: 100%;
  background-color: gold;
}
</style>