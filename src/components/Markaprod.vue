<template>
    <div id="product">
        <div class="chet" v-for="product in products" :key="product.id">
            <div class="chet-item" id="id">
                <h2>Порядковый номер: {{product.id}}</h2>
            </div>
            <div class="chet-item" id="name">
                <h2>Ф.И.О: {{product.name}}</h2>
            </div>
            <div class="chet-item" id="date">
                <h2>Дата выдачи зарплаты: {{product.date}}</h2>
            </div>
            <div class="chet-item" id="amount">
                <h2>Количество отработанных дней: {{product.amount}}</h2>
            </div>
            <div class="chet-item" id="price">
                <h2>Сумма заработной платы сотрудника без налоговых отчислений: {{product.price}}</h2>
            </div>
            <div class="chet-item" id="price">
                <h2>Сумма заработной платы сотрудника с налоговыми отчислениями (-15%): {{product.eventualPrice}}</h2>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        products: {
            type: Array,
            required: true
        }
    }
}
</script>

<style scoped>

#product {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    padding: 40px 0;
}
.chet {
    width: 70%;
}


.chet:not(:last-child) {
    margin-bottom: 50px;
}

.chet-item {
    padding: 20px 0 20px 10px;
}

.chet-item:not(:first-child, :last-child) {
    border: 2px solid rgb(31, 124, 124, .7);
    border-top: none;
}

.chet-item:nth-child(2) {
    border-top: 2px solid rgb(31, 124, 124, .7);
}
</style>