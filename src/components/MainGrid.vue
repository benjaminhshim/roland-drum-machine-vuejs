<template>
  <div>
    <Track v-for="(track, index) in tracks" :key="index" 
      :track="track" 
      :step="step" 
      :isPlaying="isPlaying" 
      :drumkit="drumkit"
      :sequence="sequence"
      :timeDivision="timeDivision" />
  </div>
</template>

<script>
  import Track from './Track';

export default {
  
  name: 'MainGrid',
  components : {
    Track
  },
  props: {
    tracks: Array,
    step: Number,
    isPlaying: Boolean,
    drumkit: String,
    sequence: String,
    timeDivision: String
  },
  methods: {

  }
}
</script>

<style scoped>

</style>
