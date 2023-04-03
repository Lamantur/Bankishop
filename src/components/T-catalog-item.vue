<template>
  <div class="t-catalog-item">
    <div class="catalog-item-box">
      <img class="T-catalog-image" :src="require('../assets/img/' + product_data.image)">
      <H2>{{ product_data.productname }}</H2>
      <H2>{{ product_data.autor }}</H2>
      <div class="buy">
        <div class="price">
          <H4 class="oldprice">{{ product_data.oldprice }}</H4>
          <H3 class="realprice">{{ product_data.newprice }}</H3>
        </div>
        <div>
          <button @click="sendname" :class='classes' v-text="word"></button>
          <img :class='spinclass' id="spinner" src="../assets/img/Spinner.svg" width="50px">
        </div>
      </div>
    </div>

  </div>
</template>

<script>
export default {
  mounted() {
    if (localStorage.word) {
      this.word = localStorage.word;
    }
  },
  watch: {
    word(newWord) {
      localStorage.word = newWord;
    }
  },
  name: "T-catalog-item",
  created() { },
  data() {
    return {
      word: "Купить",
      classes: {
        normal: true,
        incart: false,
        inprogress: false
      },
      spinclass: {
        spintrue: true,
        spinfalse: false
      }
    };
  },
  props: {
    product_data: {
      type: Object,
      default() {
        return {}
      }
    }
  },
  methods: {
    sendname(word) {
      let isEqual = (word == this.word),
        c = this.classes;
      if (this.word === "Купить") {
        this.word = "Обрабатывается"
        c.inprogress = !isEqual;

        this.spinclass.spintrue = isEqual
        this.spinclass.spinfalse = !isEqual
        setTimeout(() => {
          this.word = "В корзине";
          c.normal = isEqual;
          c.incart = !isEqual;
          c.inprogress = isEqual;
          this.spinclass.spintrue = !isEqual
          this.spinclass.spinfalse = isEqual
        }, 2000);


      }
      else {
        this.word = "Купить"
        c.normal = !isEqual;
        c.incart = isEqual;
        c.inprogress = isEqual;
        this.spinclass.spintrue = !isEqual
        this.spinclass.spinfalse = isEqual
      }

      this.$emit('sendname', this.product_data.productname)
    }
  },
};
</script>

<style>
.T-catalog-image {
  width: 100%;
  height: 160px;
  object-fit: cover;
}

.t-catalog-item {
  width: 260px;
  margin: 0 auto;
  text-align: center;
}

.catalog-item-box {
  border: 1px solid #E1E1E1;
}

.buy {
  display: grid;
  grid-template-areas: "price button";
}

.price {
  height: 48px;
}

.price * {
  margin: 0;
}

.normal {
  background-color: #403432 .5s !important;
}

.incart {
  background-color: #403432 .5s !important;
}

.inprogress {
  visibility: hidden;
}

.spintrue {
  position: absolute;
  display: none;

}

.spinfalse {
  position: absolute;
  margin-left: -82px;
  margin-top: -5px;
}
</style>
