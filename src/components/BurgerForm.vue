<template>

    <div class="burger-form" id="make-your-hamburger">

        <h1>Monte Seu Burger</h1>

        <Message 
        :msg="msg"
        v-show="msg"
        />

        <form id="burger-form" @submit="createHamburger">

            <div class="input-container">

                <label for="name">Nome:</label>

                <input type="text" name="name" id="name" v-model="name" placeholder="Digite Seu nome">

            </div>

            <div class="input-container">

                <label for="bread">Escolha o pão:</label>

                <select name="bread" id="bread" v-model="bread">

                    <option value="">Escolha seu pão</option>

                    <option :value="bread.tipo" v-for="bread in breads" :key="bread.id">
                        {{bread.tipo}}</option>

                </select>

            </div>

            <div class="input-container">

                <label for="meat">Escolha a carne:</label>

                <select name="meat" id="meat" v-model="meat">

                    <option value="">Escolha uma carne</option>

                    <option :value="meat.tipo" v-for="meat in meats" :key="meat.id">{{meat.tipo}}</option>

                </select>

            </div>

            <div id="optional-container" class="input-container">

                <label id="optional-title" for="optional">Escolha os opcionais</label>

                <div class="checkbox-container" v-for="option in optionaldata" :key="option.id">

                    <input type="checkbox" name="optional" id="optional" :value="option.tipo" v-model="optional">

                    <span>{{option.tipo}}</span>

                </div>

            </div>
            

            <div class="input-container">

                <input type="submit" class="submit-btn" value="Monte meu burger">

            </div>
        </form>

    </div>

</template>

<script>

import Message from './Message.vue';

const axios = require('axios');

export default {
    name: 'BurgerForm',
    data(){
        return{
            breads: null,
            meats: null,
            optionaldata: null,
            name: null,
            bread: null,
            meat: null,
            optional: [],
            msg: null
        }
    },
    mounted(){
        this.getIngredients();
    },
    methods: {
        async getIngredients(){
            const req = await axios.get('http://localhost:3000/ingredientes');
            const data = await req.data;

            this.breads = data.paes;
            this.meats = data.carnes;
            this.optionaldata = data.opcionais;
        },
        async createHamburger(e){

            e.preventDefault();

            //CRIAR DADOS PARA ENVIAR PARA A DB

            const data = {
                name: this.name,
                bread: this.bread,
                meat: this.meat,
                optional: Array.from(this.optional),
                status: "Solicitado"
            }

            //CONVERTE OS DADOS PARA STRING EM JSON E ENVIA A DB

            const dataJson = JSON.stringify(data);

            const req = await fetch('http://localhost:3000/burgers', {
                method: "POST",
                headers: {"Content-type" : "application/JSON"},
                body: dataJson
            });

            const res = await req.json();

            //EXIBIR UM ALERTA

            this.msg = `Pedido N°${res.id} realizado com sucesso!`;

            //LIMPAR O ALERTA

            setTimeout(() => this.msg = "", 3000);

            
            //LIMPAR CAMPOS

            this.cleanForm();




        },
        async cleanForm(){
            this.name = "";
            this.bread = "";
            this.meat = "";
            this.optional = "";
        }
    },
    components:{
        Message
    }
}
</script>

<style scoped>

.burger-form{
    max-width: 400px;
    margin: 0 auto;
}

.input-container{
    display: flex;
    flex-direction: column;
    margin-bottom: 20px;
}

label{
    font-weight: bold;
    margin-bottom: 15px;
    color: #222;
    padding: 5px 10px;
    border-left: 4px solid #FCBA03;

}

input, select{
    padding: 5px 10px;
    width: 300px;
}

#optional-container{
    flex-direction: row;
    flex-wrap: wrap;
}

#optional-title{
    width: 100%;
}

.checkbox-container{
    display: flex;
    align-items: flex-start;
    width: 50%;
    margin-bottom: 20px;
}

.checkbox-container span,
.checkbox-container input {
    width: auto;

}

.checkbox-container span {
    margin-left: 6px;
    font-weight: bold;
}

.submit-btn{
    background-color: #222;
    color: #FCBA03;
    font-weight: bold;
    border: 2px solid #222;
    padding: 10px;
    font-size: 16px;
    cursor: pointer;
    transition: .5s;
}

.submit-btn:hover{
    background-color: transparent;
    color: #222;
}

</style>