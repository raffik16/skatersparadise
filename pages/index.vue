<template>
  <!-- Main Parent Index Div -->
  <div class="main-parent">
    <header class="header-wrap">
      <!-- Import hero header -->
      <!-- <hero-header /> -->
    </header>

    <div class="" @click="toggleClass">
      skate!
    </div>

    <img
      class="board"
      src="~/assets/board.png"
      :class="['board', { box: isActive }]"
    />

    <!-- Import hero images + titles -->

    <!-- <posts /> -->

    <!-- <footer-cmp /> -->

    <!-- <footer class="footer-wrap"></footer> -->
  </div>
</template>

<script>
export default {
  head() {
    return {
      title: "Welcome to Skaters Paradise",
      meta: [
        {
          hid: "description", //  Must use hid
          name: "description", // Type of meta property
          content: "Welcome to Skaters Paradise" // Insert description from API
        }
      ]
    };
  },
  data() {
    return {
      isActive: false
    };
  },
  methods: {
    toggleClass() {
      this.isActive = !this.isActive;
    }
  }
};
</script>

<style scoped lang="scss">
.main-parent {
  display: flex;
  height: 100vh;
  flex-direction: column;
  align-items: center;
  justify-content: center;

  .board {
    max-width: 200px;

    transition: all 0.4 ease-in-out;

    align-self: flex-end;
  }
}
</style>
