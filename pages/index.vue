<template>
  <div :class="{ 'dark-mode': isDarkMode }" @mousemove="handleMouseMove">
    <div class="lamp-effect" :style="{ top: `${lampPosition.y}px`, left: `${lampPosition.x}px` }"></div>

    <div class="h-screen flex justify-start items-end p-10">
      <nuxt-link to="/bday">
        <button @click="toggleMode" class="relative px-4 py-2 bg-black text-black rounded-3xl font-mono hover:bg-red-200 hover:text-black">Nyalakan Untuk 18th!!</button>
      </nuxt-link>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isDarkMode: true,
      lampPosition: { x: 0, y: 0 },
    };
  },
  methods: {
    toggleMode() {
      this.isDarkMode = !this.isDarkMode;
    },
    handleMouseMove(event) {
      if (this.isDarkMode) {
        this.lampPosition.x = event.pageX;
        this.lampPosition.y = event.pageY;
      }
    },
  },
};
</script>

<style scoped>
.dark-mode {
  background-color: black;
  color: white;
}

.lamp-effect {
  background: radial-gradient(circle, rgba(255, 255, 255, 0.528) 5%, transparent 70%);
  pointer-events: none;
  position: fixed;
  width: 150px;
  height: 150px;
  border-radius: 50%;
  transform: translate(-50%, -50%);
  z-index: 10;
  display: none;
}

.dark-mode .lamp-effect {
  display: block;
}
</style>
