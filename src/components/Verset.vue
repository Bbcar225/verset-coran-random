<template>
    <section class="vh-100">
        <div class="container h-100">
            <div class="row d-flex justify-content-center align-items-center h-100">
                <div class="card shadow bg-body rounded">
                    <div class="card-body p-5">
                        <div class="d-flex justify-content-center mb-4">
                            <img src="../assets/quran (1).png" class="rounded-circle shadow-1-strong" width="100" height="100"/>
                        </div>
                        <figure class="text-center mb-0" v-if="aya">
                            <blockquote class="blockquote mb-4">
                                <p>
                                    <span class="font-italic fw-bold">
                                        {{ aya.translation }}
                                    </span>
                                </p>
                            </blockquote>
                            <figcaption class="blockquote-footer mb-0 fw-bolder">
                                {{ aya.sura }} : <cite title="Source Title">{{ aya.aya }}</cite>
                            </figcaption>
                        </figure>
                        
                        <figure class="text-center mb-0" v-else>
                            <blockquote class="blockquote mb-4">
                                <p class="card-text placeholder-glow">
                                    <span class="placeholder col-7"></span>
                                    <span class="placeholder col-4"></span>
                                    <span class="placeholder col-4"></span>
                                    <span class="placeholder col-6"></span>
                                    <span class="placeholder col-8"></span>
                                </p>
                            </blockquote>
                            <figcaption class="blockquote-footer mb-0 fw-bolder text-center">
                                <p class="placeholder-glow">
                                    <span class="placeholder col-2"></span>
                                </p>
                            </figcaption>
                        </figure>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script>
    export default {
        name: 'verset',
        props: ['aya'],      
    }
</script>