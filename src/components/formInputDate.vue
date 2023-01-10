<template>

<h4 >{{ title }}</h4>
<input 
    v-model="input"
    v-on:input="$emit('update-modelValue', input)"
    class = field
    type="datetime-local"
    />
</template>

<script>
export default {
    //We define some properties so that the parent can modify them as needed
    props:  {
        title: {
            type: String,
            default: 'Text'
        }
    }

}

</script>