<template>

  <ul>
    <li>Сделать компонент кнопку, который принимает параметром title disabled, loading, и при клике эмитит событие клик</li>
    <li>Сделать компонент инпут, который двусторонне связан с родителем(т.е. принимает параметров modelValue и эмиттит событие update:modelValue), принимает параметр placeholder</li>
  </ul>

  <app-button
    :title="title" 
    :disabled="disabled" 
    :loading="loading"
    @click="buttonClick"
    @set-disabled="setDisabled"
  ></app-button>

  <app-input
    v-model="inputText"
    :app-placeholder="appPlaceholder"
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
    const inputText = ref('')
    const appPlaceholder = ref('This is placeholder')

    function buttonClick() {
      if (inputText.value !== '') {
        loading.value = true
        disabled.value = true
        setTimeout(() => {
          loading.value = false
          disabled.value = false
          inputText.value = ''
        }, 2000)
      }
    }

    function setDisabled() {
      disabled.value = true
    }

    return {
      title, 
      disabled, 
      loading, 
      buttonClick,
      setDisabled,
      inputText,
      appPlaceholder
    }
  },

  components: {AppButton, AppInput}
}
</script>