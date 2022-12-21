<template>
    <div id="block">
        <form id="forms" @submit.prevent="addProduct()">
            <input type="text" name="name" placeholder="   Ф.И.О сотрудника"
             v-model="name"
             >
            <input type="date" name="date" placeholder="Дата выдачи зарплаты"
             v-model="date"
             >
            <input type="number" name="amount" placeholder="Количество отработанных дней"
             v-model="amount"
             >
            <input type="number" name="price" placeholder="Размер заработной платы с."
            v-model="price"
            >
            <button type="submit" class="button">Добавить</button>
        </form>
        <Markaerror v-if="isValidationNeed"/>
    </div>
</template>

<script>

import Markaerror from '@/components/markaerror.vue';


export default {
    components: {
    Markaerror
},

    data() {
        return {
            name: null,
            date: null,
            amount: null,
            price: null,

            products: [],
            isErrorNeed: false
        }
    },
    methods: {
        addProduct() {

            const unmutatedProductsArray = [...this.products];

            let id = unmutatedProductsArray.length + 1;
            let name = this.name;
            let date = this.date;
            let amount = this.amount;
            let price = this.price;
            let eventualPrice = price * 0.85;

            const arr = [id, name, date, amount, price, eventualPrice];

            for(let el of arr) 
                if(!el) {
                    this.isValidationNeed = true;
                    return;
                };

                this.isValidationNeed = false;
            
            for(let product of this.products) 
                if(product.name === name) {
                    this.isValidationNeed = true;
                    return;
                };

            unmutatedProductsArray.push({
                    id,
                    name,
                    date,
                    amount,
                    price, 
                    eventualPrice
                });

            this.products = unmutatedProductsArray;
            this.$emit('getProducts', this.products);
        }
    },
    mounted() {
    }

}
</script>

<style scoped>

    #block {
        width: 100%;
        height: 100%;
        display: flex;
        align-items: center;
        justify-content: center;
        padding-left: 20px; 
    }

    #forms {
        display: flex;
        align-items: center;
        flex-direction: column;
        justify-content: center; 
        border: 5px solid rgba(52, 28, 138, 0.7);
        padding: 55px;
    }

    input {
        display: block;
        padding: 30px 100px;
        border: none;
        background-color: rgba(238, 50, 255, 0.7);
        color: rgb(255, 255, 255);
    }

    input[type="date"] {
        padding: 30px 130px;
    }
    input::placeholder {
        color: rgb(255, 255, 255);
        font-family: 'Chivo Mono', sans-serif;
        font-size: 12px;
        overflow: inherit;
    }

    input:not(:last-child) {
        margin-bottom: 30px;
    }

    .button {
        border: none;
        background-color: rgba(87, 23, 100, 0.8);
        padding: 20px 50px;
        border-radius: 5px;
        color: #fff;
    }
</style>