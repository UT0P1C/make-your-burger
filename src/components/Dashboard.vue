<template>

    <div id="burger-table">

        <div>

            <div id="burger-table-heading">

                <div class="order-id">#</div>
                <div>Nome:</div>
                <div>Pão:</div>
                <div>Carne:</div>
                <div>Opcionais:</div>
                <div>Ações:</div>

            </div>

        </div>
        
        <div id="burger-table-rows">

            <div class="burger-table-row" v-for="(burger,index) in burgers" :key="index">

                <div class="order-num">{{burger.id}}</div>
                <div>{{burger.name}}</div>
                <div>{{burger.bread}}</div>
                <div>{{burger.meat}}</div>
                <div>

                    <ul v-for="(opcional, index) in burger.optional" :key="index">
                        <li>{{opcional}}</li>
                    </ul>
                </div>

                <div>

                    <select name="status" class="status-order">

                        <option :value="status.tipo" v-for="(status, index) in statuses" :key="index" :selected="burger.status == status.tipo">{{status.tipo}}</option>

                    </select>

                    <button class="btn-delete" v-on:click="deletePedido">Cancelar</button>

                </div>

            </div>

            

        </div>

    </div>

</template>

<script>

const axios = require('axios');

export default {
    name: "Dashboard",
    data(){
        return{
            burgers: null,
            burger_id: null,
            statuses: []
        }
    },
    methods: {
        async getPedidos(){
            //PUXA OS PEDIDOS
            const req = await axios.get('http://localhost:3000/burgers');

            const data = await req.data;

            this.burgers = data;

            this.getStatus();

        },
        async getStatus(){
            //PUXA OS STATUS
            const req = await axios.get('http://localhost:3000/status');
            const data = await req.data;

            this.statuses = data;
        },
        async deletePedido(){

        }
    },
    mounted(){
        this.getPedidos();
    }
}
</script>

<style scoped>

#burger-table{
    max-width: 1200px;
    margin: 0 auto;
}

#burger-table-heading,
#burger-table-rows,
.burger-table-row{
    display: flex;
    flex-wrap: wrap;
}

#burger-table-heading{
    font-weight: bold;
    padding: 12px;
    border-bottom: 3px solid #333;
}

#burger-table-heading div,
.burger-table-row div{
    width: 19%;
}

.burger-table-row{
    width: 100%;
    padding: 12px;
    border-bottom: 1px solid #CCC;
}

#burger-table-heading .order-id,
.burger-table-row .order-num{
    width: 5%;
}

select{
    padding: 12px 6px;
    margin-right: 6px;
}

.btn-delete {
    background-color: #222;
    color: #FCBA03;
    font-weight: bold;
    border: 2px solid #222;
    padding: 10px;
    font-size: 16px;
    margin: 0 auto;
    cursor: pointer;
    transition: .5s;
}

.btn-delete:hover{
    background-color: transparent;
    color: #222;
}

</style>