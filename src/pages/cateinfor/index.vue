<template>
    <table class="table table-hover">
      <thead>
        <th scope="col">Tên</th>
        <th scope="col">Giá</th>
        <th scope="col">Số lượng</th>
        <th scope="col">Hình ảnh</th>
      </thead>
      <tbody>
        <tr v-for="item in product" :key="item.id">
        
        <td>{{ item.name_product }}</td>
        <td>{{ item.price }}</td>
        <td>{{ item.qty }}</td>
        <td><img :src="path + '/upload/' + item.image" alt="image" style=" width: 150px;"  ></td>
      </tr>
      </tbody>
    </table>
</template>
<script>
import axios from 'axios';


export default{
    data(){
        return{
            product:[],
            path: 'https://banxedap-backend-api.onrender.com',

        };
    },
    
    created(){
        this.getProduct();
    },
    methods: {
        
        async getProduct(id) {
        try {
          const response = await axios.get(`https://banxedap-backend-api.onrender.com/api/category/${this.$route.params.id}`);
          this.product = response.data;
        } catch (err) {
          console.log(err);
        }
      },
    }
}
</script>