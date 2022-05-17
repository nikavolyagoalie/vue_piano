<template>
  <div class="octave" :class="{ 'active-octave': activeOctave === true }">
    <button
      class="key"
      v-for="(key, i) in keys"
      :key="i"
      @click.prevent="playSound(sounds[key])"
      :disabled="togglePiano"
    >
      <div v-if="!String(key[1]).includes('s')" class="white">
        {{ key }}
      </div>
      <div v-else class="black">
        {{ key }}
      </div>
    </button>
  </div>
</template>

<script>
export default {
  created() {
    window.addEventListener("keydown", (e) => {
      if (!this.togglePiano) {
        if (e.key === this.keyboard[0]) {
          this.playSound(this.sounds[this.keys[0]]);
        }

        if (e.key === this.keyboard[1]) {
          this.playSound(this.sounds[this.keys[1]]);
        }

        if (e.key === this.keyboard[2]) {
          this.playSound(this.sounds[this.keys[2]]);
        }

        if (e.key === this.keyboard[3]) {
          this.playSound(this.sounds[this.keys[3]]);
        }

        if (e.key === this.keyboard[4]) {
          this.playSound(this.sounds[this.keys[4]]);
        }

        if (e.key === this.keyboard[5]) {
          this.playSound(this.sounds[this.keys[5]]);
        }

        if (e.key === this.keyboard[6]) {
          this.playSound(this.sounds[this.keys[6]]);
        }

        if (e.key === this.keyboard[7]) {
          this.playSound(this.sounds[this.keys[7]]);
        }

        if (e.key === this.keyboard[8]) {
          this.playSound(this.sounds[this.keys[8]]);
        }

        if (e.key === this.keyboard[9]) {
          this.playSound(this.sounds[this.keys[9]]);
        }

        if (e.key === this.keyboard[10]) {
          this.playSound(this.sounds[this.keys[10]]);
        }

        if (e.key === this.keyboard[11]) {
          this.playSound(this.sounds[this.keys[11]]);
        }

        if (e.key === this.keyboard[12]) {
          this.playSound(this.sounds[this.keys[12]]);
        }

        if (e.key === this.keyboard[13]) {
          this.playSound(this.sounds[this.keys[13]]);
        }
      }
    });
  },
  props: {
    octaveNum: {
      type: Number,
    },
    activeOctaveAll: {
      type: Boolean,
      default: false,
    },
    activeOctave: {
      type: Boolean,
      default: false,
    },
    sounds: {
      type: Object,
    },
    keys: {
      type: Array,
    },
    togglePiano: {
      type: Boolean,
      default: true,
    },
  },
  data() {
    return {
      keyboard: ["a", "w", "s", "e", "d", "f", "t", "g", "y", "h", "u", "j"],
    };
  },
  methods: {
    playSound(sound) {
      console.log(sound);
      if (sound) {
        let audio = new Audio(sound);
        console.log(audio);
        audio.play();
      }
    },
  },
};
</script>

<style scoped>
.key {
  cursor: pointer;
  height: 200px;
  outline: none;
  border: 1px solid #000;
  background-color: #fff;
  margin: 0 0.5px;
  position: relative;
  width: 27px;
}

.white {
  background-color: #fff;
  color: #000;
  top: 0;
  position: absolute;
}

.black {
  background-color: #000;
  color: #fff;
  position: absolute;
  width: 100%;
  height: 100%;
  top: 0;
}

.octave {
  border: 3px solid transparent;
  margin: 0 0.5px;
}

.active-octave {
  border: 3px solid #12c912;
}
</style>