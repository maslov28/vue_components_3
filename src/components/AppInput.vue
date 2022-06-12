<template>

    <input 
        type="text" 
        :value="modelValue" 
        @input="$emit('update:modelValue', $event.target.value)"
        :placeholder="appPlaceholder"
    />

</template>

<script>

export default {
    props: {
        modelValue: String, 
        appPlaceholder: String
    },
    emits: ['update:modelValue']
}
</script>