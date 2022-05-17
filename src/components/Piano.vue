<template>
  <div class="piano">
    <div class="piano__head">
      <div class="piano__dashboard">
        <div class="piano__power piano__block">
          <span>Power</span>
          <div class="btns">
            <Button @click="disableAllButtons" :class="{'power': togglePiano === false}"/>
          </div>
        </div>
        <div class="piano__volume piano__block">
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
          <div class="piano__volume-btns btns">
            <Button @click="minusVolume" />
            <Button @click="plusVolume" />
          </div>
        </div>
        <div class="piano__samples piano__block">
          <span>Tone</span>
          <div class="btns">
            <Button />
            <Button />
            <Button />
          </div>
        </div>
        <div class="piano__octaves piano__block">
          <span>Octaves</span>
          <div class="btns">
            <Button @click="minusOctave" :disabled="minusOctaveBtn" />
            <Button @click="plusOctave" :disabled="plusOctaveBtn" />
          </div>
        </div>
      </div>
    </div>
    <div class="piano__keys">
      <Octave
        :octaveNum="piano_keys[0].octave"
        :activeOctaveAll="octaveActive"
        :activeOctave="piano_keys[0].active"
        :sounds="music[0]"
        :keys="piano_keys[0].keys"
        :togglePiano="togglePiano"
      />
      <Octave
        :octaveNum="piano_keys[1].octave"
        :activeOctaveAll="octaveActive"
        :activeOctave="piano_keys[1].active"
        :sounds="music[1]"
        :keys="piano_keys[1].keys"
        :togglePiano="togglePiano"
      />
      <Octave
        :octaveNum="piano_keys[2].octave"
        :activeOctaveAll="octaveActive"
        :activeOctave="piano_keys[2].active"
        :sounds="music[2]"
        :keys="piano_keys[2].keys"
        :togglePiano="togglePiano"
      />
      <Octave
        :octaveNum="piano_keys[3].octave"
        :activeOctaveAll="octaveActive"
        :activeOctave="piano_keys[3].active"
        :sounds="music[3]"
        :keys="piano_keys[3].keys"
        :togglePiano="togglePiano"
      />
      <Octave
        :octaveNum="piano_keys[8].octave"
        :activeOctaveAll="octaveActive"
        :activeOctave="piano_keys[8].active"
        :sounds="music[8]"
        :keys="piano_keys[8].keys"
        :togglePiano="togglePiano"
      />
    </div>
    <div class="piano__keyboard--push">
      <table>
        <thead>
          <tr>
            <th>Клавиатура</th>
            <th>Клавиша(бел.)</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>A</td>
            <td>"C"</td>
          </tr>
          <tr>
            <td>S</td>
            <td>"D"</td>
          </tr>
          <tr>
            <td>D</td>
            <td>"E"</td>
          </tr>
          <tr>
            <td>F</td>
            <td>"F"</td>
          </tr>
          <tr>
            <td>G</td>
            <td>"G"</td>
          </tr>
          <tr>
            <td>H</td>
            <td>"A"</td>
          </tr>
          <tr>
            <td>J</td>
            <td>"B"</td>
          </tr>
        </tbody>
      </table>
      <table>
        <thead>
          <tr>
            <th>Клавиатура</th>
            <th>Клавиша(чер.)</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>W</td>
            <td>"Cs"</td>
          </tr>
          <tr>
            <td>E</td>
            <td>"Ds"</td>
          </tr>
          <tr>
            <td>T</td>
            <td>"Fs"</td>
          </tr>
          <tr>
            <td>Y</td>
            <td>"Gs"</td>
          </tr>
          <tr>
            <td>U</td>
            <td>"As"</td>
          </tr>
        </tbody>
      </table>
      <table>
        <thead>
          <tr>
            <th>Клавиатура</th>
            <th>Клавиша(верх.)</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>Z</td>
            <td>"Octaves лев."</td>
          </tr>
          <tr>
            <td>X</td>
            <td>"Octaves прав."</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
import sounds from "../assets/audiosprite";
import Button from "../components/UI/Button.vue";
import Octave from "../components/Octave.vue";

export default {
  name: "Piano",
  components: {
    Button,
    Octave,
  },
  data() {
    return {
      minusOctaveBtn: false,
      plusOctaveBtn: false,
      keys_arr: [],
      volume: 2,
      octave: 1,
      octaveActive: false,
      volume_levels: [
        { id: 1, vol: true },
        { id: 2, vol: true },
        { id: 3, vol: false },
        { id: 4, vol: false },
        { id: 5, vol: false },
      ],
      togglePiano: true,

      music: [
        sounds["octava0"],
        sounds["octava1"],
        sounds["octava2"],
        sounds["octava3"],
        sounds["octava4"],
        sounds["octava5"],
        sounds["octava6"],
        sounds["octava7"],
        sounds["octava8"],
      ],

      piano_keys: [
        { octave: 0, keys: ["A0", "As0", "B0"], active: false },
        {
          octave: 1,
          keys: [
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
          ],
          active: true,
        },
        {
          octave: 2,
          keys: [
            "C2",
            "Cs2",
            "D2",
            "Ds2",
            "E2",
            "F2",
            "Fs2",
            "G2",
            "Gs2",
            "A2",
            "As2",
            "B2",
          ],
          active: false,
        },
        {
          octave: 3,
          keys: [
            "C3",
            "Cs3",
            "D3",
            "Ds3",
            "E3",
            "F3",
            "Fs3",
            "G3",
            "Gs3",
            "A3",
            "As3",
            "B3",
          ],
          active: false,
        },
        {
          octave: 4,
          keys: [
            "C4",
            "Cs4",
            "D4",
            "Ds4",
            "E4",
            "F4",
            "Fs4",
            "G4",
            "Gs4",
            "A4",
            "As4",
            "B4",
          ],
          active: false,
        },
        {
          octave: 5,
          keys: [
            "C5",
            "Cs5",
            "D5",
            "Ds5",
            "E5",
            "F5",
            "Fs5",
            "G5",
            "Gs5",
            "A5",
            "As5",
            "B5",
          ],
          active: false,
        },
        {
          octave: 6,
          keys: [
            "C6",
            "Cs6",
            "D6",
            "Ds6",
            "E6",
            "F6",
            "Fs6",
            "G6",
            "Gs6",
            "A6",
            "As6",
            "B6",
          ],
          active: false,
        },
        {
          octave: 7,
          keys: [
            "C7",
            "Cs7",
            "D7",
            "Ds7",
            "E7",
            "F7",
            "Fs7",
            "G7",
            "Gs7",
            "A7",
            "As7",
            "B7",
          ],
          active: false,
        },
        { octave: 8, keys: ["C8"], active: false },
      ],
    };
  },

  created() {
    this.keys_arr = this.piano_keys.map((item) => item.keys).flat();

    window.addEventListener("keydown", (e) => {
      if (!this.togglePiano) {
        if (e.key === "z") {
          this.minusOctave();
        }

        if (e.key === "x") {
          this.plusOctave();
        }
      }
    });
  },

  methods: {
    disableAllButtons() {
      if (this.togglePiano) {
        this.togglePiano = false;
      } else {
        this.togglePiano = true;
      }
    },

    minusVolume() {
      if (this.volume > 0 && !this.togglePiano) {
        this.volume -= 1;
        this.volume_levels[this.volume].vol = false;
      }
    },

    plusVolume() {
      if (this.volume < this.volume_levels.length && !this.togglePiano) {
        this.volume += 1;
        this.volume_levels[this.volume - 1].vol = true;
      }
    },

    minusOctave() {
      if (!this.togglePiano) {
        console.log(this.octave);
        this.octave -= 1;
        this.piano_keys[this.octave].active = true;
        this.piano_keys[this.octave + 1].active = false;
        if (this.octave <= 0) {
          this.minusOctaveBtn = true;
          this.plusOctaveBtn = false;
        }
      }
    },

    plusOctave() {
      if (!this.togglePiano) {
        console.log(this.octave);
        this.octave += 1;
        this.piano_keys[this.octave - 1].active = false;
        this.piano_keys[this.octave].active = true;
        if (this.octave >= this.piano_keys.length - 1) {
          this.plusOctaveBtn = true;
          this.minusOctaveBtn = false;
        }
      }
    },
  },
};
</script>

<style scoped>
.btns {
  display: flex;
  justify-content: space-around;
  margin-top: 20px;
}

.btn {
  height: 40px;
  background-color: #c0c3a5;
}

.btn.power {
  background-color: #9cac08;
}

.piano {
  display: flex;
  width: 100%;
  flex-direction: column;
  background-color: #000;
}

.piano__head {
  margin: 25px auto 30px;
}

.piano__dashboard {
  display: flex;
  align-items: flex-end;
}

.piano__block {
  margin: 0 10px;
  min-width: 60px;
}

.piano__keys {
  display: flex;
  margin: 0 auto;
}

.piano__volume-levels {
  display: flex;
}

.piano__keyboard--push {
  display: flex;
  margin: 20px auto;
}

table {
  margin: 0 20px;
}

.level {
  width: 10px;
  height: 10px;
  border-radius: 50%;
  border: 1px solid #fff;
  margin-left: 5px;
}

.vol {
  background-color: #fff;
}
</style>