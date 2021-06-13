<template>
  <div>
    <form @submit.prevent="onFormSubmit">
      <div>
        <label for="nome"><strong>PRODUTO</strong></label>
        <input
          type="text"
          class="form-control"
          v-model="nome"
          placeholder="Digite o nome do Produto"
        />
        <small><strong>{{isProductNameLimitExceeded}}</strong></small>
      </div>
      <div>
        <label for="nome"><strong>PREÇO</strong></label>
        <input
          type="text"
          class="form-control"
          v-model="preco"
          placeholder="Digite o preço do Produto"
        />
      </div>
      <div>
        <label for="nome"><strong>CATEGORIA</strong></label>
        <input
          type="text"
          class="form-control"
          v-model="categoria"
          placeholder="Digite a categoria do Produto"
        />
      </div>
      <nav>
        <ol>
          <li>
            <strong>Produto:</strong> {{ nome }} <br/> 
            <strong>Preço:</strong> {{ preco }} <br/> 
            <strong>Categoria:</strong> {{ categoria }}
          </li>
        </ol>
      </nav>
      <button type="submit">CADASTRAR</button>
    </form>
  </div>
</template>

<script>


export default {
  data() {
    return {
      nome: "",
      preco: "",
      categoria: "",
      isProductNameLimitExceeded: ""
    };
  },
  props: {
    onAddProduto: Function,
  },
  methods: {
    onFormSubmit() {
      const produto = {
        nome: `${this.nome}`,
        preco: `${this.preco}`,
        categoria: `${this.categoria}`,
      };

      this.onAddProduto(produto);
    },
  },
  watch: {
      nome(){
          if(this.nome.length > 25){
              this.isProductNameLimitExceeded = "Nome do produto tem o limite de 25 caracteres"
          } else {
              this.isProductNameLimitExceeded = ""
          }
      }
  }
};
</script>