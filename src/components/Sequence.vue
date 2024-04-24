<template>
    <div class="mr-4 text-black">
        <select id="sequence" v-model="sequence" @change="updateSequence" class="border border-gray-900 font-bold cursor-pointer">
            <option value="sequence-1">SEQUENCE-1</option>
            <option value="sequence-2">SEQUENCE-2</option>
            <option value="sequence-3">SEQUENCE-3</option>
        </select>
    </div>
</template>

<script>

export default {
  name: 'Sequence',
  props: {
    msg: String
  },
  data() {
    return {
      sequence: 'sequence-1'
    }
  },
  methods: {
      startPlayback() {
        this.$emit('startPlayback');
    },
    stopPlayback() {
      this.$emit('stopPlayback');
    },
    updateSequence() {
      this.$emit('updateSequence', this.sequence);
    }
  }
}
</script>
