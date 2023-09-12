<template>
    <li class="list-group-item d-flex justify-content-between" @dblclick="isEdit= true">
        <input type="text" v-if="isEdit" @keyup.enter="isEdit = false">
        <div v-else class="">
           <input type="checkbox" v-model="isDone" class="mr-2" id="customCheck">
            <label>{{list.message}}</label>
        </div>
        <span class="material-symbols-outlined" @click="del(list.id)" style="float: right;">
            x
        </span>
    </li>
</template>

<script>
    export default {
        name:"ListComponent",
        data() {
            return {
                isEdit:false,
                isDone:false,
            }
        },
        props: {
            list: {
                type: Object, 
                required: true,
            },
            
        },
        methods: {
            del(x) {
                this.$emit("del", x)
            }
        },
        
    }
</script>

<style lang="scss" scoped>
    
</style>