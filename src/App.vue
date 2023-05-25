<template>
  <div id="app">
    <h1>Problema Monty Hall</h1>
    <div class="form">
      <div v-if="!started">
        <label for="portsAmount">Quantas portas ?</label>
        <input
          type="text"
          size="3"
          id="portsAmount"
          v-model.number="portsAmount"
        />
      </div>
      <div v-if="!started">
        <label for="selectedPort"> Qual é a porta premiada ?</label>
        <input
          type="text"
          id="selectedPort"
          size="3"
          v-model.number="selectedPort"
        />
      </div>
      <button v-if="!started" @click="started = true">Iniciar</button>
      <button v-if="started" @click="started = false">Reiniciar</button>
    </div>
    <div class="doors" v-if="started">
      <div v-for="i in portsAmount" :key="i">
        <DoorSelected :hasGift="i === selectedPort" :number="i" />
      </div>
    </div>
  </div>
</template>

<script>
import DoorSelected from "./components/DoorOpen.vue";
export default {
  name: "App",
  components: {
    DoorSelected,
  },
  data: function () {
    return {
      started: false,
      portsAmount: 3,
      selectedPort: null,
    };
  },
};
</script>

<style>
* {
  box-sizing: border-box;
}
body {
  color: #fff;
  background: linear-gradient(to right, rgba(21, 153, 87), rgba(21, 87, 153));
}
#app {
  display: flex;
  flex-direction: column;
  align-items: center;
}
#app h1 {
  border: 1px solid #111;
  background-color: #1114;
  padding: 20px;
  margin-bottom: 60px;
}
.form {
  display: flex;
  flex-direction: column;
  justify-self: center;
  align-items: center;
  margin-bottom: 40px;
}
.form,
.form input,
.form button {
  margin-bottom: 10px;
  font-size: 2rem;
}
.doors {
  align-self: stretch;
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
}
</style>
