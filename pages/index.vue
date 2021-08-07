<template>
  <!-- Main Parent Index Div -->
  <div class="main-parent">
    <h1>
      Skateboarding with CSS
    </h1>
    <p>
      First pick your style, then your trick!
    </p>
    <p>
      This was designed for those who want to just throw some tricks but cant
      due to whatever your situtation is. Push some buttons and land some
      tricks.
    </p>
    <p>
      Submit your own tricks @
      <a target="_blank" href="https://github.com/raffik16/skatersparadise"
        ><b>GitHub</b></a
      >
    </p>
    <div class="menu">
      <button
        class="menu-item"
        :disabled="rollingForward || rollingBack"
        @click="
          tricks = !tricks;
          railTricks = false;
          rail = false;
        "
      >
        traditional tricks
      </button>

      <button
        class="menu-item"
        :disabled="rollingForward || rollingBack"
        @click="
          railTricks = !railTricks;
          tricks = false;
        "
      >
        rail tricks
      </button>

      ...

      <button
        class="menu-item"
        :disabled="rollingForward || rollingBack"
        v-if="tricks"
        @click="
          toggleRoll();
          startOllie();
        "
      >
        ollie
      </button>

      <button
        class="menu-item"
        :disabled="rollingForward || rollingBack"
        v-if="tricks"
        @click="
          toggleRoll();
          startKickflip();
        "
      >
        kickflip
      </button>

      <button
        class="menu-item"
        :disabled="rollingForward || rollingBack"
        v-if="tricks"
        @click="
          toggleRoll();
          startHardFlip();
        "
      >
        hardflip
      </button>

      <button
        class="menu-item"
        :disabled="rollingForward || rollingBack"
        v-if="tricks"
        @click="
          toggleRoll();
          startThreeSixtyFlip();
        "
      >
        360 Flip
      </button>

      <button
        class="menu-item"
        :disabled="rollingForward || rollingBack"
        v-if="railTricks"
        @click="
          toggleRoll();
          startFiveO();
        "
      >
        5-0
      </button>

      <button
        class="menu-item"
        :disabled="rollingForward || rollingBack"
        v-if="railTricks"
        @click="
          toggleRoll();
          startKickflipNoseGrind();
        "
      >
        Kickflip Nose Grind
      </button>
    </div>

    <div :class="['board-meta', { rolling: rollingForward }]">
      <img :class="classes" src="~/assets/board.png" />
    </div>

    <div class="rail" v-if="railTricks" />
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
      rollingBack: false,
      tricks: false,
      railTricks: false,
      rollingForward: false,
      ollie: false,
      kickflip: false,
      hardflip: false,
      fiveO: false,
      threeSixtyFlip: false,
      kickflipNoseGrind: false
    };
  },
  computed: {
    classes() {
      return [
        "board",
        { olling: this.ollie },
        { kickfliping: this.kickflip },
        { hardlfliping: this.hardflip },
        { fiveo: this.fiveO },
        { threesixtyflip: this.threeSixtyFlip },
        { kickflipnosegrind: this.kickflipNoseGrind }
      ];
    }
  },
  methods: {
    toggleRoll() {
      this.rollingForward = true;

      setTimeout(
        function() {
          this.rollingForward = false;
          this.rollingBack = true;
          this.rollBack();
        }.bind(this),
        2500
      );
    },

    rollBack() {
      setTimeout(
        function() {
          this.rollingBack = false;
        }.bind(this),
        2500
      );
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
    },

    startKickflip() {
      this.kickflip = true;
      this.endKickflip();
    },
    endKickflip() {
      setTimeout(
        function() {
          this.kickflip = false;
        }.bind(this),
        1500
      );
    },

    startHardFlip() {
      this.hardflip = true;
      this.endHardFlip();
    },
    endHardFlip() {
      setTimeout(
        function() {
          this.hardflip = false;
        }.bind(this),
        1500
      );
    },

    startThreeSixtyFlip() {
      this.threeSixtyFlip = true;
      this.endThreeSixtyFlip();
    },
    endThreeSixtyFlip() {
      setTimeout(
        function() {
          this.threeSixtyFlip = false;
        }.bind(this),
        1500
      );
    },

    // Grinds
    startFiveO() {
      this.fiveO = true;
      this.endFiveO();
    },
    endFiveO() {
      setTimeout(
        function() {
          this.fiveO = false;
        }.bind(this),
        1500
      );
    },
    startKickflipNoseGrind() {
      this.kickflipNoseGrind = true;
      this.endKickflipNoseGrind();
    },
    endKickflipNoseGrind() {
      setTimeout(
        function() {
          this.kickflipNoseGrind = false;
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

  .menu {
    display: flex;
    margin-bottom: auto;
    margin-top: 10px;
    font-size: 20px;

    .menu-item {
      cursor: pointer;
      padding: 5px 8px;
      margin: 0 5px;
      color: white;
      text-transform: capitalize;
      background: transparent;

      &:hover {
        color: lightYellow;
      }

      &:disabled {
        cursor: not-allowed;
      }
    }
  }

  .rail {
    border: 6px solid transparent;
    border-image: linear-gradient(to right, teal, lightYellow);
    border-image-slice: 1;
    border-bottom: 0;

    width: 60%;
    height: 100px;
    position: absolute;
    bottom: 0;
  }

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

    &.kickfliping {
      animation: kickflip 1.5s forwards ease-in-out;
    }

    &.hardlfliping {
      animation: hardflip 1.5s forwards ease-in-out;
      transform-origin: left;
    }

    &.threesixtyflip {
      animation: threesixtyflip 1.5s forwards ease-in-out;
    }

    &.fiveo {
      animation: fiveo 1.5s forwards ease-in-out;
    }

    &.kickflipnosegrind {
      animation: kickflipnosegrind 1.5s forwards ease-in-out 0.2s;
    }

    @keyframes ollie {
      0% {
        transform: rotate(0) translateY(0);
      }
      25% {
        transform: rotate(0) translateY(0);
      }
      50% {
        transform: rotate(-30deg) translateY(-20px);
      }
      75% {
        transform: rotate(15deg) translateY(-200px);
      }
      100% {
        transform: rotate(0) translateY(0);
      }
    }

    @keyframes kickflip {
      0% {
        transform: rotate(0) translateY(0) rotateX(0);
      }
      25% {
        transform: rotate(0) translateY(0) rotateX(0);
      }
      50% {
        transform: rotate(-30deg) translateY(-100px) rotateX(-180deg);
      }
      75% {
        transform: rotate(20deg) translateY(-200px) rotateX(0);
      }
      100% {
        transform: rotate(0) translateY(0);
      }
    }

    @keyframes hardflip {
      0% {
        transform: rotate(0) translateY(0) rotateX(0);
      }
      25% {
        transform: rotate(0) translateY(0) rotateX(0);
      }
      50% {
        transform: rotate(-90deg) translateY(100px) rotateX(-180deg);
      }
      75% {
        transform: rotate(-180deg) translateY(200px) rotateX(-180deg);
      }
      100% {
        transform: rotate(-180deg) translateY(0) rotateX(-180deg);
      }
    }

    @keyframes threesixtyflip {
      0% {
        transform: rotate(0) translateY(0) rotateX(0) rotateY(0);
      }
      25% {
        transform: rotate(0) translateY(0) rotateX(0) rotateY(0);
      }
      45% {
        transform: rotate(-15deg) translateY(-75px) rotateX(0) rotateY(0);
      }
      50% {
        transform: rotate(-15deg) translateY(-150px) rotateX(-180deg)
          rotateY(-180deg);
      }
      75% {
        transform: rotate(10deg) translateY(-250px) rotateX(0) rotateY(0);
      }
      100% {
        transform: rotate(0) translateY(0) rotateY(0);
      }
    }

    @keyframes fiveo {
      0% {
        transform: rotate(0) translateY(0);
      }
      25% {
        transform: rotate(0) translateY(0);
      }
      45% {
        transform: rotate(0) translateY(0);
      }
      55% {
        transform: rotate(-30deg) translateY(-135px);
      }
      75% {
        transform: rotate(-30deg) translateY(-135px);
      }
      95% {
        transform: rotate(-30deg) translateY(-135px);
      }
      100% {
        transform: rotate(0) translateY(0);
      }
    }

    @keyframes kickflipnosegrind {
      0% {
        transform: rotate(0) translateY(0) rotateX(0);
      }
      15% {
        transform: rotate(0) translateY(0) rotateX(0);
      }
      20% {
        transform: rotate(-30deg) translateY(-120px) rotateX(-180deg);
      }
      40% {
        transform: rotate(20deg) translateY(-120px) rotateX(0);
      }
      60% {
        transform: rotate(20deg) translateY(-120px) rotateX(0);
      }
      80% {
        transform: rotate(20deg) translateY(-120px) rotateX(0);
      }
      95% {
        transform: rotate(0) translateY(0);
      }
      100% {
        transform: rotate(0) translateY(0);
      }
    }
  }
}
</style>
