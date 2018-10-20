<template>
    <li class="custom-checkbox" @click="done">
        <input 
            class="checkbox-btn" 
            type="checkbox"
            :id="todo.id"
        >
        <label class="checkbox-label"></label>
        <span v-if="!todo.done">
            {{ todo.text }}
        </span>
        <span v-else class="doneTodo">
            <s>{{ todo.text }}</s>
        </span>
        <span class="checkbox-close" @click="$emit('remove', todo.id)">×</span>
    </li>
</template>

<script>
export default {
    props: ["todo"],
    methods: {
        done() {
            document.getElementById(this.todo.id).checked = !document.getElementById(this.todo.id).checked
            this.$emit('done', this.todo.id)
        }
    }
}
</script>
<style>
    .custom-checkbox {
        height: 36px;
        position: relative;
        border-radius: 6px;
        font-size: 18px;
        text-indent: 1em;
        line-height: 36px;
    }
    .checkbox-btn {
        visibility: hidden;
    }
    .checkbox-label {
        position: absolute;
        top: 7px;
        left: 7px;
        width: 20px;
        height: 20px;
        border: 1px solid #ddd;
        border-radius: 50%;
        cursor: pointer;
        transition: all .5s ease;
    }
    .checkbox-label:after {
        opacity: 0.0;
        content: '';
        position: absolute;
        width: 9px;
        height: 5px;
        background: transparent;
        top: 4.5px;
        left: 4px;
        border: 3px solid #42b983;
        border-top: none;
        border-right: none;
    
        -webkit-transform: rotate(-45deg);
        -moz-transform: rotate(-45deg);
        -o-transform: rotate(-45deg);
        -ms-transform: rotate(-45deg);
        transform: rotate(-45deg);
    }
    .custom-checkbox label:hover::after {
        color: #42b983;
        opacity: 0.3;
    }
    .custom-checkbox input[type=checkbox]:checked + label:after {
        border: 3px solid #fff;
        border-top: none;
        border-right: none;
        opacity: 1;
    }
    .custom-checkbox input[type=checkbox]:checked + label {
        background: #42b983;
    }
    .checkbox-close {
        float: right;
        color: #ddd;
        cursor: pointer;
    }
    .checkbox-close:hover {
        color: #333;
    }
    li {
        margin: 6px 0;
        padding-right: 10px;
        text-align: left;
    }
    li:hover {
        background: #f7efef;
    }
    li:hover .checkbox-close {
        font-size: 22px;
        color: rgb(143, 138, 138);
    }
    .doneTodo {
        color: #ccc;
    }
</style>


