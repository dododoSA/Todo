<template>
    <div>
        <h2>TodoList</h2>
        <div v-for="item in tasks" :key="item.id">
            <div>
                {{ item.id }}
                {{ item.name }} : 
                <button @click="changeState(item)">{{ getState(item.state) }}</button>
                <button @click="removeTask(item)">削除</button>
            </div>
        </div>
        <label>
            <input type="text" v-model="newTaskName">
        </label>
        <button @click="addTask">追加</button>
    </div>
</template>

<script>
export default {
    name: 'TodoList',
    data() {
        return {
            tasks: [],
            newTaskName: "",
            lastId: 0
        }
    },
    methods: {
        getState(state){
            if(state == 0){
                return "未完"
            }
            else{
                return "完了済み"
            }
        },
        changeState(item){
            item.state = item.state ? 0 : 1
        },
        addTask(){
            if(this.newTaskName){
                this.tasks.push({id: this.lastId,name: this.newTaskName, state: 0});
                this.newTaskName = ""
                this.lastId++
            }
        },
        removeTask(item){
            var tempIndex = this.tasks.indexOf(item)
            this.tasks.splice(tempIndex, 1)
            for(var i = tempIndex; i < this.tasks.length; i++){
                this.tasks[i].id--
            }
            this.lastId--
        }
    }
}
</script>
