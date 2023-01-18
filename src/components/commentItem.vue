<template>
<section>
    <h4>{{name}} {{lastname}}</h4>
    <p>{{comment}}</p>
    <p>{{rating}}/10</p>
</section>
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
            type: Number,
            default: 0
        }
    }
};
</script>