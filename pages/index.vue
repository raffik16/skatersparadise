<template>
  <!-- Main Parent Index Div -->
  <div class="main-parent">
    <header class="header-wrap">
      <!-- Import hero header -->
      <!-- <hero-header /> -->
    </header>

    <div
      class=""
      @click="
        toggleClass();
        startOllie();
      "
    >
      skate!
    </div>

    <div :class="['board-meta', { rolling: isActive }]">
      <img :class="['board', { olling: ollie }]" src="~/assets/board.png" />
    </div>

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
      isActive: false,
      ollie: false
    };
  },
  methods: {
    toggleClass() {
      this.isActive = !this.isActive;
    },
    startOllie() {
      this.ollie = true;
      this.endOllie();
    },
    endOllie() {
      setTimeout(
        function() {
          this.ollie = false;
        }.bind(this),
        1500
      );
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

  .board-meta {
    transition: all 2.5s ease-in-out;
    transform: translate(0);
    position: absolute;

    bottom: 0;
    left: 0;

    &.rolling {
      transform: translateX(calc(100vw - 200px));
    }
  }

  .board {
    max-width: 200px;

    &.olling {
      animation: ollie 1.5s forwards ease-in-out;
    }

    @keyframes ollie {
      0% {
        transform: rotate(0) translateY(0);
      }
      25% {
        transform: rotate(0) translateY(0);
      }
      50% {
        transform: rotate(-30deg) translateY(0);
      }
      75% {
        transform: rotate(20deg) translateY(-200px);
      }
      100% {
        transform: rotate(0) translateY(-1px);
      }
    }
  }
}
</style>
