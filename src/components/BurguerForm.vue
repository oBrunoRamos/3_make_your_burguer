<template>
    <div>
        <p>Componente de mensagem</p>
        <div>
            <form id="burguer-form" @submit="createBurguer">
                <div class="input-container">
                    <label for="nome">Nome do Cliente:</label>
                    <input type="text" id="nome" name="nome" v-model="nome" placeholder="Digite seu nome">
                </div>
                <div class="input-container">
                    <label for="pao">Escolha o pão:</label>
                    <select type="text" id="pao" name="pao" v-model="pao">
                        <option selected>Selecione seu pão</option>
                        <option v-for="pao in paesdata" :key="pao.id" :value="pao.tipo">{{ pao.tipo }}</option>
                        
                    </select>
                </div>
                <div class="input-container">
                    <label for="carne">Escolha a carne:</label>
                    <select type="text" id="carne" name="carne" v-model="carne">
                        <option selected>Selecione o tipo de carne</option>
                    <option v-for="carne in carnesdata" :key="carne.id" :value="carne.tipo">{{ carne.tipo }}</option>
                    </select>
                </div>
                <div id="opcionais-container" class="input-container">
                    <label id="opcionais-title" for="opcionais">Escolha aos opcionais:</label>
                    <div class="checkbox-container" v-for="opcionaldata in opcionaisdata" :key="opcionaldata.id">
                        <input style="cursor: pointer;" type="checkbox" name="opcionais" v-model="opcionais" :value="opcionaldata.tipo">
                        <span>{{ opcionaldata.tipo }}</span>
                    </div>
                </div>
                <div class="input-container">
                    <input type="submit" class="submit-btn" value="Criar meu burguer">
                </div>
            </form>
        </div>
    </div>
</template>

<script>
export default{
    name: 'BurguerForm',
    data(){
        return{
            paesdata: null, 
            carnesdata: null,
            opcionaisdata: null,

            nome: null,
            pao: null,
            carne: null,
            opcionais: [],

            status: 'Solicitado',
            msg: null
        }
    },
    methods:{
        async getIngredients(){
            const req = await fetch('http://localhost:3000/ingredientes');
            const data = await req.json();

            this.paesdata = data.paes;
            this.carnesdata = data.carnes;
            this.opcionaisdata = data.opcionais;
            
        },
        async createBurguer(event){
            event.preventDefault()

            
            const data ={
                nome: this.nome,
                carne: this.carne,
                pao: this.pao,
                opcionais: Array.from(this.opcionais),
                status: 'Solicitado'
            }
            const dataJson = JSON.stringify(data)

            const req = await fetch("http://localhost:3000/burgers", {
                method: "POST",
                headers: {"Content-Type": "application/json"},
                body: dataJson
            })
        
            const res = await req.json();

            this.pao='';
            this.nome='';
            this.carne='';
            this.opcionais='';
        }
    },
    mounted(){
        this.getIngredients()
    }
}
</script>
<style scoped>
    #burguer-form{
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
        border-radius: 3px;
        border-left: solid 4px #fcba03;
    }

    input, select{
        padding: 5px 10px;
        width: 300px;

        border-radius: 10px;
    }

    #opcionais-container{
        flex-flow: row wrap;
    }

    #opcionais-title{
        width: 100%;
    }
    .checkbox-container{
        display: flex;
        align-items: flex-start;
        width: 50%;
        margin-bottom: 20px;
    }
    .checkbox-container span, .checkbox-container input{
        width: auto;
    }
    .checkbox-container span{
        margin-left: 6px;
        font-weight: bold;
    }
    .submit-btn{
        background: #222;
        color: #fcba03;
        font-weight: bold;
        border: 2px solid #222;
        padding: 10px;
        font-size: 16px;
        margin: 0 auto;
        cursor: pointer;
        transition: .5s;
    }
    .submit-btn:hover{
        background: transparent;
        color: #222;
    }
</style>