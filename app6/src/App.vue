<script setup>
import { reactive, ref } from 'vue'

const order = reactive({
  name: {
    first: "",
    last: ""
  },
  email: "",
  size: "",
  quantity: "",
  deliveryDate: "",
  address: {
    streetAddr: "",
    streetAddr2: "",
    city: "",
    zip: ""
  }
})

function purchase() {
  console.log("User data:")

  let jsonString = JSON.stringify(order)

  let jsonObject = JSON.parse(jsonString)
  console.log(jsonObject);
}

const asterisk = ref("*");
</script>

<template>
  <div class="background">
    <h2>Order Form</h2>
    <p>Please fill in your information and we'll be sending your order in no time.</p>
    <div class="info">
      <form id="form">

        <label for="firstName">Name *</label>
        <input type="text" id="firstName" name="firstName" v-model="order.name.first" placeholder="First Name" required>
        <input type="text" id="lastName" name="lastName" v-model="order.name.last" placeholder="Last Name" required>

        <div id="email-div">
          <label for="email">Email *</label>
          <input type="text" id="email" name="email" v-model="order.email" placeholder="example@gmail.com" required>
        </div>

        <label for="shirt1">T-shirt model *</label>

        <div id="shirts">
          <input type="radio" id="shirt1" name="shirt" value="shirt1" required>
          <img src="/collared-shirt.png" id="collared-shirt">
          <input type="radio" id="shirt2" name="shirt" value="shirt2" required>
          <img src="/long-sleeve.png" id="long-sleeve">
          <input type="radio" id="shirt3" name="shirt" value="shirt3" required>
          <img src="/t-shirt.png" id="t-shirt">
        </div>

        <div id="specifics">
          <div id="shirt-div">
            <label for="size">Size</label>
            <input list="shirt-sizes" name="sizes" id="sizes" v-model="order.size" required>

            <datalist id="shirt-sizes">
              <option value="XS"></option>
              <option value="S"></option>
              <option value="M"></option>
              <option value="L"></option>
              <option value="XL"></option>
            </datalist>
          </div>

          <label for="quantity" name="quantity">Quantity *</label>
          <input type="text" id="quantity" name="quantity" v-model="order.quantity" required>

          <div id="date-div">
            <label for="deliveryDate" name="deliveryDate">Delivery Date *</label>
            <input type="text" id="deliveryDate" name="delivDate" placeholder="01/01/2023" v-model="order.deliveryDate"
              required>
          </div>
        </div>

        <div id="delivAddress">
          <label for="street1" name="delivAddr">Delivery Address</label>
          <div id="addrInputs">
            <input type="text" id="street1" name="street1" placeholder="Street Address"
              v-model="order.address.streetAddr" required><br>
            <input type="text" id="street2" name="street2" placeholder="Street Address Line 2"
              v-model="order.address.streetAddr2"><br>
            <input type="text" id="city" name="city" placeholder="City" v-model="order.address.city" required><br>
            <input type="text" id="zip" name="zip" placeholder="Postal / Zip Code" v-model="order.address.zip" required>
          </div>
        </div>
        <button id="purchase" class="btn" type="button" @click="purchase">Purchase</button>
      </form>
    </div>
  </div>
</template>

<style>
.background {
  position: relative;
  font-family: sans-serif;
  background-color: rgba(41, 174, 41, 0.884);
  margin: 20px;
  border: 1px solid lightgrey;
  border-radius: 17px;
  width: 750px;
  left: 40px;
}

.background h2 {
  color: white;
  padding-left: 45px;
  padding-top: 10px;
}

.info label {
  margin-left: 60px;
}

.background p {
  color: white;
  padding-left: 45px;
}

input {
  margin: 5px;
  margin: 10px;
  padding: 4px;
}

label {
  margin-left: 20px;

}

#shirt1 {
  margin-left: 210px;
}

#shirt2 {
  margin-left: -15px;
}

#shirt3 {
  margin-left: 20px;
}

#purchase {
  position: relative;
  background-color: rgba(41, 174, 41, 0.884);
  border-color: rgba(41, 174, 41, 0.884);
  border-radius: 2px;
  color: white;
  bottom: -55px;
  left: 640px;
  scale: 1.5;
  font-size: 10px;
  padding: 8px;
  width: 80px;
}

.info {
  background-color: white;
}

#delivAddress label {
  position: relative;
  top: 5px;
  margin-left: 10px;
}

#delivAddress {
  position: relative;
  background-color: rgb(236, 236, 236);
  width: 610px;
  left: 50px;
  height: 185px;
}

#delivAddress input {
  position: relative;
  left: 150px;
  bottom: 20px;
}

#collared-shirt {
  position: relative;
  width: 130px;
  left: -30px;
}

#street1 {
  width: 430px;
}

#street2 {
  width: 430px;
}

#long-sleeve {
  width: 90px;
  margin-left: 8px;
}

#t-shirt {
  width: 100px;
}

img {
  scale: .8
}

#quantity {
  position: relative;
  left: 70px;
}

#sizes {
  position: relative;
  left: 110px;
}

#deliveryDate {
  position: relative;
  left: 34px;
}

#email {
  position: relative;
  left: 87px;
}

#lastName {
  position: relative;
  left: 87px;
}

#firstName {
  position: relative;
  left: 84px;
}

</style>
