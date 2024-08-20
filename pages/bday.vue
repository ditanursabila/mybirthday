<template>
  <div class="relative bg-gradient-to-r from-pink-500 to-blue-500 p-10 h-screen overflow-hidden">
    <div>
      <h1 class="text-5xl font-extrabold text-center bg-gradient-to-br from-cyan-400 to-neutral-100 bg-clip-text text-transparent tracking-widest">Happy Birthday</h1>
      <h1 class="text-4xl mt-5 font-bold text-center  text-white tracking-wider">DITA NUR SABILA</h1>
      <div class="flex items-center justify-center">
        <div class="rounded-full w-[450px] md:h-[450px] my-16  h-[300px]"> 

          <img class="w-full h-full  bg-center object-cover rounded-full hover:scale-105 border-2 border-pink-300 hover:transition duration-300" src="assets/img/dita.jpeg" alt="foto" />
        </div>
      </div>
      <h2 class="text-center text-neutral-100 font-medium mt-3 text-balance">
        "Happy Birthday to me! Here's to a new chapter filled with hope, dreams, and endless possibilities. I embrace every step forward and trust that happiness is on the horizon. This year, I choose courage, joy, and self-belief."
      </h2>
      <h1 class="text-2xl mt-5 font-semibold text-center bg-gradient-to-br from-cyan-400 to-neutral-100 bg-clip-text text-transparent">23 AGUSTUS 2006</h1>
    </div>
    <div v-for="balloon in balloons" :key="balloon.id" :style="balloon.style" class="balloon-container">
      <div class="balloon" :style="{ width: balloon.style.width, height: balloon.style.height, backgroundColor: balloon.color }"></div>
      <svg class="string" viewBox="0 0 100 100">
        <path d="M50,0 Q60,20 50,40 Q40,60 50,80 Q60,100 50,120" stroke="currentColor" fill="transparent" />
      </svg>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      balloons: [],
    };
  },
  created() {
    this.generateBalloons();
  },
  methods: {
    generateBalloons() {
      const colors = [
        "rgba(255, 87, 51, 0.7)", // Red
        "rgba(51, 255, 87, 0.7)", // Green
        "rgba(51, 87, 255, 0.7)", // Blue
        "rgba(241, 196, 15, 0.7)", // Yellow
        "rgba(155, 89, 182, 0.7)", // Purple
        "rgba(230, 126, 34, 0.7)", // Orange
        "rgba(46, 204, 113, 0.7)", // Light Green
        "rgba(52, 152, 219, 0.7)", // Light Blue
      ];

      const balloonWidth = "90px"; // Lebar balon tetap
      const balloonHeight = "100px"; // Tinggi balon tetap (rasio 1:1.5 untuk elips)

      for (let i = 0; i < 10; i++) {
        const delay = Math.random() * 5 + "s";
        const duration = Math.random() * 5 + 5 + "s";
        const left = Math.random() * 100 + "%";

        const color = colors[Math.floor(Math.random() * colors.length)];

        this.balloons.push({
          id: i,
          style: {
            left,
            animationDelay: delay,
            animationDuration: duration,
            width: balloonWidth,
            height: balloonHeight,
          },
          color,
        });
      }
    },
  },
};
</script>
<style>
@import url('https://fonts.googleapis.com/css2?family=Marcellus+SC&display=swap');
body{
  font-family: 'Marcellus SC', serif;
}
</style>
<style scoped>
.balloon-container {
  @apply absolute bottom-0 flex flex-col items-center;
  animation: flyUp infinite ease-in;
}

/* Balon berbentuk elips */
.balloon {
  @apply rounded-full;
  background: linear-gradient(145deg, rgba(255, 255, 255, 0.5), rgba(0, 0, 0, 0.2)); /* Kilauan dan bayangan */
  box-shadow: inset -10px -10px 20px rgba(0, 0, 0, 0.2), inset 10px 10px 20px rgba(255, 255, 255, 0.3), 10px 10px 20px rgba(0, 0, 0, 0.2); /* Bayangan untuk memberikan kedalaman */
  position: relative;
}

/* Tali balon */
.string {
  @apply bg-gray-700 absolute w-0.5;
  height: 80%; /* Panjang tali */
  margin-top: 100px; /* Menghubungkan tali ke balon */
  /* animation: spiral 5s infinite linear; */
  transform-origin: center bottom;
}

/* Animasi tali balon */
@keyframes spiral {
  0% {
    transform: translateY(0) rotate(0deg);
  }
  100% {
    transform: translateY(100vh) rotate(720deg); /* Menambahkan rotasi */
  }
}

@keyframes flyUp {
  0% {
    transform: translateY(0);
  }
  100% {
    transform: translateY(-100vh);
  }
}
</style>
