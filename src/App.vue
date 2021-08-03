<template>
  <div id="app" class="container">

    <div id="add_del" >
      <a class="waves-effect waves-light btn-small modal-trigger green darken-0"><i class="fal fa-plus"></i> Novo</a>
      
      <a class="waves-effect waves-light red lighten-2 btn-small excluir"><i class="far fa-trash-alt"></i> Excluir</a>
    
    </div>

    <div id="titleProd">
      <span>Gerenciar Produto</span>
      <div id="pesquisar">
        <input type="text" placeholder="Nome do Produto...">
        <a id="btnPesquisar" class="waves-effect waves-light btn-small green darken-0"><i class="fal fa-search"></i>Pesquisar</a>
      </div>
    </div>

    <div>
      <table class="table">
        <thead class="table-secondary">
          <tr id="titleTable">
            <th></th>
            <th scope="col">Codigo<span class="material-icons">swap_vert</span></th>
            <th scope="col">Nome<span class="material-icons">swap_vert</span></th>
            <th scope="col">Preço<span class="material-icons">swap_vert</span></th>
            <th scope="col">Categoria<span class="material-icons">swap_vert</span></th>
            <th scope="col">Status<span class="material-icons">swap_vert</span></th>
            <th></th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="produto of produtos" :key="produto.id">
            <p>
              <label>
                <input type="checkbox"/>
                <span></span>
              </label>
            </p>
            <td>{{produto.codigo}}</td>
            <td>{{produto.nome}}</td>
            <td>$ {{produto.preco}}</td>
            <td>{{produto.categoria}}</td>
            <td><strong>{{produto.status}}</strong></td>
            <td>
              <a class="btn-floating btn-small waves-effect waves-light green darken-0"><i class="material-icons">edit</i></a>
              <a id="btnTableDel" class="btn-floating btn-small waves-effect waves-light orange accent-2 delete"><i class="far fa-trash-alt"></i></a>
            </td>
          </tr>
        </tbody>
      </table>
    </div>

    <div id="pagination">
      <ul class="pagination">
        <li class="disabled"><a href="#!"><i class="material-icons">chevron_left</i></a></li>
        <li class="active"><a href="#!">1</a></li>
        <li class="waves-effect"><a href="#!">2</a></li>
        <li class="waves-effect"><a href="#!">3</a></li>
        <li class="waves-effect"><a href="#!">4</a></li>
        <li class="waves-effect"><a href="#!">5</a></li>
        <li class="waves-effect"><a href="#!"><i class="material-icons">chevron_right</i></a></li>
      </ul>
    </div>
  </div>

</template>



<script>
import Produto from './services/produtos'

export default {
  data () {
    return{
      produtos: []
    }
  },
  
  mounted(){
    Produto.listar().then(resposta => {
      console.log(resposta.data)
      this.produtos = resposta.data
    })
  },
  
}
</script>




<style scoped>
#app {
  margin-top: 20px;
}

#titleProd{
  background-color: rgba(221, 220, 220, 0.356);
  border: 1px solid rgba(172, 171, 171, 0.438);
  padding: 15px;
  border-radius: 4px;
  margin-top: 15px;
  justify-content: space-between;
  display: flex;
  align-items: center;
}

#pesquisar{
  display: flex;
  margin-left: auto;
}

#add_del{
  margin-top: 20px;
  background-color: rgba(221, 220, 220, 0.356);
  border: 1px solid rgba(172, 171, 171, 0.438);
  padding: 15px;
  border-radius: 4px;
}

#add_del .excluir{
  margin-left: 10px;
}

.table>:not(:last-child)>:last-child>* {
    border-bottom-color: #8080807d;
    background-color: rgba(221, 220, 220, 0.356);
}


#titleProd span{
  font-size: 20px;
  justify-content:space-between;
  display: flex;
  color: grey;
}

#pesquisar input[data-v-7ba5bd90]{
  padding-left: 10px;
}

#titleTable{
  color: grey;
}

#pesquisar input{
  border-radius: 4px;
  height: 2rem;
  width: 100%;
  font-size: 16px;          
  box-sizing: content-box;
  background-color: white;
  border: 1px solid #8080807d;
  outline: none;
  height: 2rem;
  width: 70%;
}

#btnPesquisar{
  height: 2rem;
  display: flex;
  align-items: center;
  justify-content: center;
  justify-items: center;
  width: 40%;
  padding: 0 20px;
}


#btnTableDel{
  margin-left: 10px;
}


#pagination {
  display: flex;
  justify-content: center;
  margin-top: 30px;
  
}


</style>
