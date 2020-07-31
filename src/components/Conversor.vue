<template>
    <div class="conversor">
        <h2> {{ moedaA }} para {{ moedaB }} </h2>
    
        <input 
            type="text" 
            v-model="moedaA_value"
            :placeholder="moedaA" 
        />

        <input 
            type="button" 
            value="Converter"
            v-on:click="converter"
        />
    
        <h2> {{moedaB_value}} R$ </h2>
    </div> 
</template>

<script>
export default {
    name: 'Conversor',
    props: [ 'moedaA', 'moedaB'],

    data(){
        return{
            moedaA_value: '',
            moedaB_value: 0
        }
    },

    methods:{
        converter(){
            let de_para = this.moedaA + "-" + this.moedaB
            let url = `https://economia.awesomeapi.com.br/all/${de_para}`
            const typeMoeda = 'USD'

            fetch(url)
                .then(res => {return res.json()})
                .then(json => {
                    //console.log(json)
                    let cotacao = json[typeMoeda].ask
                    this.moedaB_value = (cotacao * parseFloat(this.moedaA_value)).toFixed(2)
                })
        }
    }
}
</script>

<style scoped>

</style>>

