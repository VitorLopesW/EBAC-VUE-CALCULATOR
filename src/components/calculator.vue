<script setup>
    import { reactive } from 'vue'
    //
    let state = reactive({
        a: 0,
        b: 0,
        operation: '+',
        result: '0'
    })
    function updateCalculator(key, value){
        state[key] = value
        console.log(state)
        state['result'] = eval(`${state.a} ${state.operation} ${state.b}`)
    }
</script>

<template>
    <form>
        <h4>Calculadora VueJs</h4>
        <input type="number" @keyup="updateCalculator('a', $event.target.value)"/>

        <select @change="updateCalculator('operation', $event.target.value)">
            <option value="+">+</option>
            <option value="-">-</option>
            <option value="*">*</option>
            <option value="/">/</option>
        </select>

        <input type="number" @keyup="updateCalculator('b', $event.target.value)"/>

        <h5>Resultado: {{ state.result }}</h5>
    </form>
    
</template>

<style>
    form{
        
        width: 300px;
        height: 300px;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        background: teal;
        color: white;
        gap: 10px;
    }
    input, select{
        width: 200px;
    }
    select{
        text-align: center;
    }
</style>