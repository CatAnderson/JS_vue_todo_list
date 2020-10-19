<template>
    <div id="app">
        <ul>
            <li v-for="task in tasks">{{ task }}</li>
        </ul>

        <form v-on:submit.prevent="saveNewTask">
            <label for="new-todo">add new task:</label>
            <input id="new-todo" type="text" v-model="newTask">
            <input type="submit" value="save new task">
        </form>
    </div>
</template>

<script>
export default {
    data(){
        return {
            tasks: ["Buy shopping", "Clean bathroom", "Car's MOT"],
            newTask: ""
        }
    },
    
    methods: {
        saveNewTask: function(){
            this.tasks.push(this.newTask);
            this.newTask = ""
        }
    }
}
</script>

<style>

</style>