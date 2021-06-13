<template>
  <div id="app">
    <Nav titulo="CADASTRO DE PRODUTOS" />
    <div>
      <div class="row">
        <div>
          <ProductForm :onAddProduto="handleOnAddProduct" />
        </div>
        <div>
          <ProductList :produtos="produtos" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Nav from "./components/Nav";
import ProductForm from "./components/ProductForm";
import ProductList from "./components/ProductList";

export default {
  components: {
    Nav,
    ProductForm,
    ProductList,
  },
  data() {
    return {
      produtos: [
        {
          nome: "Playstation 5",
          preco: "4.500",
          categoria: "Console",
        },
        {
          nome: "Smart TV 65'",
          preco: "6.000",
          categoria: "TV",
        },
        {
          nome: "Iphone XR",
          preco: "3.200",
          categoria: "Smartfone",
        },
      ],
    };
  },
  methods: {
    handleOnAddProduct(produto) {
      this.produtos = this.produtos.concat(produto);
    },
  },
};
</script>