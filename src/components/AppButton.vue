<template>

  <button
    :disabled="isDisabled"
    @click="click"
  >{{buttonTitle}}

    <i v-if="isLoading" class="fa fa-circle-o-notch fa-spin"></i>

  </button>

</template>

<script>

import {ref, onMounted} from 'vue'

export default {
  props: ['title', 'disabled', 'loading'],
  emits: ['button-click'],
    
  setup(props, context) {
      const buttonTitle = ref(props.title)
      const isDisabled = ref(props.disabled)
      const isLoading = ref(props.loading)

      function click() {
        context.emit('button-click')
      }

      onMounted(() => {
        if (isLoading.value) isDisabled.value = true
      })

    return {
      buttonTitle, 
      isDisabled, 
      isLoading, 
      click
    }
  }
}
</script>