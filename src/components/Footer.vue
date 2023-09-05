<template>
    <footer id="footer">
        <p>Make You Burguer &copy; 2023</p>
    </footer >
</template>
<script>
export default {
    name: 'Footer',
}
</script>
<style scoped>
    #footer{
        display: flex;
        justify-content: center;
        align-items: center;

        bottom: 0;

        width: 100%;
        height: 200px;

        color: #fcba03;

        background: #222;
        border-top: 4px solid #111;
    }
</style>