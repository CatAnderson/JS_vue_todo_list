<template>
    <div id="app">
        <ul>
            <li v-for="task in tasks">
                <span> {{ task.name }} </span>
                <span> {{ task.priority }} </span>
            </li>
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
            tasks: [
                { name: "Buy shopping", priority: false },
                { name: "Clean bathroom", priority: false },
                { name: "Car's MOT", priority: false }
                ],
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