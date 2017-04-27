<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <p>
      Vue Box Panel
      <button v-on:click="showBoxPanel = true">Abrir box panel</button>
    </p>
    <box-panel v-if="showBoxPanel" @close="showBoxPanel = false">
      <h3 slot="box-title-header">Box Panel Title</h3>
      <div slot="box-content">
        Lorem ipsum dolor sit amet, consectetur adipisicing elit. Reprehenderit, repellat eveniet maxime recusandae amet esse temporibus, similique quibusdam consequatur repudiandae molestias, odit cum minus molestiae ratione placeat neque ullam rerum.
      </div>
    </box-panel>
  </div>
</template>

<script>
import BoxPanel from "./BoxPanel";
export default {
  name: 'hello',
  components: {
    BoxPanel,
  },
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      showBoxPanel: false
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
