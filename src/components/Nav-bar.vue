<template>
    <div id="sticky-sidebar">
        <ul class="nav flex-column fw-bold" v-if="sourates">
        <sourate v-for="(sourate, index) in sourates" :key="index" :nom="sourate.translated_name.name" :id="sourate.id" @event-sourate-for-aya-random="send_event_send_sourate"></sourate>
        </ul>
        <br>
        <br>
    </div>
</template>

<script>
    import Sourate from './Sourate.vue'
    export default {
        components: { Sourate },
        name: 'nav-bar',
        props: ['sourates'],
        methods: {
            send_event_send_sourate: function (e) {
                this.$emit('event-sourate-for-aya-random', e)
            }
        }
    }
</script>

<style scoped>
    #sticky-sidebar {
        width: 33%;
        height: 100%;
        position: fixed;
        overflow-y: scroll;
    }
</style>