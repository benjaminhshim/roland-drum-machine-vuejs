<template>
  <div style="display: flex; align-items: center;" class="m-1">
      <h1 style="width: 150px; text-align: right; color: orange" class="font-bold text-3xl">JS-808</h1>
        <div style="width: 80%"></div>
        <div class="flex">
          <Transport 
            @startPlayback="startPlayback"
            @pausePlayback="pausePlayback" 
            @stopPlayback="stopPlayback"
            @updateBpm="updateBpm"
            
            :isPlaying="isPlaying"
            :isStopped="isStopped"
            :isPaused="isPaused"
      />
        <TimeDivision @updateTimeDivision="updateTimeDivision"/>

        <Sequence @updateSequence="updateSequence"/>

        <DrumKit @updateDrumkit="updateDrumkit"/>
        </div>
        
  </div>
</template>

<script>

import Transport from './Transport.vue';
import Sequence from './Sequence.vue';
import DrumKit from './DrumKit.vue';
import TimeDivision from './TimeDivision.vue';

export default {
  name: 'Header',
  components : {
      Transport,
      Sequence,
      DrumKit,
      TimeDivision
  },
  data() {
    return {
      tempo: 0
    }
  },
  props: {
    isPlaying: Boolean,
    isStopped: Boolean,
    isPaused: Boolean
  },
  methods: {
    startPlayback() {
        this.$emit('startPlayback');
    },
    stopPlayback() {
      this.$emit('stopPlayback');
    },
    pausePlayback() {
      this.$emit('pausePlayback');
    },
    updateBpm(tempo) {
      this.$emit('updateBpm', tempo)
    },
    updateTimeDivision(time) {
      this.$emit('<div class="divide-y"></div>', time)
    },
    updateSequence(sequence) {
      this.$emit('updateSequence', sequence)
    },
    updateDrumkit(drumkit) {
      this.$emit('updateDrumkit', drumkit)
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
