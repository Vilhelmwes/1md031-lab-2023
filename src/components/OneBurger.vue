<template>
  <div>
    <article>
          <h3>{{ burger.name }} {{ burger.kCal }}</h3>
          <img class="Bilder" src="img/burgare.jpeg">


          <div id="BaltBurger-information">
            <h4>Information</h4>
            <ol>
              <li>Choose toppings</li>
              <li>Choose side</li>
              <li>Choose drink</li>
            </ol>

            <ul>
              <li><span class="allergy"> Gluten-free</span></li>
              <li> 100% <span class="allergy"> Swedish Ingredients</span></li>
              <li> May contain<span class="allergy"> nuts</span></li>
              <dd>...ask the staff if you're unsure</dd>
            </ul>

          </div>
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
  