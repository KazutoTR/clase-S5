<script>
export default  {
  name: 'app',
  data() {
    return {
      drawer: false,
      items: [
        { label: 'Home', to: '/Home'},
        { label: 'About', to: '/About'}
      ]
    }
  },
  methods: {
    toggleDrawer() {
      this.drawer = !this.drawer
    }
  }
}
</script>

<template>
  <pv-toast/>
  <header>
    <pv-toolbar class="bg-primary" fixed>
      <template #start>
        <pv-button class="p-button-text text-white" icon="pi pi-bars" @click="toggleDrawer"/>
        <h1>ACME Learning Center</h1>
      </template>
      <template #end>
        <div class="flex-column">
          <router-link v-for="item in items" :key="item.label" v-slot="{navigate, href}" :to="item.to" custom>
            <pv-button :href="href" class="p-button-text text-white" @click="navigate">{{item.label}}</pv-button>
          </router-link>
        </div>
      </template>
    </pv-toolbar>
  </header>
  <pv-sidebar v-model="drawer"/>
  <router-view/>
</template>

<style scoped>
</style>
