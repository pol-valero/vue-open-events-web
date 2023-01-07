<template>

<h4 >{{ title }}</h4>
<input 
    :placeholder= "defaultTxt" 
    :value = "modelValue"
    @input = "$emit('update:modelValue', modelValue)"
    />
</template>

<script>
export default {
    properties:  {
        title: {
            type: String,
            default: 'Text'
        },
        defaultTxt: {
            type: String,
            default: 'Text'
        },
        modelValue: {
            type: [String, Number]
        }
    }

}

</script>