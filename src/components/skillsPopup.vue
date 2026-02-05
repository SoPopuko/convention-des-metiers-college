<template>
    <div class="bg-red-900 rounded border border-red-500 text-black m-1 px-2 py-1">
        <h3 class="text-red-200"> Choisis une compétence</h3>
        <hr />
        <div v-for="pkmSkill in pkmSkills" @click="SendSkillInfos(pkmSkill)" class="cursor-pointer m-1 p-1 bg-red-400 rounded border border-red-200">
            {{ pkmSkill.name }} - {{ pkmSkill.dgts }} de dégats
        </div>
    </div>
</template>

<script lang="ts">
export default {
    props: {
    pkmSkills: Object
    },
    data() {
        return {
            skillInfo: []
        };
    },
    methods: {
        SendSkillInfos(pkmSkillInfo: any) {
            this.skillInfo = { name: pkmSkillInfo.name, type: pkmSkillInfo.type, dgts: pkmSkillInfo.dgts}
            this.$emit('sendChoosenSkill', this.skillInfo)
        }
    }
};
</script>