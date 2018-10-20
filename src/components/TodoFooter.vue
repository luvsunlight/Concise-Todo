<template>
    <div class="footer">
        <span class="footer-bar">
            <span class="highlight">{{ todoCount }}</span> items active
        </span> 
        <span class="footer-bar">
            <span class="highlight">{{ doneCount }}</span> items done
        </span>
        <span 
            class="footer-bar footer-clear" 
            v-if="doneCount>0"
            @click="$emit('clear')"
        >Clear complete</span>
    </div>
</template>

<script>
export default {
    props: ["todoCount", "doneCount"]
}
</script>

<style>
    .footer {
        padding-top: 8px;
        border-top: 1px solid #ddd;
        font-size: 10px;
    }
    .footer-bar {
        margin: 0 10px;
    }
    .footer-clear {
        padding: 2px 10px;
        border: 1px solid #fff;
        border-radius: 4px;
        cursor: pointer;
    }
    .footer-clear:hover {
        border: 1px solid #ccc;
        box-sizing: border-box;
    }
</style>    