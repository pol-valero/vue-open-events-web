<template>

<h4 >{{ title }}</h4>
<input 
    v-model="model"
    v-on:input="$emit('update-modelValue', model)"
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