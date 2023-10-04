<template>
    <div id="burguer-table">
      <div>
        <div id="burguer-table-heading">
            <div class="order-id">#:</div>
            <div>Cliente</div>
            <div>Pao</div>
            <div>Carne</div>
            <div>Opcionais:</div>
            <div>Ações</div>
        </div>
      </div>
      <div id="burguer-table-rows">
        <div class="burguer-table-row" v-for="burger in burgers" :key="burger.id">
            <div class="order-number"> {{ burger.id }}</div>
            <div>{{ burger.nome }}</div>
            <div>{{burger.pao}}</div>
            <div>{{ burger.carne }}</div>
            <div>
                <ul>
                    <li v-for="(opcional, index) in burger.opcionais" :key="index">{{opcional}}</li>
                   
               </ul>
            </div>
            <div>
                <select name="status" id="status">
                    <option value="">Selecione </option>
                </select>
                <button class="delete-btn"> Cancelar</button>
            </div>
        </div>
       
      </div>
    </div>

</template>

<script>
export default{
    name:'Dashboard',
    data(){
        return{
            burgers:null,
            burger_id:null,
            status: []
        }
    },
    methods: {
        async getPedidos(){
                const req = await fetch('http://localhost:3000/burgers');
                const data = await req.json();

                this.burgers = data; 
                // verificar se é assim mesmo
            console.log(this.burgers);
        }
    },
    mounted(){
        this.getPedidos(); 
    }
}

</script>

<style scoped>

#burguer-table {
    max-width: 1200px;
    margin: 0 auto;
  }

  #burguer-table-heading,
  #burguer-table-rows,
  .burguer-table-row {
    display: flex;
    flex-wrap: wrap;
  }

  #burguer-table-heading {
    font-weight: bold;
    padding: 12px;
    border-bottom: 3px solid #333;
  }

  .burguer-table-row {
    width: 100%;
    padding: 12px;
    border-bottom: 1px solid #CCC;
  }

  #burguer-table-heading div,
  .burguer-table-row div {
    width: 19%;
  }

  #burguer-table-heading .order-id,
  .burguer-table-row .order-number {
    width: 5%;
  }

  select {
    padding: 12px 6px;
    margin-right: 12px;
  }

  .delete-btn {
    background-color: #222;
    color:#fcba03;
    font-weight: bold;
    border: 2px solid #222;
    padding: 10px;
    font-size: 16px;
    margin: 0 auto;
    cursor: pointer;
    transition: .5s;
  }
  
  .delete-btn:hover {
    background-color: transparent;
    color: #222;
  }

</style>