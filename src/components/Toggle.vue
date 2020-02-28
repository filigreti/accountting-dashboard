<template id="toggle">
  <main>
    <div v-if="toggled == 0" class="not-toggle">
      <svg
        class="switch"
        width="60"
        height="32"
        viewBox="0 0 60 32"
        fill="none"
        xmlns="http://www.w3.org/2000/svg"
      >
        <path
          opacity="0.05"
          d="M44 0H16C7.16344 0 0 7.16344 0 16C0 24.8366 7.16344 32 16 32H44C52.8366 32 60 24.8366 60 16C60 7.16344 52.8366 0 44 0Z"
          fill="black"
        />
        <path
          d="M43 29C50.1797 29 56 23.1797 56 16C56 8.8203 50.1797 3 43 3C35.8203 3 30 8.8203 30 16C30 23.1797 35.8203 29 43 29Z"
          fill="white"
        />
      </svg>
    </div>
    <div v-else class="toggle">
      <svg
        class="switch"
        width="60"
        height="32"
        viewBox="0 0 60 32"
        fill="none"
        xmlns="http://www.w3.org/2000/svg"
      >
        <path
          d="M44 0H16C7.16344 0 0 7.16344 0 16C0 24.8366 7.16344 32 16 32H44C52.8366 32 60 24.8366 60 16C60 7.16344 52.8366 0 44 0Z"
          fill="#43424B"
          stroke="1"
        />
        <path
          d="M18 29C25.1797 29 31 23.1797 31 16C31 8.8203 25.1797 3 18 3C10.8203 3 5 8.8203 5 16C5 23.1797 10.8203 29 18 29Z"
          fill="white"
        />
      </svg>
    </div>
    <!-- <span
      class="fa toggle"
      v-bind:class="{'fa-toggle-on': toggled, 'fa-toggle-off': !toggled, 'text-success': toggled, 'text-muted': !toggled}"
      @click="toggled = !toggled"
    ></span>-->
  </main>
</template>

<script>
export default {
  props: ['toggled']
};
</script>
<style scoped>
.switch {
  width: 40px;
}
</style>
