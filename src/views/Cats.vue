<template>
    <div>
        <h1>Cats</h1>
        <b-table striped hover :items="cats">
            <template slot="name" slot-scope="data">
                <!-- `data.value` is the value after formatted by the Formatter -->
                <router-link :to="`/pets/cats/${data.index}`">{{
                    data.value
                }}</router-link>
            </template>
        </b-table>
    </div>
</template>

<script>
export default {
    data() {
        return {};
    },
    computed: {
        cats() {
            return this.$store.state.cats;
        }
    }
};
</script>

