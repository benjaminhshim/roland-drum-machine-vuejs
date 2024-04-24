<template>
    <div class="mr-4 text-black">
        <select id="time-division" v-model="timeDivision" @change="updateTimeDivision" class="border border-gray-900 font-bold cursor-pointer">
            <option value="4">1/4</option>
            <option value="8">1/8</option>
            <option value="16">1/16</option>
        </select>
    </div>
</template>

<script>

export default {
  name: 'TimeDivision',
  props: {
    msg: String
  },
  data() {
    return {
      timeDivision: '16'
    }
  },
  methods: {
      startPlayback() {
        this.$emit('startPlayback');
    },
    stopPlayback() {
      this.$emit('stopPlayback');
    },
    updateTimeDivision() {
      this.$emit('updateTimeDivision', this.timeDivision);
    }
  }
}
</script>
