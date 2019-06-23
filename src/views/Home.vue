<template>
    <div class="home">
        <h1>Adopt a new best friend!</h1>
        <h2>{{ animalsCount }}</h2>
        <button @click="togglePetForm()" class="btn btn-primary">
            Add new Pet
        </button>
        <b-form
            id="form"
            @submit.prevent="onSubmit"
            @reset="onReset"
            v-if="showPetForm"
        >
            <b-form-group
                id="input-group-1"
                label="Pet's Name:"
                label-for="input-1"
            >
                <b-form-input
                    id="input-2"
                    v-model="formData.name"
                    required
                    placeholder="Enter name"
                ></b-form-input>
            </b-form-group>

            <b-form-group
                id="input-group-2"
                label="Species:"
                label-for="input-3"
            >
                <b-form-select
                    id="input-1"
                    v-model="formData.species"
                    :options="['cats', 'dogs']"
                    required
                ></b-form-select>
            </b-form-group>
            <b-form-group id="input-group-1" label="Age:" label-for="input-1">
                <b-form-input
                    type="number"
                    id="input-2"
                    v-model="formData.age"
                    required
                    placeholder="Enter name"
                ></b-form-input>
            </b-form-group>

            <b-button type="submit" variant="primary">Submit</b-button>
            <b-button type="reset" variant="danger">Reset</b-button>
        </b-form>
    </div>
</template>

<script>
import { mapActions, mapGetters } from "vuex";
export default {
    data() {
        return {
            showPetForm: false,
            formData: {
                name: "",
                age: 0,
                species: null
            }
        };
    },
    computed: {
        ...mapGetters(["animalsCount"])
    },
    methods: {
        ...mapActions(["addPet"]),
        togglePetForm() {
            this.showPetForm = !this.showPetForm;
        },
        onSubmit() {
            const payload = {
                species: this.formData.species,
                pet: {
                    name: this.formData.name,
                    age: this.formData.age
                }
            };
            this.addPet(payload);
            this.onReset();
        },
        onReset() {
            this.formData = { name: "", age: 0, species: null };
        }
    }
};
</script>

<style scoped>
#form {
    margin-left: 25em;
    margin-right: 25em;
}
</style>

