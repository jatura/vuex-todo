<template>
    <div>
        <h3>Todos</h3>
        <div class="todos">
            <div v-for="todo in allTodos" :key="todo.id" class="todo" :class="todo.completed?'complete':''" @dblclick="toggleCompleted(todo)">
                {{ todo.title}}
                <small class="del" @click="deleteTodo(todo.id)">Del</small>
            </div>
        </div>
    </div>
</template>
<script>
import { mapGetters, mapActions } from 'vuex'
export default {
    name: "Todos",
    methods: {
        ...mapActions(["fetchTodos", "deleteTodo","toggleCompleted"])
    },
    computed: mapGetters(["allTodos"]),
    created(){
        this.fetchTodos();
    }
}
</script>
<style scoped>
.todos{
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 1rem;
}
.todo{
    border: 1px solid #ccc;
    background: #41b883;
    padding: 1rem;
    border-radius: 5px;
    text-align: center;
    position: relative;
    cursor: pointer;
}
.complete{
  background: #35495e;
  color: #fff;
}
.del{
    color: #fff;
    position: absolute;
    right: 10px;
    bottom: 10px;
    cursor: pointer;
}
</style>