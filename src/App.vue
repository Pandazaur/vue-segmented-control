<template>
    <div id="app">
        <segmented-control
            color="white"
            active-color="#444"
            :options="options"
            :multiple="false" />
    </div>
</template>

<script>
import SegmentedControl from './SegmentedControl.vue'

export default {
    components: {
        SegmentedControl
    },
    data () {
        return {
            options: [
                { label: 'Homme', value: 'man' },
                { label: 'Femme', value: 'woman' },
                { label: 'Autre', value: 'other' }
            ]
        }
    }
}
</script>

<style>
    body {
        font-family: Arial, serif;
    }
</style>
