<template>
  <v-ons-page>

  <v-ons-toolbar>
    <div class="center">BIR Calculator</div>
  </v-ons-toolbar>

    <section style="margin: 16px">

      <v-ons-list>
        <v-ons-list-item>
          <div class="center">
            <v-ons-input modifier="material" placeholder="Enter Amount"
                         v-model="name"
            >
            </v-ons-input>
          </div>
        </v-ons-list-item>
      </v-ons-list>

    </section>

    <section style="margin: 16px">
      <v-ons-button modifier="large" style="margin: 0 0">Compute</v-ons-button>
    </section>

</v-ons-page>
</template>

<script>
import HomePage from './components/HomePage'
import MenuPage from './components/MenuPage'

export default {
    data () {


    }

};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
ons-splitter-side[side=left][animation=overlay] {
  border-right: 1px solid #BBB;
}
</style>
