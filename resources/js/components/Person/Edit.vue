<template>
    <div class="w-50" v-if="person">
        <div class="mb-3">
            <input type="text" v-model="person.name" placeholder="name" class="form-control">
        </div>
        <div class="mb-3">
            <input type="number" v-model="person.age" placeholder="age" class="form-control">
        </div>
        <div class="mb-3">
            <input type="text" v-model="person.job" placeholder="job" class="form-control">
        </div>
        <div class="mb-3">
            <input type="submit" :disabled="!isDisabled" @click.prevent="$store.dispatch('update', {id: person.id,name: person.name, age: person.age, job: person.job})" value="Update" class="btn btn-primary">
        </div>
    </div>
</template>

<script>

import person from "../../store/modules/person";

export default {
    name: "Edit",

    mounted() {
        this.$store.dispatch('getPerson', this.$route.params.id);
    },

    computed: {
        isDisabled() {
            return this.$store.getters.isDisabled
        },
        person() {
            return this.$store.getters.person
        }
    }
}
</script>

<style scoped>

</style>
