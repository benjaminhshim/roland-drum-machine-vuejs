<template :class="{'grid-cols-4 divide-x divide-gray-900': index % 4 === 0}">
    <div>
        <input type="checkbox" v-model="checked"/>
    </div>
</template>

<script>
import kick707 from '@/assets/707/TR-707Kick01.wav';
import snare707 from '@/assets/707/TR-707Snare02.wav';
import openhat707 from '@/assets/707/TR-707Hat_O.wav';
import closedhat707 from '@/assets/707/TR-707Hat_C.wav';

import kick808 from '@/assets/808/TR-808Kick04.wav';
import snare808 from '@/assets/808/TR-808Snare01.wav';
import openhat808 from '@/assets/808/TR-808Hat_O03.wav';
import closedhat808 from '@/assets/808/TR-808Hat_C02.wav';

import kick909 from '@/assets/909/TR909_kick_01.wav';
import snare909 from '@/assets/909/TR-909Snare 02.wav';
import openhat909 from '@/assets/909/TR-909Hat O 03.wav';
import closedhat909 from '@/assets/909/TR-909Hat C 02.wav';

export default {
  name: 'Value',
  props: {
    track: Object,
    index: Number,
    isPlaying: Boolean,
    step: Number,
    drumkit: String,
    sequence: String,
    timeDivision: String
  },
  data() {
    return {
      checked: false
    }
  },
  methods: {
  },
  created() {
    if (this.track.values.indexOf(this.index) >= 0) {
        this.checked = true;
      } else {
        this.checked = false;
      }
  },
  computed: {
    checkedSequence() {
      if (this.track.values.indexOf(this.index) >= 0) {
        return true;
      }

      return false;
    }
  },
  watch: {
    'step'() {
      if (this.drumkit === '707') {
        if (this.track.name === 'kick' && this.isPlaying && this.step === this.index + 1 && (this.checkedSequence || this.checked)) {
          // console.log('kick');
          const audio = new Audio(kick707);
          audio.play();
        }

        if (this.track.name === 'snare' && this.isPlaying && this.step === this.index + 1 && (this.checkedSequence || this.checked)) {
          // console.log('snare');
          const audio = new Audio(snare707);
          audio.play();
        }

        if (this.track.name === 'openhat' && this.isPlaying && this.step === this.index + 1 && (this.checkedSequence || this.checked)) {
          // console.log('openhat');
          const audio = new Audio(openhat707);
          audio.play();
        }

        if (this.track.name === 'closedhat' && this.isPlaying && this.step === this.index + 1 && (this.checkedSequence || this.checked)) {
          // console.log('closedhat');
          const audio = new Audio(closedhat707);
          audio.play();
        }
      } else if (this.drumkit === '808') {
        if (this.track.name === 'kick' && this.isPlaying && this.step === this.index + 1 && (this.checkedSequence || this.checked)) {
          // console.log('kick');
          const audio = new Audio(kick808);
          audio.play();
        }

        if (this.track.name === 'snare' && this.isPlaying && this.step === this.index + 1 && (this.checkedSequence || this.checked)) {
          // console.log('snare');
          const audio = new Audio(snare808);
          audio.play();
        }

        if (this.track.name === 'openhat' && this.isPlaying && this.step === this.index + 1 && (this.checkedSequence || this.checked)) {
          // console.log('openhat');
          const audio = new Audio(openhat808);
          audio.play();
        }

        if (this.track.name === 'closedhat' && this.isPlaying && this.step === this.index + 1 && (this.checkedSequence || this.checked)) {
          // console.log('closedhat');
          const audio = new Audio(closedhat808);
          audio.play();
        }
      } else if (this.drumkit === '909') {
        if (this.track.name === 'kick' && this.isPlaying && this.step === this.index + 1 && (this.checkedSequence || this.checked)) {
          // console.log('kick');
          const audio = new Audio(kick909);
          audio.play();
        }

        if (this.track.name === 'snare' && this.isPlaying && this.step === this.index + 1 && (this.checkedSequence || this.checked)) {
          // console.log('snare');
          const audio = new Audio(snare909);
          audio.play();
        }

        if (this.track.name === 'openhat' && this.isPlaying && this.step === this.index + 1 && (this.checkedSequence || this.checked)) {
          // console.log('openhat');
          const audio = new Audio(openhat909);
          audio.play();
        }

        if (this.track.name === 'closedhat' && this.isPlaying && this.step === this.index + 1 && (this.checkedSequence || this.checked)) {
          // console.log('closedhat');
          const audio = new Audio(closedhat909);
          audio.play();
        }
      }
      
    },
    'sequence'() {
      if (this.track.values.indexOf(this.index) >= 0) {
        this.checked = true;
      } else {
        this.checked = false;
      }
    }
  }
}
</script>

<style scoped>

</style>