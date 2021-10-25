<template>
    <div class="modal">
        <div>
            <h1 id="header">You're an alienzombie.</h1>
            <p>
                In order to survive on Earth, you have to pretend to be a human on this
                planet. You took over the body of a nearby hooman, but the trouble is, their
                best friend showed up!
            </p>
            <p>
                They look suspicious. Answer the questions right to make sure identity is
                kept secret!
            </p>
            <h2>Witch hooman do you want to be ?</h2>

            <p v-for="option of characterChoices" :key="option" class="character-choices">
                <input type="radio" :id="option" v-model="characterinput" :value="option">
                <label :for="option">{{ option }}</label>
            </p>

            <button @click="pickCharacter">pick your character!</button>
        </div>
    </div>
</template>

<script>
import { mapState } from 'vuex';

export default {
    data() {
        return {
            characterinput: ''
        }
    },
    computed: {
        ...mapState([
            'characterChoices',
        ])
    },

    methods: {
        pickCharacter() {
            this.$store.commit('PICK_CHARACTER', this.characterinput);
            this.$store.commit('UPDATE_UISTATE', 'characterChosen');
        }
    },
};
</script>

<style scoped>

</style>