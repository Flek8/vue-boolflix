<template>
    <header>
        <h1>BOOLFLIX</h1>
        <div class="search">
            <input v-model="testoRicerca" type="text" placeholder="Cerca il tuo film preferito...">
            <button @click="inviaRichiesta()">Cerca</button>
        </div>
    </header>
</template>

<script>
export default {
    name: 'MyHeader',
    data() {
        return {
            testoRicerca: ''
        }
    },
    methods: {
        inviaRichiesta() {
            if (this.testoRicerca != '') {
                this.$emit('ricerca', this.testoRicerca);
            }
        }
    }
    
}
</script>

<style scoped lang="scss">
    header {
        background-color: black;
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 15px;

        h1 {
            color: red;
        }

        input {
            padding: 5px;
            margin-right: 5px;
        }

        button {
            background-color: red;
            color: white;
            padding: 5px;
            border-color: red;
            &:hover {
                cursor: pointer;
            }
        }
    }
</style>