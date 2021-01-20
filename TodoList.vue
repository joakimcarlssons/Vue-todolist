<template>
<div class="wrapper">
    <button class="btn" @click="addItem()">New todo...</button>
    <ul>
    <TodoItem
    v-for="(item, index) of items"
    :key="index"
    :itemData="items[index]"
    :itemName="items[index].content"
    v-on:marked="mark(index)"
    />
    </ul>
</div>
</template>

<script>
import TodoItem from './TodoItem'

export default {
    components: {
        TodoItem
    },

    data(){ return {
        items : [{content:"Apples", done:false}, 
        {content:"Pears", done:false},
        {content:"Candy, lots of candy", done:false}, 
        {content:"Tesla model 3", done:false}]
    }},

    methods: {

        addItem() {
            this.items.push({
                content : "",
                done : false
            })
        },

        mark(index) {

            const item = this.items[index]

            if (item.done) {
                document.querySelector(`li:nth-of-type(${index+1})`).classList.remove("green")
                this.items[index].done = false
            }
            else {
                document.querySelector(`li:nth-of-type(${index+1})`).classList.add("green")
                this.items[index].done = true
            }
            
        }
    }

}
</script>

<style>

.wrapper {
    display: flex;
    flex-direction: column;
    align-items: center;

    font-family: Arial, Helvetica, sans-serif;
    margin: 10rem;
}
ul {
    width: 100%;
    margin: 0;
    padding: 0;
    align-self: flex-start;
    list-style-type: none;
}

li {
    
    padding: .7rem;
    background-color: lightgray;
    color: #474646;
    font-weight: 600;
    margin: .2rem 0;
}

.btn {
    width: 100%;
    border: none;
    background-color: darkgrey;
    color: white;
    padding: 1rem;
    font-weight: 700;
    font-size: 1.3rem;
}

.green {
    background-color: lightgreen;
    color: darkgreen;
}

</style>