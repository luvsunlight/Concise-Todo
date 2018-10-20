<template>
    <input 
        v-model="newTodo"
        type="text"
        class="input"
        autofocus
        @keydown.enter="addTodo"
    >
</template>

<script>
export default {
    data() {
        return {
            newTodo: ""
        };
    },
    methods: {
        addTodo() {
            if (this.newTodo) {
                this.$emit("add", this.newTodo);
                this.newTodo = "";
            }
        }
    }
};
</script>

<style>
.input {
    width: 100%;
    height: 45px;
    padding: 6px;
    border: 1px solid #ddd;
    border-radius: 5px;
    box-sizing: border-box;
    color: #555;
    text-indent: 0.5em;
    font-size: 20px;
    font-style: italic;
    outline: none;
}
::-webkit-input-placeholder {
    color: #ccc;
}
</style>
