<template>
    <div class="text-black">
        <select id="drumkit" v-model="drumkit" @change="updateDrumkit" class="border border-gray-900 font-bold cursor-pointer">
            <option value="707">707</option>
            <option value="808">808</option>
            <option value="909">909</option>
        </select>
    </div>
</template>

<script>

export default {
  name: 'DrumKit',
  props: {
    msg: String
  },
  data() {
    return {
      drumkit: '808'
    }
  },
  methods: {
      startPlayback() {
        this.$emit('startPlayback');
    },
    stopPlayback() {
      this.$emit('stopPlayback');
    },
    updateDrumkit() {
      this.$emit('updateDrumkit', this.drumkit);
    }
  }
}
</script>
