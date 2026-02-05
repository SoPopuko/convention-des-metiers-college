<template>
    <div class="w-50 bg-white rounded border border-yellow-500 m-1">
        <div class="grid grid-cols-9 text-black px-2 pt-1"> 
            <img class="w-6 col-span-1" :src="pokemon!.typeicon" /> 
            <span class="col-span-5 px-1"> {{ pokemon!.name }} </span>
            <span class="col-span-3"> {{ pokemon!.health }}/{{ pokemon!.maxhealth }} </span>
        </div>
        <div v-if="isShaymin == false" class="flex m-2 w-40 h-5 border-slate-950 border-4 rounded-lg">
            <div v-if="pokemon!.health >= 0" v-for="index in pokemon!.health" :key="index" class="h-3 bg-green-500" style="width: 2.1px;" />
        </div>
        <div v-else class="flex m-2 w-40 h-5 border-slate-950 border-4 rounded-lg">
            <div class="h-3 bg-green-500" style="width: 10rem;" :class="{'hidden': pokemon!.health == 0}" />
        </div>
    </div>
</template>

<script lang="ts">
export default {
    props: {
    pokemon: Object,
    isShaymin: Boolean
    }
};
</script>