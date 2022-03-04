<template>
    <div id="app" class="container-fluid">
        <div class="row">
            <div class="col-4 text-center">
                <h4 class="text-uppercase my-2 text-warning fw-bold">Versets coranique</h4>
                <nav-bar :sourates="sourates" @event-sourate-for-aya-random="send_event_send_sourate"></nav-bar>
            </div>
            
            <div class="col-8">
                <verset :aya="aya"></verset>
            </div>
        </div>
    </div>
</template>

<script>
    import axios from 'axios'
    import NavBar from './components/Nav-bar.vue'
    import Verset from './components/Verset.vue'
    
    export default {
        components: { Verset, NavBar },
        name: 'App',
        data: function () {
            return {
                sourates: [],
                aya: null
            }
        },
        mounted: function () {
            axios.get('https://api.quran.com/api/v4/chapters?language=fr').then((response_sourates) => {
                this.sourates = response_sourates.data.chapters
            })
            
            var number_sourate = Math.floor(Math.random() * 114) + 1;
            
            axios.get(`https://quranenc.com/api/v1/translation/sura/french_montada/${number_sourate}`).then((response_sourate) => {
                var number_aya = Math.floor(Math.random() * response_sourate.data.result.length) + 1;
                
                axios.get(`https://quranenc.com/api/v1/translation/aya/french_montada/${number_sourate}/${number_aya}`).then((response_aya) => {
                    this.aya = response_aya.data.result
                })
            })
        },
        methods: {
            send_event_send_sourate: function (e) {
                this.aya = null

                axios.get(`https://quranenc.com/api/v1/translation/sura/french_montada/${e}`).then((response_sourate) => {
                    var number_aya = Math.floor(Math.random() * response_sourate.data.result.length) + 1;
                    
                    axios.get(`https://quranenc.com/api/v1/translation/aya/french_montada/${e}/${number_aya}`).then((response_aya) => {
                        this.aya = response_aya.data.result
                    })
                })
            }
        }
    }
</script>
