<script>
    import SliderShop from '@/components/SliderShop.vue'
    import HeaderShop from '@/components/HeaderShop.vue'
    import ProductService from '../services/Product.service'
    import { mapState } from "pinia";
    import { useAuthStore } from "@/stores/Auth.store";
    import toastsVue from '../components/toasts.vue';
    export default {
         data(){
            return {
                Products:[],
            }
        },
        components:{
            HeaderShop,
            SliderShop,
            toastsVue
        },
        computed: {
            ...mapState(useAuthStore,{
                currentUser: "user",
            }),
    },
        methods:{
             async retrieveProduct() {
            try {
                this.Products = await ProductService.getAll();
            } catch (error) {
                console.log(error);
                }
            },          
        },
        mounted() {
        this.retrieveProduct();
        },
    }
</script>
<template>
    <div class="header">
        <HeaderShop></HeaderShop>
      </div>
      <toastsVue></toastsVue>
    <div class="slider">
        <SliderShop></SliderShop>
    </div> 
<div style="margin: 20px 100px;">
    <div style="text-align: center; margin: 30px 0;" class="heading">
        <h3>Truyện thể loại Action</h3>
        <h5>Truyện phổ biến nhất</h5>
    </div>
    <div class="flex-row" style="margin:0 100px;">
        <div class="d-sm-flex flex-wrap" id="x">
            <div class="card m-1" style="width: 18rem;"  v-for="item in Products" v-show="item.categories === 'Action'">
                <div>
                    <div>
                        <div class="image_item" v-for="img in item.img">
                            <img :src="img" class="card-img-top" alt="...">
                        </div>
                    </div>
                </div>
                <div class="card-body product">
                    <h5 class="card-title">{{item.title}}</h5>
                    <h6 class="price text-primary">{{item.price}} Lượt Xem</h6>
                    <router-link :to="{
                        name: 'details',
                        params: { id: item._id },
                    }"  >
                        <button type="button" class="btn btn-outline-dark">THÊM</button>
                    </router-link>
                </div>
            </div>
        </div> 
    <div style="text-align: center; margin: 30px 0;" class="heading">
        <h3>Truyện thể loại Commedy</h3>
        <h5>Truyện lấy nhiều nước mắt nhất</h5>
    </div>
        <div class="d-sm-flex flex-wrap" id="xx">
                 <div class="card m-1" style="width: 18rem;"  v-for="item in Products" v-show="item.categories === 'Commedy'">
                <div>
                    <div>
                        <div class="image_item" v-for="img in item.img">
                            <img :src="img" class="card-img-top" alt="...">
                        </div>
                    </div>
                </div>
                <div class="card-body product">
                    <h5 class="card-title">{{item.title}}</h5>
                    <h6 class="price text-primary">{{item.price}} lượt xem</h6>
                       <router-link :to="{
                        name: 'details',
                        params: { id: item._id },
                    }">
                        <button type="button" class="btn btn-outline-primary" @click="nextdetailsproduct">THÊM</button>
                    </router-link>
                </div>
            </div>
        </div> 
    <div style="text-align: center; margin: 30px 0;" class="heading">
        <h3>Truyện thể loại Isekai</h3>
        <h5>Top những truyện hay nhất</h5>
    </div>
       <div class="d-sm-flex flex-wrap" id="xxx">
               <div class="card m-1" style="width: 18rem;"  v-for="item in Products" v-show="item.categories === 'Isekai'">
                <div>
                    <div>
                        <div class="image_item" v-for="img in item.img">
                            <img :src="img" class="card-img-top" alt="...">
                        </div>
                    </div>
                </div>
                <div class="card-body product">
                    <h5 class="card-title">{{item.title}}</h5>
                    <h6 class="price text-primary">{{item.price}} lượt xem</h6>      
                       <router-link :to="{
                        name: 'details',
                        params: { id: item._id },
                    }">
                        <button type="button" class="btn btn-outline-success" @click="nextdetailsproduct">THÊM</button>
                    </router-link>
                </div>
            </div>
        </div> 
    </div>   
</div>
<div>
</div>
</template>
<style scoped>   

    .image_slider:hover{ 
       transform: translateX(-100%);
    }
   .image_item{
       flex: 1 0 100%;
   }
   
</style>