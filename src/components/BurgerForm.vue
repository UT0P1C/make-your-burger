<template>

    <div class="burger-form">

        <h1>Monte Seu Burger</h1>

        <p>mensagem</p>

        <div class="input-container">

            <label for="name">Nome:</label>

            <input type="text" name="name" id="name" v-model="name" placeholder="Digite Seu nome">

        </div>

        <div class="input-container">

            <label for="bread">Escolha o pão:</label>

            <select name="bread" id="bread" v-model="bread">

                <option value="">Escolha seu pão</option>

                <option value="integral">integral</option>

            </select>

        </div>

        <div class="input-container">

            <label for="meat">Escolha a carne:</label>

            <select name="meat" id="meat" v-model="meat">

                <option value="">Escolha uma carne</option>

                <option value="maminha">maminha</option>

            </select>

        </div>

        <div id="optional-container" class="input-container">

            <label id="optional-title" for="optional">Escolha os opcionais</label>

            <div class="checkbox-container">

                <input type="checkbox" name="optional" id="optional" value="salame" v-model="optional">

                <span>salame</span>

            </div>

        </div>
        

        <div class="input-container">

            <input type="submit" class="submit-btn" value="Monte meu burger">

        </div>

    </div>

</template>

<script>
export default {
    name: 'BurgerForm'
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

.checkbox-container spann {
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