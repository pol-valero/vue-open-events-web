<template>

    <h4 >{{ title }}</h4>
    <textarea
          v-model="input"
          v-on:input="$emit('update-modelValue', input)"

          class="textarea field"
          cols="40"
          rows="5"
          :placeholder="defaultTxt"
        ></textarea>
    </template>
    
<script>
    export default {
        //We define some properties so that the parent can modify them as needed
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