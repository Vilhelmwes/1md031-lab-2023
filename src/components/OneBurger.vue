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

      <ul>{{ burger.kCal }} kCal</ul> 
      <ul class="allergy">
        
        <li v-if="!burger.lactose">Lactose-free!</li>
        <li v-if="!burger.gluten">Gluten-free!</li>
      </ul>


      

      <div>
        <p>Amount Ordered: {{ amountOrdered }}</p>
        <button name="Increase" type="submit" v-on:click="increaseOrder">Increase</button>
        <button name="Decrease" type="submit" v-on:click="decreaseOrder">Decrease</button>
        <button name="addBurger" type="submit" v-on:click="addBurger">Add to order</button>
      </div>


    </article>
  </div>
</template>

<script>
export default {
  name: 'OneBurger',
  props: {
    burger: Object
  },
  data: function () {
    return {
      amountOrdered: 0,
    };
  },
  methods: {
    increaseOrder: function () {
      this.amountOrdered += 1;
    },
    decreaseOrder: function () {
      if (this.amountOrdered > 0) {
        this.amountOrdered -= 1;
      }
    },
    addBurger: function () {
      this.$emit('orderedBurger', {
        name: this.burger.name,
        amount: this.amountOrdered
      }
      );

    }
  }
};

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

button {
  background-color: black;
  color: white;
  padding:0.5em;
  margin:0.2em;
  font-weight:bold;

}
</style>
  