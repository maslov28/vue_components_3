<template>

    <input 
        type="text" 
        v-model="modelValue" 
        :placeholder="appPlaceholder"
        @input="update"
    />

</template>

<script>

import {ref} from 'vue'

export default {
    props: ['model-value', 'app-placeholder'],
    emits: ['update'],

    setup(props, context) {
        const modelValue = ref(props.modelValue)
        const appPlaceholder = ref(props.appPlaceholder)

        function update() {
            context.emit('update', modelValue.value)
        }

        return {
            modelValue, 
            appPlaceholder, 
            update
        }
    }

}
</script>