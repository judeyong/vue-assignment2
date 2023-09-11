<template>
  <dialog class="background" open>
    <div>
      <header>
        <h2>Error</h2>
        <base-button @click="closeBtnModal">close</base-button>
      </header>
      <p>input is not value</p>
    </div>
  </dialog>
</template>

<script>
import BaseButton from '../ui/BaseButton.vue';
export default {
  components: { BaseButton },
 emits: ['closeBtn'],

  methods: {
    closeBtnModal() {
      this.$emit('close-btn', false);
    }
  },
};
</script>
<style scoped>
.background {
  border-radius: 0;
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 10;
  background-color: rgba(0, 0, 0, 0.45);
}

div {
  position: absolute;
  top: 20vh;
  left: 30%;
  z-index: 100;
  width: 40%;
  height: 15rem;
  border: 1px solid black;
  border-radius: 12px;
  background-color: white;
}
header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  background-color: blueviolet;
  margin: 0;
  padding: 0.5rem;
  border-top-left-radius: 10px;
  border-top-right-radius: 10px;
}
h2 {
  margin: 0;
  color: white;
}
p {
  font-weight: bold;
  font-size: 2rem;
  padding: 0.5rem;
}
</style>
