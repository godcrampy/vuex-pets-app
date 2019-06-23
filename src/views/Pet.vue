<template>
    <div>
        <h1>{{ animal.name }} ({{ $route.params.species }})</h1>
        <p style="color:#878787;">{{ animal.notes }}</p>
        <p>Breed: {{ animal.breed }}</p>
        <p>Age: {{ animal.age }} years old</p>
    </div>
</template>

<script>
export default {
    data() {
        return {
            animal: {}
        };
    },
    computed: {
        cats() {
            return this.$store.state.cats;
        },
        dogs() {
            return this.$store.state.dogs;
        }
    },
    mounted() {
        const animal = this[this.$route.params.species][this.$route.params.id];
        this.animal = animal;
    }
};
</script>
