<template>

    <div class="main-banner">

        <h1><a href="#make-your-hamburger">Make your burger</a></h1>
        
    </div>

</template>

<script>
export default {
    name: 'Banner'
}
</script>

<style scoped>

.main-banner{
    background-image: url('/img/burger.jpg');
    background-position: 0 -250px;
    background-size: cover;
    height: 500px;
    display: flex;
    align-items: center;
    justify-content: flex-start;
}

.main-banner h1{
    color: #fff;
    background-color: #222;
    font-size: 60px;
    padding: 20px 40px;
}

.main-banner a {
    color: #fff;
    text-decoration: none;
}

</style>