<template>
    <div>
        <h2 class="text-blue-600">Wpisy na bloga</h2>
        <div class="w-100 flex flex-row-reverse">
            <button @click="pobierzWpisy" class="float-right bg-blue-600 rounded-sm text-white p-4">refresh</button>
        </div>
        <div class="grid mx-6 gap-4 my-4">
            <div v-for="(wpis, index) in wpisy" class="grid drop-shadow-xl bg-stone-300 p-4">
                <p>{{ wpis }}</p>
             </div>
        <div class="flex justify-center flex-col">
            <input v-model="nowyBlog" class="border-2 border-blue-600 p-4" type="text">
            <button @click="dodajWpisy" class="float-right bg-blue-600 rounded-sm text-white p-4">dodaj</button>
        </div>
        </div>
    </div>
</template>

<script>
import { dzien3_backend } from 'declarations/dzien3_backend/index';

export default {
    data() {
        return {
            wpisy: [],
            nowyBlog: ""
        }
    },
    methods: {
        async dodajWpisy() {
            await dzien3_backend.dodaj_wpis(this.nowyBlog);
        },
        async pobierzWpisy() {
            this.wpisy = await dzien3_backend.odczytaj_wpisy();
        }
    },

}
</script>