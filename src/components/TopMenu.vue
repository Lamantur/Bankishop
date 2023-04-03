<template>
    <div class="root">
        <div class="mainmenu">

            <a href="" class="mainmenuelements">Каталог</a>
            <a href="" class="mainmenuelements">Доставка</a>
            <a href="" class="mainmenuelements">Оплата</a>
            <a href="" class="mainmenuelements">Контакты</a>
            <a href="" class="mainmenuelements">О компании</a>
            <input type="search" placeholder="Поиск по названию картины" v-model="searchValue" />
            <button class="search_btn" @click="search(searchValue)">Найти</button>

        </div>
    </div>
</template>

<script>

export default {
    name: 'TopMenu',
    data() {
        return {
            text: "TopMenu",
            searchValue: ""
        }
    },
    methods: {
        search(value) {
            this.$emit('sendvalue', value)
        }
    }
}
</script>
<style>
.mainmenu {

    height: 95px;
    width: 100vw;
    display: table-cell;
    vertical-align: middle;
    text-align: center;
    border-bottom: 1px solid #E1E1E1;
}

.mainmenuelements {
    padding: 0px 24px;
    text-align: center;
    font-size: 14px;
    font-family: Merriweather;
    text-decoration: none;
    color: #343030;

}

input {

    margin-left: 138px;
    width: 294px;
    height: 42px;
    border-radius: 0;
    border-color: #E1E1E1;

}

button {
    width: 118px;
    height: 48px;
    background-color: #403432;
    color: #F4F6F9;
    font-size: 14px;


}

body {
    margin: 0;
    font-family: Merriweather;
}
</style>