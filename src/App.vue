<template>
    <div id="app">
        <h1>Problema de Monty Hall</h1>
        <div class="form">
            <div v-if="!started">
                <label for="portsAmount">Quantas Portas?</label>
                <input type="text" id="portsAmount" size="3"
                    v-model.number="portsAmount">
            </div>
            <div v-if="!started">
                <label for="selectedPort">Qual a porta Premiada?</label>
                <input type="text" id="selectedPort" size="3"
                    v-model.number="selectedPort">
            </div>
            <button @click="started = !started" class="button">
                {{stTxt}}
            </button>

            <div class="doors" v-if="started">
                <div v-for="port in portsAmount" :key="port">
                    <Door :number="port" :hasGift="selectedPort === port"/>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import Door from './Components/Door'
export default {
    name: 'App',
    components: {Door},
    data: function () {
        return {
            started: false,
            portsAmount: 3,
            selectedPort: null
        }
    },
    computed: {
        stTxt() {
            return this.started ? 'Reiniciar' : 'Iniciar'
        }
    }
}
</script>

<style>
*{
    box-sizing: border-box;
    font-family: 'Montserrat', monospace;
}
body {
    background: linear-gradient(to right, #0f0c29, #302b63, #24243e);
    color: #fff;
}
#app {
    display: flex;
    flex-direction: column;
    align-items: center;

}
#app h1 {
    border: 1px solid #000;
    background-color: #0004;
    padding: 20px;
    margin-bottom: 60px;
}

.form {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    margin-bottom: 40px;
}

.form, .form input, .form button {
    margin-bottom: 10px;
    font-size: 2rem;
}

.doors {
    align-self: stretch;

    display: flex;

    justify-content: space-around;

    flex-wrap: wrap;
    
}
</style>
