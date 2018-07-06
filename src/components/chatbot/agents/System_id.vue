<template>
  <div class="col-md-8">
    <div class="row">
      <div style="margin-bottom: 30px;">
        <button class="btn btn-secondary btn-micro" v-on:click="back_page">
          <span aria-hidden="true" class="entypo entypo-back" style="font-size: 17px;"></span>
          {{'Back'}}
        </button>
        <button class="btn btn-secondary btn-micro" v-on:click="add_intent">
          <span aria-hidden="true" class="entypo entypo-plus" style="font-size: 17px;"></span>
          {{'Add a new intent'}}
        </button>
      </div>
    </div>
  </div>

</template>

<script>
    export default {
      name: 'System_id'
    }
</script>

<style scoped>

</style>
