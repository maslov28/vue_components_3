<template>

  <ul>
    <li>Сделать компонент кнопку, который принимает параметром title disabled, loading, и при клике эмитит событие клик</li>
    <li>Сделать компонент инпут, который двусторонне связан с родителем(т.е. принимает параметров modelValue и эмиттит событие update:modelValue), принимает параметр placeholder</li>
  </ul>

  <app-button
    :title="title" 
    :disabled="disabled" 
    :loading="loading"
    @button-click="buttonClick"
  ></app-button>

  <app-input
    :model-value="modelValue"
    :app-placeholder="appPlaceholder"
    @update="update"
  ></app-input>

</template>

<script>
import AppButton from './components/AppButton.vue'
import AppInput from './components/AppInput.vue'

import {ref} from 'vue'

export default {
  setup() {
    const title = ref('App Button')
    const disabled = ref(false)
    const loading = ref(false)
    const modelValue = ref('')
    const appPlaceholder = ref('This is placeholder')

    function buttonClick() {
      console.log('clicked')
    }

    function update(data) {
      modelValue.value = data
      console.log(modelValue.value)
    }

    return {
      title, 
      disabled, 
      loading, 
      buttonClick,
      modelValue,
      appPlaceholder,
      update
    }
  },

  components: {AppButton, AppInput}
}
</script>