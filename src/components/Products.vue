<template>
<div class="conatiner d-flex justify-content-center">
  <div class="conatiner-fluid d-flex flex-wrap justify-content-evenly" style="max-width: 1200px;" >
    <div class="card mb-3 mt-3 border-dark" style="width: 350px;" v-for="product in filtered" :key="product.id">
      <div class="card-header border-dark">
        <h5 class="card-title">{{ product.name }}</h5>
      </div>
      <div class="card-body border-dark">
        <div class="border-dark" >
          <img :src="product.img"  class="img rounded-start" style="width: 18rem; height: 10rem;" alt="">
        </div>
      </div>
        <p class="card-text">PHP{{ `${product.price}.00` }}</p>
          <div class="card-footer border-dark">
          <router-link :to="{name: 'Detail', 
            params:{pathname: product.name}, 
            query:{name: product.name, 
                  price: product.price,
                  quantity: product.quantity,
                  category: product.category,
                  img: product.img, 
                  description: product.description}
            }">
            Details
          </router-link>
      </div>
    </div>
  </div>
</div>
</template>

<script>
export default {
  name: 'Products',
  props: {
    searchInput: {
      type: String,
      default: ''
    }
  },
  data () {
    return {
      products: [
    {id: 1, name: "Bacon",price:250,quantity:10, category: ["Meat"],img:'https://healthyrecipesblogs.com/wp-content/uploads/2018/01/oven-bacon-featured.jpg',
    description: "Smoked strips of pork. With just enough fat, but not too greasy"},
    {id: 2, name: "Fish",price:150,quantity:5, category: ["Seafood","Fresh"],img:'https://cdn-prod.medicalnewstoday.com/content/images/articles/322/322522/fresh-fish-on-ice.jpg',
    description: " The culinary skills involved in preparing this dish can impress even the greatest chefs of Liyue."},
    {id: 3, name: "Chicken",price:200,quantity:9, category: ["Poultry","Fresh"],img:'https://www.seriouseats.com/thmb/t82X6N4ZwGkFZmWPuCjwT-osL3g=/1500x844/smart/filters:no_upscale()/20210714-potato-starch-fried-chicken-vicky-wasik-seriouseats-20-17e193a6bf274bba9091810a0b18ef89.jpg',
    description: " The fragrance alone brings the vivid image of crispy skin and tender meat to mind. One bite and the luscious juices begin to flow. Truly irresistible."},
    {id: 4, name: "Beef",price:300,quantity:11, category: ["Meat"],img:'https://post.healthline.com/wp-content/uploads/2020/08/beef-update-1200x628-facebook-1200x628.jpg', 
    description: "Juicy, flavorsome, fragrant steak. One bite and you feel yourself come alive."},
    {id: 5, name: "Soy Sauce",price:50,quantity:20, category: ["Sauce","Seasoning"],img:'https://www.tasteofhome.com/wp-content/uploads/2020/01/GettyImages-461879075.jpg?fit=700,1024', 
    description: " Indistinguishable from ordinary spring water. May or may not be worth putting all of one's hopes into."},
    {id: 9, name: "Egg",price:10,quantity:72, category: ["Dairy"],img:'https://cdn.britannica.com/94/151894-050-F72A5317/Brown-eggs.jpg', 
    description: " With a taste of the summer sun, it invigorates you from the first bite."},
    {id: 11, name: "Pork",price:200,quantity:12, category: ["Meat"],img:'https://www.seriouseats.com/thmb/yHg0KQZc928Iqbm8G-aOE91gJb0=/1500x1125/filters:fill(auto,1)/__opt__aboutcom__coeus__resources__content_migration__serious_eats__seriouseats.com__recipes__images__2016__02__20160208-sous-vide-pork-chop-guide-food-lab-37-9bfa2f9b8a464bccad99ea08423b9d8e.jpg', 
    description: " Feast your eyes and then your stomach upon this delicacy as the soft ribs melt in your mouth."},
    ],
      filtered: []
    }
  },
  mounted () {//function is called whenever component is loaded
      this.filtered = this.products.map(product => { 
          return product 
        })
  }
  // watch: { //watching for changes on the variable chosen
  //     searchInput(data){
  //         if (data === ''){
  //             this.filtered = []
  //             this.filtered = this.products.map(product => {
  //                 return product
  //             })
  //         }else {
  //             this.filtered = []
  //             this.products.forEach(item => {
  //               if (item.name.includes(data)) {
  //                   this.filtered.push(item)
  //               }
  //               })
  //         }
  //     }
  // }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
/* div {
  border: 1px solid black;
} */
</style>