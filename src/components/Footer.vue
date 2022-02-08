<template>

    <footer id="footer">
        
        <p>Make your burger &copy; 2022</p>
        
        <a href="https://twitter.com/esq1z0" target="_blank"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/twitter/twitter-original.svg" id="logo"/></a>

        <a href="https://github.com/UT0P1C" target="_blank"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/github/github-original.svg" id="logo"/></a>

    </footer>

</template>

<script>
export default {
    name: 'Footer'    
}

</script>

<style scoped>

#footer{
    height: 200px;
    background-color: #222;
    border-top: 4px solid #111;
    color: #FACB03;
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100%;

}

#logo{
    width: 30px;
    height: 20px;
    margin: 5px;
}

</style>
