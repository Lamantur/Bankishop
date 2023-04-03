<template>
  <div class="T-catalog">
    <T-catalog-item v-for="product in queryProducts" :key="product.id" v-bind:product_data="product"
      @sendname="showinconsolename" />

  </div>
</template>

<script>
import TCatalogItem from './T-catalog-item.vue'
import { computed } from 'vue';

export default {

  name: "T-catalog",
  components: {
    TCatalogItem
  },
  created() { },
  data() {
    return {
      title: 'Картины эпохи Возрождения',
      queryProducts: computed(() => {
        let p = this.products;
        if (this.msge) {
          p = p.filter((product) => product.productname.indexOf(this.msge) !== -1)

        }
        return p;
      }),
      products: [
        {
          id: 1,
          image: "1.png",
          productname: "Рождение Венеры",
          autor: "Сандро Ботичелли",
          oldprice: "2 000 000 $",
          newprice: "1 000 000 $",
          incart: false,
          available: true

        },
        {
          id: 2,
          image: "2.png",
          productname: "Тайная вечеря",
          autor: "Леонардо да Винчи",
          oldprice: "",
          newprice: "3 000 000 $",
          incart: false,
          available: true

        },
        {
          id: 3,
          image: "3.png",
          productname: "Сотворение Адама",
          autor: "Микеланджело",
          oldprice: "6 000 000 $",
          newprice: "5 000 000 $",
          incart: false,
          available: true

        },
        {
          id: 4,
          image: "4.png",
          productname: "Урок анатомии",
          autor: "Рембрандт",
          oldprice: "",
          newprice: "",
          incart: false,
          available: false

        }
      ]
    }
  },
  props: ['msge'],
  methods: {
    showinconsolename(data) {
      console.log(data)
    }
  },
};
</script>

<style>
.T-catalog {

  display: grid;
  grid-template-columns: repeat(auto-fill, 260px);
  grid-gap: 32px;
}
</style>