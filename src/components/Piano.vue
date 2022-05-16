<template>
  <div class="piano">
    <div class="piano__head">
      <div class="piano__dashboard">
        <div class="piano__power">
          <span>{{ togglePiano === false ? "On" : "Off" }}</span>
          <Button @click="disableAllButtons" />
        </div>
        <div class="piano__volume">
          <div class="piano__volume-header">
            <span>Volume</span>
            <div class="piano__volume-levels">
              <div
                class="level"
                v-for="lvl in volume_levels"
                :key="lvl"
                :class="{ vol: lvl.vol }"
              ></div>
            </div>
          </div>
          <div class="piano__volume-btns">
            <Button @click="minusVolume" />
            <Button @click="plusVolume" />
          </div>
        </div>
        <div class="piano__samples">
          <span>Tone</span>
          <div class="btns">
            <Button />
            <Button />
            <Button />
          </div>
        </div>
        <div class="piano__octaves">
          <div class="btns">
            <Button @click="minusOctave"/>
            <Button @click="plusOctave"/>
          </div>
        </div>
      </div>
    </div>
    <div class="piano__keys">
      <button
        class="key"
        v-for="(key, i) in keys_arr"
        :key="i"
        @click.prevent="playSound(music[1][key])"
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
  </div>
</template>

<script>
import sounds from "../assets/audiosprite";
import Button from "../components/UI/Button.vue";

export default {
  name: "Piano",
  components: {
    Button,
  },
  data() {
    return {
      keys_arr: [],
      volume: 2,
      octave: 1,
      volume_levels: [
        { id: 1, vol: true },
        { id: 2, vol: true },
        { id: 3, vol: false },
        { id: 4, vol: false },
        { id: 5, vol: false },
      ],
      togglePiano: true,
      music: [sounds["octava0"], sounds["octava1"]],
      piano_keys: [
        {octave: 0, keys: ["A0", "As0", "B0"], active: false},
        {octave: 1, keys:[
          "C1",
          "Cs1",
          "D1",
          "Ds1",
          "E1",
          "F1",
          "Fs1",
          "G1",
          "Gs1",
          "A1",
          "As1",
          "B1",
        ], active: true},
        {octave: 2, keys:[
          "C2",
          "C#2",
          "D2",
          "D#2",
          "E2",
          "F2",
          "F#2",
          "G2",
          "G#2",
          "A2",
          "A#2",
          "B2",
        ], active: false},
        {octave: 3, keys:[
          "C3",
          "C#3",
          "D3",
          "D#3",
          "E3",
          "F3",
          "F#3",
          "G3",
          "G#3",
          "A3",
          "A#3",
          "B3",
        ], active: false},
        {octave: 4, keys:[
          "C4",
          "C#4",
          "D4",
          "D#4",
          "E4",
          "F4",
          "F#4",
          "G4",
          "G#4",
          "A4",
          "A#4",
          "B4",
        ], active: false},
        {octave: 5, keys:[
          "C5",
          "C#5",
          "D5",
          "D#5",
          "E5",
          "F5",
          "F#5",
          "G5",
          "G#5",
          "A5",
          "A#5",
          "B5",
        ], active: false},
        {octave: 6, keys:[
          "C6",
          "C#6",
          "D6",
          "D#6",
          "E6",
          "F6",
          "F#6",
          "G6",
          "G#6",
          "A6",
          "A#6",
          "B6",
        ], active: false},
        {octave: 7, keys:[
          "C7",
          "C#7",
          "D7",
          "D#7",
          "E7",
          "F7",
          "F#7",
          "G7",
          "G#7",
          "A7",
          "A#7",
          "B7",
        ], active: false},
        {octave: 8, keys:["C8"], active: false},
      ],
    };
  },

  created() {
    this.keys_arr = this.piano_keys.map(item => item.keys).flat()
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

    disableAllButtons() {
      if (this.togglePiano) {
        this.togglePiano = false;
      } else {
        this.togglePiano = true;
      }
    },

    minusVolume() {
      if (this.volume > 0) {
        this.volume -= 1;
        this.volume_levels[this.volume].vol = false;
      }
    },

    plusVolume() {
      if (this.volume < this.volume_levels.length) {
        this.volume += 1;
        this.volume_levels[this.volume - 1].vol = true;
      }
    },

    minusOctave() {
      if (this.octave > 0) {
        this.octave -= 1;
        console.log(this.octave)
        this.piano_keys[this.octave - 1].active = false;
        this.piano_keys[this.octave + 1].active = true;

      }
    },

    plusOctave() {
      if (this.octave < this.piano_keys.length) {
        this.octave += 1;
        console.log(this.octave)
        this.piano_keys[this.octave - 1].active = true;
        this.piano_keys[this.octave + 1].active = false;

      }
    },
  },
};
</script>

<style scoped>
.piano {
  display: flex;
  width: 100%;
  flex-direction: column;
}

.piano__dashboard {
  display: flex;
}

.piano__keys {
  width: 80%;
}

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

.piano__volume-levels {
  display: flex;
}

.level {
  width: 10px;
  height: 10px;
  border-radius: 50%;
  border: 1px solid #000;
  margin-left: 5px;
}

.vol {
  background-color: red;
}
</style>