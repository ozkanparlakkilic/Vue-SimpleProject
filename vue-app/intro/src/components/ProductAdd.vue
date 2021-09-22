<template>
  <div id="addForm" class="container">
    <form @submit.prevent="handleAdd()">
      <div class="form-group">
        <label for="categoryId">Category Id</label>
        <input v-model="product.categoryId" type="text" class="form-control" id="categoryId" />
      </div>
      <div class="form-group">
        <label for="productName">Product Name</label>
        <input v-model="product.productName" type="text" class="form-control" id="productName" />
      </div>
      <div class="form-group">
        <label for="quantityPerUnit">Quantity Per Unit</label>
        <input v-model="product.quantityPerUnit" type="text" class="form-control" id="quantityPerUnit" />
      </div>
      <div class="form-group">
        <label for="unitPrice">unit Price</label>
        <input v-model="product.unitPrice" type="text" class="form-control" id="unitPrice" />
      </div>
      <div class="form-group">
        <label for="unitsInStock">Units In Stock</label>
        <input v-model="product.unitsInStock" type="text" class="form-control" id="unitsInStock" />
      </div>
      <button type="submit" class="btn btn-sm btn-primary">Add</button>
    </form>
  </div>
</template>

<script>
export default {
  name: "product-add",
  data() {
    return {
      product: {
        id: "",
        categoryId: "",
        productName: "",
        quantityPerUnit: "",
        unitPrice: "",
        unitsInStock: "",
      },
    };
  },
  methods:{
      handleAdd(){
          this.$emit("add:product",this.product)
      }
  }
};
</script>

<style scoped>
 
</style>
