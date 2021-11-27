<template>
<div class="container d-flex justify-content-center">
    <div class="card border-dark" id="detail">
        <div class="row g-0">
            <div class="col-md-4">
            <img :src="$route.query.img" class="img-fluid rounded-start" alt="" style="height: 320px">
            </div>
            <div class="col-md-8">
            <div class="card-body">
                <h3 class="card-title">{{ $route.query.name }}</h3>
                <h6 class="card-text">PHP {{ $route.query.price }}.00</h6>
                <h6 class="card-text">{{ $route.query.category }}</h6>
                <p class="card-text">{{ $route.query.description }}</p>
                <div class="row justify-content-center" style="margin-top: 30px;">
                    <div class="col bd-highlight"><button @click="increment">+</button></div>
                    <div class="col bd-highlight"><input type="number" v-model="cnt" min="0" :max="$route.query.quantity"></div>
                    <div class="col bd-highlight"><button @click="decrement">-</button></div>
                </div>
                <div class="mt-3">
                    <button type="button" class="btn btn-success" @click="add">Add to cart</button>
                </div>
            </div>
            </div>
        </div>
    </div>
</div>
</template>

<script>

export default{
    name: 'Detail',
    data() {
        return{
            cnt: 0
        }
    },
    methods: {
        increment() {
            if(this.cnt <= this.$route.query.quantity){
                this.cnt++
            }
        },
        decrement(){
            if(this.cnt !== 0 ){
                this.cnt--
            }
        },
        add(){
            const item = {
                name: this.$route.query.name,
                price: this.$route.query.price * this.cnt,
                origPrice: this.$route.query.price,
                cnt: this.cnt,
                img: this.$route.query.img
            };
            console.log(item)
            this.$emit('add',item)
        }  
    }
}
</script>
