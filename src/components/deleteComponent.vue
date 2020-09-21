<template>
        <i id="app" @click="remove(id)" class="fas fa-trash-alt"></i>
</template>

<script>
  export default {
    name: "removeComponent",
    props:{
      id:{
          type:Number,
          required:true,
      },
    },
    methods:{
        remove(id){
        this.$emit("remove",{id:id})
        },
    }
  }
</script>
