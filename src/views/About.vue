<template>
  <div class="about">
    <div class="container f-fles justify-content-center">
      <div class="card" style="width: 18rem;">
      <img :src="myItems.img" class="card-img-top" alt="...">
      <div class="card-body">
        <h5 class="card-title">{{ myItems.name }}</h5>
        <p class="card-text">{{ `${myItems.price}` }}</p>
      </div>
      <div class="row " style="margin-top: 30px;">
          <div class="col"><button>+</button></div>
          <div class="col"><input type="number" :v-model="myItems.cnt"></div>
          <div class="col"><button>-</button></div>
      </div>
    </div>
  </div>
    <footer>
      <div class="row justify-content-center">
        <div class="col">
          <label for="cupon">Enter cupon code</label>
          <input type="text" id="cupon">
        </div>
        <div class="col">
          <label for="money">Enter Payment</label>
          <input type="text" id="money">
        </div>
        <div class="col">
          <button @click="check">Check Out</button>
        </div>
      </div>
    </footer>
  </div>
</template>
<script>

export default{
    name: 'About',
    props: {
      myItems: Object
    },
    data() {
        return{
            cuponcode: 0,
            total: 0,
            cupons: [
              { code: "menu50", discount: 0.5},
              { code: "menu20", discount: 0.2},
              { code: "menu10", discount: 0.1},
              { code: "menu200flat", discount: 2.00},
            ],
            items: [],
        }
    },
    methods: {
        check() {
            if(this.price <= this.money){
                console.log("successful")
                this.money - this.price
                this.$alert("Successfuly Paid");
            }else{
              this.$alert("Uh-oh... please recheck payment");
            }
        },
        cupon() {
          if(this.cuponcode === this.cupons){
              console.log("successful")
              this.total * 0.3
          }
        },
        push(){
          items.push(myItems)
        }
    }
}
</script>
<style scoped>
footer{
  text-align: center;
  width: 2000px;
  height: 100px;
  background-color: white;
  position:fixed;
  bottom:0;
}
</style>