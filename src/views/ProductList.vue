<script lang="ts">
//import { ref } from 'vue'

export default {
  name: 'ProductList',
  props:{
    products: {
        type: Array as () => { id: number; label: string; description: string; status: string}[],
    },
  },
  setup(props) {
    const productsData = props.products
    console.log(productsData)
    return {
        productsData
    };
  }
}

</script>
<template>
  <div>
    <table>
        <thead>
            <tr>
                <th>ID</th>
                <th>Label</th>
                <th>description</th>
                <th>Statut</th>
            </tr>
        </thead>
        <body>
            <tr v-for="productsData in productsData" :key="productsData.id">
                <td>{{ productsData.id }}</td>
                <td>{{ productsData.label }}</td>
                <td>{{ productsData.description }}</td>
                <td v-if="productsData.quantityData > 0">Disponible</td>
                <td v-if="productsData.quantityData < 1">Indisponible</td>
            </tr>
        </body>
    </table>
    </div>
</template>
<style></style>