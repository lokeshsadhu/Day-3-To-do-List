<template>
  <div>
    <h1>Shopping List with Important items</h1>
    <form v-on:submit.prevent="addItem" class="form">
      <div>
        <label for="input" class="label">Enter Item :</label>
        <input id="input" type="text" v-model="name" placeholder="Enter text"/>
      </div>
      <div>
        <label for="input" class="label">Enter Quantity :</label>
        <input id="input" type="number" v-model="number" placeholder="Enter number"/>
      </div>
      <div>
        <label for="input" class="label">Important ? :</label>
        <input id="input" type="checkbox" v-model="check" placeholder="Enter number"/>
      </div>
      <div>
        <button type="submit">Add Item</button>
      </div>
    </form>
  </div>
  <div>
    <h1>Shopping Items List</h1>
    <ul class="list">
      <li  v-for="i in items" v-bind:class="{ impClass: i.important }">
        <h3>{{i.item}} : {{ i.quantity }} - {{ i.important }}</h3>
      </li>
    </ul>
  </div>
</template>

<script setup>
import {ref,reactive} from "vue"

const name=ref("")
const number=ref("")
const check=ref(false)
const items=reactive([{item:"Apple",quantity:5,important:false}])


const addItem=()=>{
  let item = {
          item: name.value,
          quantity: number.value,
          important: check.value
        }
  items.push(item)
  console.log(items)
}
</script>

<style>Enter
.form{
  display: flex;
  flex-direction: column;
}
#input{
  margin-left: 8px;
}
.label{
  font-size: 20px;
}
.list{
  display: flex;
  flex-direction: column;
}
.impClass {
  background-color: rgb(255, 202, 202);
  font-weight: bold;
}
</style>