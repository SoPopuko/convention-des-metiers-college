<template>
    <div class="w-48 bg-white rounded border border-yellow-500 m-1">
        <div class="grid grid-cols-9 text-black px-2 pt-1"> 
            <img class="w-6 col-span-1" :src=typeIcon /> 
            <span class="col-span-5"> {{ pokemonName }} </span>
            <span class="col-span-3"> {{ healthPoints }}/73 </span>
        </div>
        <div class="flex m-2 w-40 h-5 border-slate-950 border-4 rounded-lg">
            <div v-for="index in healthPoints" :key="index" class="h-3 w-2" :class="barColor" />
        </div>
    </div>
</template>

<script>
export default {
    props: {
    pokemonName: String,
    typeIcon: String,
    healthPoints: Number,
    barColor: String
    }
};
</script>