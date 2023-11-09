<template>
  <div>
    <article>
      <h3>{{ burger.name }}</h3>
      <img class="Bilder" v-bind:src="burger.url">

      <h4>Information</h4>
      <ol>
        <li>Choose toppings</li>
        <li>Choose side</li>
        <li>Choose drink</li>
      </ol>

      <ul>
        <li>{{ burger.kCal }} kCal</li>
        <li>{{ burger.lactose }}</li>
        <li>{{ burger.gluten }}</li>
        
      </ul>


    </article>
  </div>
</template>

<script>
export default {
  name: 'OneBurger',
  props: {
    burger: Object
  }
}

</script>
  
  <!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.Bilder {
  width: 300px;
  height: 200px;
}

.allergy {
  font-weight: bold;
}
</style>
  