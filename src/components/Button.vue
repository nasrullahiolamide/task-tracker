<template>
    <button @click="$emit('toggle-add-task')" :style= "{background:color}"> 
        {{text}} 
    </button>
</template>

<script>
export default {
    name: 'Button',
    props: {
        text: String,
        color: String
    },
}
</script>