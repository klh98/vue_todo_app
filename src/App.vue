<template>
  <div class="container mt-4">
    <div class="row">
        <div class="col-md-4"></div>
        <div class="col-md-4">
          <TitleComponent title="Vue todo App" class="text-center"></TitleComponent>

            <ListCreate @create="create"></ListCreate>

            <div class="form-row d-flex">
                <p>Job Done</p>
                <p class="badge badge-pill badge-primary ml-2">{{ doneTotal }}</p>
            </div>

            <ul class="list-group">
              <ListComponent v-for="list in lists" :key="list.id" :list="list" @del="del" class=""></ListComponent>               
            </ul>   

        </div>
        <div class="col-md-4"></div>
    </div>
</div>
</template>

<script>
  import TitleComponent from './components/TitleComponent.vue';
  import ListComponent from './components/ListComponent.vue';
  import ListCreate from './components/ListCreate.vue';

  export default {
    name:'App',
    components: {TitleComponent, ListComponent, ListCreate},
    data() {
      return {
            title: "Vue todo App",
            lists:[],
            currentId: 1, 
          }
        },
        computed:{
            doneTotal()
            {
                return this.lists.filter(el=> el.isDone === true).length;
            }
        },
        methods: {
          create(x) {
            this.currentId++,
            this.lists.push({
              id: this.currentId,
              message: x, 
              isDone: false,
            })
          }
        },

        del(x)
        {
          this.lists = this.lists.filter(el=> el.id !== x);
        }
 }

  
</script>

<style lang="scss" scoped>

</style>