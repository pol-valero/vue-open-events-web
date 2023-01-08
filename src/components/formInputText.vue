<template>

<h4 >{{ title }}</h4>
<input 
    v-model="input"
    v-on:input="$emit('update-modelValue', input)"
    class = field
    :placeholder= "defaultTxt" 
    />
</template>

<script>
export default {
    props:  {
        title: {
            type: String,
            default: 'Text'
        },
        defaultTxt: {
            type: String,
            default: 'Text'
        }
    }

}

</script>