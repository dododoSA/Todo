<template>
    <div>
        <div>
            <div>ItemList</div>
            <div v-for="item in items" :key="item.name">
                <div class="item" :class="{over500 : item.price > 500}">
                    <div class="name">名前: {{ item.name }}</div>
                    <div class="price">{{ item.price }}</div>
                    <div v-if="item.price >= 10000">高額商品</div>
                </div>
            </div>
        </div>
        <div>
            <label>
                名前<input type="text" v-model="newItemName">
            </label>
            <label>
                価格<input type="number" v-model="newItemPrice">
            </label>
            <button @click="addItem">add</button>
        </div>
    </div>
</template>

<script>
export default {
    name: "ItemList",
    data(){
        return {
            items: [
                {name: 'たまご', price: 100},
                {name: 'りんご', price: 100}
            ],
            newItemName: "",
            newItemPrice: 0
        }
    },
    methods: {
        addItem(){
            if(this.newItemName && this.newItemPrice){
                this.items.push({name: this.newItemName, price: this.newItemPrice });
                this.newItemName = ""
                this.newItemPrice = 0
            }
        }
    }
};
</script>

<style>
.over500{
    color:red;
}
</style>
