<template>
  <header>
    <h1>Hello and Welcome to Vilhelms baltburgare</h1>

  </header>

  <main>
    <section id="Burger-selection">
      <h2>Select Your Burger</h2>
      <p>Choose from a large variety of tasty burgers, sides and drinks to fill your stomach and quench your
        thirst.<br>Psst, don't forget to order for a friend!</p>



      <div id="Burgerlist">

        <Burger v-for="burger in burgers" v-bind:burger="burger" v-bind:key="burger.name" />
      </div>
    </section>


    <section id="Customer-Information">
      <h2>Customer information</h2>
      <p> Provide your delivery address and other necessary details for your order below:</p>


      <section id="contact">
        <form>
          <p>
            <label for="fullname">Full name</label><br>
            <input type="text" id="fullname" v-model="fn" required="required" placeholder="First & Last Name">
          </p>
          <p>
            <label for="email">Email</label><br>
            <input type="text" id="email" v-model="em" required="required" placeholder="E-mail address">
          </p>
          <p>
            <label for="street">Street</label><br>
            <input type="text" id="street" v-model="st" required="required" placeholder="Street name">
          </p>
          <p>
            <label for="house">House</label><br>
            <input type="text" id="house" v-model="ho" required="required" placeholder="House number">
          </p>

          <p>
            <label for="payment-method">Payment method</label><br>
            <select select="select" v-model="slc">
              <option selected="selected">Card</option>
              <option>Swish</option>
              <option>Invoice</option>
              <option>Cash at delivery</option>
            </select>
          </p>

          <label for="gender">Gender</label><br>
          <label>
            <input type="radio" v-model="gender" value="male"> Male
          </label>

          <label>
            <input type="radio" v-model="gender" value="female" checked> Female
          </label>

          <label>
            <input type="radio" v-model="gender" value="not_specified"> Do not wish to provide
          </label>
        </form>
      </section>
    </section>
    <button name="data-form" type="submit" v-on:click="markDone">
      <img src="img/ordernow4.png" width="150" height="100">

    </button>
    <br><br>

  </main>

  <hr>

  <footer>
    <section id="Copyrights-And-Contact-Info">
      <h2>Contact info</h2>
      <p>To be announced...</p>
    </section>
    &COPY;
  </footer>
</template>

<script>
import Burger from '../components/OneBurger.vue'
import io from 'socket.io-client'
import menu from '../assets/menu.json'

const socket = io();

/*function MenuItem(nm, kc, url, la, gl){
  this.name = nm;
  this.kCal = kc;
  this.url = url;
  this.lactose = la;
  this.gluten = gl;
  }

 let allBurgers = [
  {name:"Burger 1",kCal:300,url:"img/burgare.jpeg",lactose:"Lactose-free",gluten:"Gluten-free"},
  {name: "Burger 2",kCal:400,url:"img/burgare2.jpeg",lactose:"Contains lactose",gluten:"Gluten-free"},
  {name: "Burger 3",kCal:500,url:"img/burgare3.jpeg",lactose:"Contains lactose",gluten:"Contains gluten"}];

console.log(allBurgers);*/

export default {
  name: 'HomeView',
  components: {
    Burger
  },
  data: function () {
    return {
      burgers: menu,
      fn: '',
      em: '',
      st: '',
      ho: '',
      slc: '',
      gender: '',

    }
  },
  methods: {
    markDone: function () {
      console.log(this.fn, this.em, this.st, this.ho, this.gender)
    },
    getOrderNumber: function () {
      return Math.floor(Math.random() * 100000);
    },
    addOrder: function (event) {
      var offset = {
        x: event.currentTarget.getBoundingClientRect().left,
        y: event.currentTarget.getBoundingClientRect().top
      };
      /*socket.emit("addOrder", {
        orderId: this.getOrderNumber(),
        details: {
          x: event.clientX - 10 - offset.x,
          y: event.clientY - 10 - offset.y
        },
        orderItems: ["Alicia", "Är bäst"]
      }
      );*/
    },
  }
}

</script>

<style>
/* För att kommentera kod */

@import 'https://fonts.googleapis.com/css?family=Pacifico|Dosis';

body {
  font-family: arial, sans-serif;
  font-size: 1em;
}

#Burger-selection {
  background-color: black;
  color: white;
  padding: 20px;
}

button {
  background-color: rgba(0, 0, 0, 0);
  border: 0;

}

button[type=submit]:hover {
  background-color: darkgray;
  cursor: pointer;
}

section[id=Burger-selection] {
  margin: 2em;
  border: 2px dotted;
  border-color: white;
}

#Burgerlist {
  display: grid;
  grid-template-columns: repeat(auto-fill, 20em);
  gap: 2em;
}

section[id=Customer-Information] {
  margin: 2em;
  border: 2px dotted;
  border-color: black;
  padding: 2em;
}

.Bilder {
  width: 300px;
  height: 200px;
}

.allergy {
  font-weight: bold;
}

header {
  background-image: url("../../public/img/header-image.jpeg");
  height: 7em;
  background-size: cover;
  background-color: rgba(0, 0, 0, 0.5);
  color: white;
  margin: 2em;
  padding-top: 1em;
  font-size: 1.5em;
  text-align: center;
}
</style>

