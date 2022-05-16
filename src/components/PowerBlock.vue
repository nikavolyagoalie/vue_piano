<template>
  <div>
      <span>On/Off</span>
      <Button @click="disableAllButtons"/>
  </div>
</template>

<script>
import Button from '../components/UI/Button.vue'

export default {
    name: 'power-block',
    components: {
        Button
    },
    props: {
        power: {
            type: Boolean,
            default: true
        }
    },
    methods: {
        disableAllButtons() {
            this.$emit('update:power', false)
        }
    }
}
</script>

<style>

</style>