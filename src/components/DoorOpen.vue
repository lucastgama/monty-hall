<template>
  <div class="door-area">
    <div class="door-frame" :class="{ selected: selected && !open }">
      <GiftComponent v-if="open && hasGift" />
    </div>
    <div class="door" :class="{ open }" @click="selected = !selected">
      <div class="number" :class="{ selected }">{{ number }}</div>
      <div class="knoob" :class="{ selected }" @click="open = true"></div>
    </div>
  </div>
</template>

<script>
import GiftComponent from "./GiftComponent.vue";

export default {
  name: "DoorSelected",
  components: { GiftComponent },
  props: {
    number: {},
    hasGift: { type: Boolean },
  },
  data: function () {
    return {
      open: false,
      selected: false,
    };
  },
};
</script>
<style>
* {
  box-sizing: border-box;
}
.door-area {
  position: relative;
  width: 200px;
  height: 310px;
  border-bottom: 10px solid #aaa;
  margin-bottom: 20px;
  font-size: 3rem;

  display: flex;
  justify-content: center;
}

.door-frame {
  position: absolute;
  height: 300px;
  width: 180px;
  border-left: 3px solid brown;
  border-right: 3px solid brown;
  border-top: 3px solid brown;
  display: flex;
  align-items: flex-end;
  justify-content: center;
}
.door {
  position: absolute;
  top: 5px;
  height: 295px;
  width: 170px;
  background-color: chocolate;
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 20px;
}
.door .knoob {
  height: 20px;
  width: 20px;
  border-radius: 10px;
  background-color: brown;
  align-self: flex-start;
  margin-top: 60px;
}
.door-frame.selected {
  border-left: 3px solid goldenrod;
  border-right: 3px solid goldenrod;
  border-top: 3px solid goldenrod;
}
.door .number.selected {
  color: goldenrod;
}
.door .knoob.selected {
  background-color: goldenrod;
}
.door.open {
  background-color: #0007;
}
.door.open .knoob {
  display: none;
}
.door.open .number {
  display: none;
}
</style>
