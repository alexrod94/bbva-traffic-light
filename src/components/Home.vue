<template>
  <div>
    <section
      class="header flex flex-row justify-between items-center bg-slate-200 py-3 px-5"
    >
      <h4 class="text-md">Hi {{ user }}</h4>
      <svg
        class="w-4 h-4"
        fill="none"
        stroke="currentColor"
        viewBox="0 0 24 24"
        xmlns="http://www.w3.org/2000/svg"
        @click="logout"
      >
        <path
          stroke-linecap="round"
          stroke-linejoin="round"
          stroke-width="2"
          d="M17 16l4-4m0 0l-4-4m4 4H7m6 4v1a3 3 0 01-3 3H6a3 3 0 01-3-3V7a3 3 0 013-3h4a3 3 0 013 3v1"
        ></path>
      </svg>
    </section>
    <section class="mt-10 flex flex-col items-center justify-center">
      <h2 class="text-lg">Highest Score: {{ highScore }}</h2>
      <TrafficLight class="mt-10" :color="trafficColor" />
    </section>
  </div>
</template>

<script>
import TrafficLight from "./TrafficLight.vue";
export default {
  components: {
    TrafficLight,
  },
  data() {
    return {
      user: "",
      currentScore: 0,
      highScore: 0,
      trafficLight: "green",
      trafficColor: "fill-green-500",
      lastStep: "",
      currentStep: "",
    };
  },
  mounted() {
    this.user = localStorage.getItem("user");
  },
  methods: {
    logout() {
      localStorage.removeItem("user");
      this.$router.push("/login");
    },
  },
};
</script>

<style></style>
