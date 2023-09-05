<template>
    <div id="burguer-table">
        <div>
            <div>
                <div id="burguer-table-heading">
                    <div class="order-id">#:</div>
                    <div>Cliente:</div>
                    <div>Pão:</div>
                    <div>Carne:</div>
                    <div>Opcionais:</div>
                    <div>Ações:</div>
                </div>
                <div id="burguer-table-rows">
                    <div class="burguer-table-rows">
                        <div class="order-number">
                            1
                        </div>
                        <div>bruno:</div>
                        <div>doce:</div>
                        <div>picanha:</div>
                        <div>
                            <ul>
                                <li>Salame</li>
                                <li>cebola</li>
                            </ul>
                        </div>
                        <div>
                            <select name="status" class="status">
                                <option value="">Selecione</option>
                            </select>
                            <button class="delete-btn">Cancelar</button>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    name: 'Dashboard',
    data() {
        return{
            nome: null,
            pao: null,
            crane: null,
            opcionais:[] 
        }
    },
    methods:{
        async getBurguers(){
            const req = await fetch('http://localhost:3000/burguers')
        }
    },
    // mounted:{

    // }
}
</script>
<style scoped>
    #burguer-table{
        max-width: 1200px;
        margin: 0 auto;
    }
    #burguer-table-heading, #burguer-table-rows, .burguer-table-rows{
        display: flex;
        flex-flow: wrap;
    }

    #burguer-table-heading{
        font-weight: bold;
        padding: 12px;
        border-bottom: 3px solid;
    }
    #burguer-table-heading div, .burguer-table-rows div{
        width: 19%;
    }

    .burguer-table-rows{
        width: 100%;
        padding: 12px;
        border-bottom: 1px solid #ccc;
    }
    #burguer-table-heading .order-id, .burguer-table-rows .order-number{
        width: 5%;
    }

    select{
        padding: 12px 6px;
        margin-right: 12px;
        border-radius: 10px;
    }
    option{
        border-radius: 10px;
    }

    .delete-btn{
        background: #222;
        color: #fcba03;
        font-weight: bold;
        border: 2px solid #222;
        padding: 10px;
        font-size: 16px;
        margin: 0 auto;
        border-radius: 10px;
        cursor: pointer;
        transition: .5s;
    }
    .delete-btn:hover{
        background: transparent;
        color: #222;
    }
</style>