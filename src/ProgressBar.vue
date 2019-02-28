<template>
    <div class="progress-bar"
        :style="style"/>
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
        transition: {
            type: Number,
            default: 0,
        },
        opacity: {
            type: Number,
            default: 1,
            validator: v => v > 0 && v <= 1,
        },
        progress: {
            type: Number,
            required: true,
            validator: v => v >= 0 && v <= 100,
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
                height: `${this.thickness}px`,
                width: `${this.progress}%`,
                opacity: this.opacity,
                backgroundColor: this.color,
                boxShadow: `0 0 5px ${this.color}`,
                transition: `width ${this.transition}s`,
            };
        },
    },
};
</script>

<style lang="scss">
    .progress-bar {
        left: 0px;
        top: 0px;
        z-index: 9999;
    }
</style>
