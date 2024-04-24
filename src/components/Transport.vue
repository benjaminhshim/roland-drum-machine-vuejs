<template>
    <div style="display: flex; align-items: center" class="mr-4">
        <div id="stop" @click="$emit('stopPlayback')" class="mr-1 cursor-pointer">
            <i class="fa fa-stop"></i>
        </div>
        <div v-if="!isPlaying" id="play" class="mr-1 cursor-pointer">
            <span @click="$emit('startPlayback')">
                <i class="fa fa-play"></i>
            </span>
        </div>
        <div v-else-if="isPlaying" id="pause" class="mr-1 cursor-pointer">
            <span @click="$emit('pausePlayback')">
                <i class="fa fa-pause"></i>
            </span>
        </div>

        <input id="tempo" v-model.number="tempo" type="number" min="20" max="200" @input="$emit('updateBpm', tempo)"  class="mr-1 cursor-pointer text-black"/>
        <div id="bpm" class="font-bold text-1xl">
            BPM
        </div>
    </div>
</template>

<script>
export default {
  name: 'Transport',
  props: {
    isPlaying: Boolean,
    isStopped: Boolean,
    isPaused: Boolean
  },
  data() {
      return {
          tempo: 128
      }
  }
}
</script>

<style scoped>
    #stop{
        /* border: 1px solid black; */
        width: 25px;
        height: 25px;
        display: inline-block;
    }

    #play {
        /* border: 1px solid black; */
        width: 25px;
        height: 25px;
        display: inline-block;
    }

    #pause {
        border: 1px solid black;
        width: 25px;
        height: 25px;
        display: inline-block;
    }

    #tempo {
        border: 1px solid black;
        width: 50px;
        height: 25px;
        display: inline-block;
    }

    #bpm {
        display: inline-block;
    }
</style>
