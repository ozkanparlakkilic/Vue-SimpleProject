<template>
  <div>
    <h3 class="text-center my-5">Product List</h3>
    <p v-if="products.length == 0">Empty Product List</p>
    <table v-else class="table container">
      <thead>
        <tr>
          <th>Id</th>
          <th>Product Name</th>
          <th>Category</th>
          <th>Description</th>
          <th>Unit Price</th>
          <th>Unit In Stock</th>
          <th></th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="product in products" :key="product.id">
          <td v-if="updateId === product.id">
            <input
              v-model="product.id"
              type="text"
              class="form-control"
              id="id"
            />
          </td>
          <td v-else>
            {{ product.id }}
          </td>
          <td v-if="updateId === product.id">
            <input
              v-model="product.productName"
              type="text"
              class="form-control"
              id="productName"
            />
          </td>
          <td v-else>
            {{ product.productName }}
          </td>
          <td v-if="updateId === product.id">
            <input
              v-model="product.categoryId"
              type="text"
              class="form-control"
              id="categoryId"
            />
          </td>
          <td v-else>
            {{ product.categoryId }}
          </td>
          <td v-if="updateId === product.id">
            <input
              v-model="product.quantityPerUnit"
              type="text"
              class="form-control"
              id="quantityPerUnit"
            />
          </td>
          <td v-else>
            {{ product.quantityPerUnit }}
          </td>
          <td v-if="updateId === product.id">
            <input
              v-model="product.unitPrice"
              type="text"
              class="form-control"
              id="unitPrice"
            />
          </td>
          <td v-else>
            {{ product.unitPrice }}
          </td>
          <td v-if="updateId === product.id">
            <input
              v-model="product.unitsInStock"
              type="text"
              class="form-control"
              id="unitsInStock"
            />
          </td>
          <td v-else>
            {{ product.unitsInStock }}
          </td>

          <td v-if="updateId !== product.id">
            <button
              class="btn btn-sm btn-success pr-1"
              @click="handleUpdate(product)"
            >
              Update
            </button>
            <button
              class="btn btn-sm btn-danger"
              @click="handleDelete(product)"
            >
              X
            </button>
          </td>
          <td v-else>
            <button
              class="btn btn-sm btn-success pr-1"
              @click="handleSave(product)"
            >
              Save
            </button>
            <button class="btn btn-sm btn-danger" @click="updateId = null">
              Not Save
            </button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: "product-list",
  data() {
    return { updateId: null };
  },
  props: {
    products: Array,
  },
  methods: {
    handleDelete(product) {
      this.$emit("delete:product", product);
    },
    handleUpdate(product) {
      this.updateId = product.id;
    },
    handleSave(product) {
      this.$emit("update:product", product);
      this.updateId = null;
    },
  },
};
</script>
<style scoped></style>
