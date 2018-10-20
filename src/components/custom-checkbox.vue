<template>
    <div class="custom-checkbox">
        <input type="checkbox" :id="todo.id">
        <label :for="todo.id" class="checkbox-label"></label>
        <label :for="todo.id" class="checkbox-text">{{ todo.text }}</label>
        <slot></slot>
    </div>
</template>

<script>
export default {
    props:["todo"]
}
</script>

<style>
    .custom-checkbox {
        width: 20px;
        height: 20px;
        background: #ddd;
        border-radius: 50%;
        position: relative;
        box-shadow: 1px 1px 1px #ddd;
    }
    .custom-checkbox input {
        visibility: hidden;
    }
    .checkbox-label {
        width: 12px;
        height: 12px;
        border-radius: 50%;
        transition: all .5s ease;
        cursor: poiner;
        position: absolute;
        top: 4px;
        left: 4px;
        background: #aaa;
    }
    .custom-checkbox input[type=checkbox]:checked + label {
        background: #26ca28;
    }
</style>        