<template>
    <div :style="style"/>
</template>

<script>
export default {
    props: {
        color: {
            type: String,
            default: '#f44336',
        },
        thickness: {
            type: Number,
            default: 2,
            validator: v => v > 0,
        },
        opacity: {
            type: Number,
            default: 1,
            validator: v => v > 0 && v <= 1,
        },
        progress: {
            type: Number,
            required: true,
        },
        position: {
            type: String,
            default: 'absolute',
            validator: v => ['absolute', 'fixed'].includes(v),
        },
    },

    computed: {
        style() {
            return {
                position: this.position,
                left: '0px',
                top: '0px',
                height: `${this.thickness}px`,
                width: `${this.progress}%`,
                opacity: this.opacity,
                backgroundColor: this.color,
                boxShadow: `0 0 5px ${this.color}`,
            };
        },
    },
};
</script>
