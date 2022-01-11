<template>
    <div v-bind:style = "{ width: width + 'px', height: height + 'px' }"></div>
</template>

<script>
export default {
    data() {
        return {
            width: 40,
            height: 80
        };
    }
};
</script>

<style scoped>
</style>