<template>
    <div class="form-row mt-4">
        <div class="form-group col-10">
            <input type="text" class="form-control" v-model="newMessage" placeholder="say something">
        </div>
        <div class="form-group col-2">
            <button class="btn btn-primary" @click="create()">Add</button>
        </div>
    </div>
</template>

<script>
    export default {
        name: "ListCreate",
        data() {
            return {
                newMessage: "",
            }
        },
        methods: {
            create() {
               if(this.newMessage)
               {
                this.$emit("create", this.newMessage)
                this.newMessage=""
               }
               else
               {
                alert('please say something');
               }
            }
        },
    }
</script>

<style lang="scss" scoped>

</style>