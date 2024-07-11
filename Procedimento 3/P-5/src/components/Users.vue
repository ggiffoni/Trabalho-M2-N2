<template>

<div class="container" id="usuarios">

<div class="bg-warning">

  <h1>Usuários de Teste via REST</h1>

  <p style="color: whitesmoke; font-weight: bold; font-style: italic;">Os usuários deste exemplo são fornecidos pela API de testes reqres.in</p>

  <div id="usuarios" class="container-fluid">

    <div class="row">

      <div class="card col-sm-3 p-2 m-3" v-for="user in users.data" :key="user.id">

        <img class="card-img-top" :src="user.avatar"/>

        <div class="card-body">

          <div class="card-title">{{user.first_name}} {{user.last_name}}</div>

            <p class="card-text">{{user.email}}</p>

          </div>

        </div>

      </div>

    </div>

  </div>

</div>  
  
</template>

<script>
import{ref} from "vue"
export default {

    name: "Users",

    async setup(){
        const users = ref(null);
        const usersResponse = await fetch("https://reqres.in/api/users?per_page=10")
        users.value = await usersResponse.json();

        return {users}


    }

}
</script>

<style>

</style>