<template>

  <button
    :disabled="disabled"
    @click="$emit('click')"
  >
    {{title}}<i v-if="loading" class="fa fa-circle-o-notch fa-spin"></i>
  </button>

</template>

<script>

export default {
  props: {
    title: String, 
    disabled: Boolean, 
    loading: Boolean
  },
  emits: ['click']
}
</script>