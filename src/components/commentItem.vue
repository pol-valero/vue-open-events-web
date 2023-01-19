<template>
    <h4>{{name}} {{lastname}}</h4>
    <p>{{comment}}</p>
    <p>{{rating}}</p>
</template>

<script>
export default {
    props: {
        name: {
            type: String,
            default: ''
        },
        lastname: {
            type: String,
            default: ''
        },
        comment: {
            type: String,
            default: ''
        },
        rating: {
            type: String,
            default: ''
        }
    }
};
</script>