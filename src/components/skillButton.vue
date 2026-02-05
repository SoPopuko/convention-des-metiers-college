<template>
    <div
        {{ pkmSkillAtqName }} - {{ pkmSkillDgts }}
    </div>
</template>

<script lang="ts">
export default {
    props: {
    pkmSkillAtqName: String,
    pkmSkillDgts: Number
    }
};
</script>