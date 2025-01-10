<template>
    <div class="w-48 bg-white rounded border border-yellow-500 m-1">
        <div class="grid grid-cols-9 text-black px-2 pt-1"> 
            <img class="w-6 col-span-1" :src="pokemon!.typeicon" /> 
            <span class="col-span-5"> {{ pokemon!.name }} </span>
            <span class="col-span-3"> {{ pokemon!.health }}/{{ pokemon!.maxhealth }} </span>
        </div>
        <div class="flex m-2 w-40 h-5 border-slate-950 border-4 rounded-lg">
            <div v-for="index in pokemon!.health" :key="index" class="h-3 w-2" :class="pokemon!.colorbar" />
        </div>
    </div>
</template>

<script lang="ts">
export default {
    props: {
    pokemon: Object
    }
};
</script>