<template>
    <div style="display: flex; align-items: center;" class="my-6">
        <div style="width: 250px; text-align: right; font-weight: 900;">{{ capsLock(track.name) }}</div>
        <div class="track-row" style="width: 100%; display: flex; justify-content: space-around;" >
            <Value v-for="(grid, index) in gridSize" :key="index" 
                :track="track" 
                :index="index" 
                :isPlaying="isPlaying" 
                :step="step"
                :drumkit="drumkit" 
                :sequence="sequence"
                :timeDivision="timeDivision" />
        </div>
    </div>
</template>

<script>

import Value from './Value.vue';

export default {
  name: 'Track',
  components : {
      Value
  },
  props: {
    track: Object,
    isPlaying: Boolean,
    step: Number,
    drumkit: String,
    sequence: String,
    timeDivision: String
  },
  data() {
      return {
        gridSize: 16
      }
  },
  methods: {
      capsLock(header) {
          return header.toUpperCase();
      }
  }
}
</script>

<style scoped>
    .track-row input{
        border: 1px solid black;
        width: 25px;
        height: 25px;
    }
</style>