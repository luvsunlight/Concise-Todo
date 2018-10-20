<template>
    <div>
        <TodoInput
            placeholder="What needs to be done?"
            @add="addTodo"
        ></TodoInput>
        <div v-if="todos.length > 0">
            <TodoAnim>
                <TodoItem
                    v-for="todo in todoList"
                    :todo="todo"
                    :key="todo.id"
                    @done="doneTodo"
                    @remove="removeTodo"
                ></TodoItem>
            </TodoAnim>
        </div>
        <div v-else>
            <p class="highlight">Get some todos right now!</p>
        </div>
        <TodoFooter
            :todoCount="todoCount"
            :doneCount="doneCount"
            @clear="clearComplete"
        ></TodoFooter>
    </div>
</template>

<script>
import TodoInput from "./TodoInput.vue";
import TodoItem from "./TodoItem.vue";
import TodoFooter from './TodoFooter.vue'
import TodoAnim from './ListAnim.vue'

export default {
    data() {
        return {
            todos: [
                {
                    id: 1,
                    text: "吃饭",
                    done: false
                },
                {
                    id: 2,
                    text: "喝水",
                    done: false
                },
                {
                    id: 3,
                    text: "睡觉",
                    done: false
                },
            ],
            nextTodoId: 4
        };
    },
    methods: {
        addTodo(newTodo) {
            this.todos.push({
                id: this.nextTodoId++,
                text: newTodo.trim(),
                done: false
            });
        },
        doneTodo(id2move) {
            let todo = this.todos.find(todo => {
                return todo.id == id2move
            })
            todo.done = !todo.done
        },
        removeTodo(id2move) {
            this.todos = this.todos.filter(todo => {
                return todo.id !== id2move
            })
        },
        clearComplete() {
            this.todos = this.todos.filter(todo => {
                return !todo.done
            })
        }
    },
    computed: {
        todoList() {
            let doneTodos = []
            this.todos = this.todos.filter(todo => {
                if (todo.done) {
                    doneTodos.push(todo)
                    return false
                }else {
                    return true
                }
            })
            doneTodos.forEach(todo => {
                this.todos.push(todo)
            })
            return this.todos
        },
        todoCount() {
            return this.todos.filter(todo => {
                return !todo.done
            }).length
        },
        doneCount() {
            return this.todos.filter(todo => {
                return todo.done
            }).length
        }
    },
    components: {
        TodoInput,
        TodoItem,
        TodoFooter,
        TodoAnim
    }
};
</script>

<style>
ul {
    list-style-type: none;
    padding-inline-start: 0;
}
.highlight {
    color: #42b983;
}
</style>