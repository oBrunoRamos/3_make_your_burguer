<template>
    <div id="main-banner">
        <h1>Make Your Burguer</h1>
    </div>
</template>
<script>
    export default {
        name: 'BurguerBanner',
        
    }
</script>
<style scoped>
    #main-banner{
        display: flex;
        align-items: center;
        justify-content: flex-start;

        height: 790px;
        width: 100%;

        background-image: url('../../public/img/burger.jpg');
        background-position: 0 -250px;
        background-size: cover;
    }
    #main-banner h1{
        color: #fff;

        text-align: center;
        font-size: 60px;
        background: #222;
        padding: 20px 40px;

    }
</style>