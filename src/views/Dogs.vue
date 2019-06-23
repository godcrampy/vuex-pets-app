<template>
    <div>
        <h1>Dogs</h1>
        <b-table striped hover :items="dogs">
            <template slot="name" slot-scope="data">
                <!-- `data.value` is the value after formatted by the Formatter -->
                <router-link :to="`/pets/dogs/${data.index}`">{{
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
        dogs() {
            return this.$store.state.dogs;
        }
    }
};
</script>

