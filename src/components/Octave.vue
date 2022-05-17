<template>
  <div class="octave">
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
  data() {
    return {
      // :octaveNum="piano_keys[8].octave"
      //   :activeOctaveAll="octaveActive"
      //   :activeOctave="piano_keys[8].active"
      //   :sounds="music[8]"
      //   :keys="piano_keys[8].keys"
    };
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
  margin-bottom: 1px;
  cursor: pointer;
}

.white {
  background-color: #fff;
  color: #000;
  border: 1px solid #000;
}

.black {
  background-color: #000;
  color: #fff;
  border: 1px solid transparent;
}
</style>