<script>
import { store } from "../store";

export default {
    data() {
        return {
            store,
        };
    },
    computed: {
        filteredSprites() {
            if (!this.store.results || !this.store.results.sprites) {
                return {};
            }
            return Object.fromEntries(
                Object.entries(this.store.results.sprites)
                    .filter(([key, value]) => typeof value === 'string' && key.includes('default'))
            );
        }
    }
};
</script>

<template>
    <div class="h-100">
        <div class=" w-100 h-100 d-flex flex-column justify-content-center align-items-center">
            <!-- Controlla se store.results e store.results.sprites sono validi -->
            <div v-if="store.results && store.results.sprites" id="carousel" class="carousel slide carousel-fade w-100">
                <div class="carousel-inner">
                    <div
                        v-for="(image, key) in filteredSprites"
                        :key="key"
                        class="carousel-item"
                        :class="{'active': key === 'front_default'}"
                    >
                        <img :src="image" class="d-block w-100 m-auto h-100" alt="Image" />
                    </div>
                </div>
                <!-- Controlli di navigazione -->
                <button class="carousel-control-prev" type="button" data-bs-target="#carousel" data-bs-slide="prev">
                    <span class="carousel-control-prev-icon" aria-hidden="true"></span>
                    <span class="visually-hidden">Previous</span>
                </button>
                <button class="carousel-control-next" type="button" data-bs-target="#carousel" data-bs-slide="next">
                    <span class="carousel-control-next-icon" aria-hidden="true"></span>
                    <span class="visually-hidden">Next</span>
                </button>
            </div>
            <!-- Messaggio di fallback -->
            <p class="m-0 text-center fw-bold fs-5" v-else>Nessuna immagine disponibile</p>
        </div>
    </div>
</template>

<style scoped lang="scss">

</style>