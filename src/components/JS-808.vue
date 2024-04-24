<template>
  <div
    style="width: 80%; margin: 0 auto; border: 1px solid black; padding: 5px; background: #1c1c1c"
    class="text-white"
  >
    <Header
      @startPlayback="startPlayback"
      @pausePlayback="pausePlayback"
      @stopPlayback="stopPlayback"
      @updateBpm="updateBpm"
      @updateTimeDivision="updateTimeDivision"
      @updateDrumkit="updateDrumkit"
      @updateSequence="updateSequence"

      :isPlaying="isPlaying"
      :isStopped="isStopped"
      :isPaused="isPaused"
    />
    <hr style="width: 98%" />
    <GridHeader :step="step" />
    <hr style="width: 98%" />
    <MainGrid 
      :tracks="tracks" 
      :step="step" 
      :isPlaying="isPlaying" 
      :drumkit="drumkit"
      :sequence="sequence"
      :timeDivision="timeDivision" />
  </div>
</template>

<script>
import Header from './Header.vue';
import GridHeader from './GridHeader.vue';
import MainGrid from './MainGrid.vue';

import SequenceJson from '../sequence.json';

export default {
  name: 'JS-808',
  components: {
    Header,
    GridHeader,
    MainGrid
  },
  props: {
    msg: String
  },
  data() {
    return {
      tempo: 128,
      step: 0,
      interval: null,
      isPlaying: false,
      isStopped: true,
      isPaused: false,
      sequence: 'sequence-1',
      timeDivision: '16',
      drumkit: '808',
      // tracks: [
      //   {
      //     name: 'kick',
      //     values: []
      //   },
      //   {
      //     name: 'snare',
      //     values: []
      //   },
      //   {
      //     name: 'open hat',
      //     values: []
      //   },
      //   {
      //     name: 'closed hat',
      //     values: []
      //   }
      // ]
    }
  },
  beforeDestroy() {
    document.removeEventListener('keydown', this.startPlayback);
  },
  mounted() {
    document.addEventListener('keydown', e => {
      if (e.key === ' ') {
        e.preventDefault();

        if (!this.isPlaying) {
          this.startPlayback();
        } else {
          this.pausePlayback();
        }
      } else if (e.key === 'Enter' || e. key === 'Return') {
        this.stopPlayback();
        this.startPlayback();
      }
    })
  },
  methods: {
    convertBpmToMs(bpm) {

      return 60000 / bpm / (this.timeDivision / 4);
    },
    startPlayback() {
      if (!this.isPlaying) {
        this.isPlaying = true;
        this.isStopped = false;
        this.isPaused = false;
        console.log('starting playback');
        this.interval = setInterval(() => {
          // console.log(this.step + 1);
          this.step += 1;

          if (this.step > 16) {
            this.step = 1;
          }

          
        }, this.convertBpmToMs(this.tempo))
      } 
        
    },
    stopPlayback() {
      if (!this.isStopped) {
        console.log('stopping playback');
        clearInterval(this.interval);
        this.step = 0;
        this.isPlaying = false;
        this.isStopped = true;
        this.isPaused = false;
      }
      
    },
    pausePlayback() {
      if (!this.isPaused && !this.isStopped) {
        console.log('pausing playback');
        clearInterval(this.interval);
        this.isPlaying = false;
        this.isStopped = false;
        this.isPaused = true;
      }
      
    },
    updateBpm(bpm) {
      this.tempo = bpm;
    },
    updateSequence(sequence) {
      this.sequence = sequence;
    },
    updateDrumkit(drumkit) {
      this.drumkit = drumkit;
    },
    updateTimeDivision(time) {
      console.log(time);
      this.timeDivision = time;
    }
  },
  // watch: {
  //   'sequence'() {
  //     if (this.sequence === 'sequence-1') {
  //       this.tracks.forEach(track => {
  //         if (track.name === 'kick') {
  //           track.values = [0, 4, 8, 12];
  //         }

  //         if (track.name === 'snare') {
  //           track.values = [4, 12];
  //         }

  //         if (track.name === 'open hat') {
  //           track.values = [2, 6, 10, 14];
  //         }

  //         if (track.name === 'closed hat') {
  //           track.values = [0, 4, 8, 12];
  //         }
  //       })
  //     }
  //   }
  // },
  computed: {
    tracks() {
      return SequenceJson[this.sequence];
    }
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
