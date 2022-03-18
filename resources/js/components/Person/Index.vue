<template>
    <div>
        <table class="table">
            <thead>
            <tr>
                <th scope="col">name</th>
                <th scope="col">age</th>
                <th scope="col">job</th>
                <th scope="col">edit</th>
                <th scope="col">delete</th>
            </tr>
            </thead>
            <tbody>
            <tr v-for="person in people">
                <td>{{ person.name }}</td>
                <td>{{ person.age }}</td>
                <td>{{ person.job }}</td>
                <td>
                    <router-link :to="{name: 'person.edit', params: {'id': person.id}}">edit</router-link>
                </td>
                <td>
                    <a @click.prevent="$store.dispatch('deletePerson', person.id)" href="#" class="btn btn-outline-danger">Delete</a>
                </td>
            </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
export default {
    name: "Index",

    mounted() {
        this.$store.dispatch('getPeople')

    },

    computed: {
        people() {
            return this.$store.getters.people
        }
    }
}
</script>

<style scoped>

</style>
