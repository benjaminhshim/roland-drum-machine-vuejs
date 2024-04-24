<template>
    <div style="display: flex;" class="my-2">
        <div style="width: 250px"></div>
        <div style="width: 100%; display: flex; justify-content: space-around;">
            <div v-for="(stepNumber, index) in steps" :key="index"
              style="width: 13px;" 
              :style="{'font-weight': step === stepNumber ? '700' : '100', 'color': index < 4 ? 'red' : index >= 4 && index <=7 ? 'orange' : index >= 8 && index <= 11 ? 'yellow' : 'white'}">
              <div class="font-bold" style="height: 12px;"><span v-show="showIndicator(stepNumber)">*</span></div>
              <div class="font-bold">{{stepNumber}}</div>
              </div>
        </div>
    </div>
</template>
<script>
export default {
  name: 'GridHeader',
  components: {
  },
  props: {
    msg: String,
    step: Number
  },
  data() {
    return {
      tempo: 128,
      steps: 16
    }
  },
  methods: {
    showIndicator(stepNumber) {
      return stepNumber === this.step;
    }
  },
}
</script>

<style scoped>
    li {
        list-style-type: none;
    }
</style>
