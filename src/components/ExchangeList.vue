<template lang="html">
  <div class="col-md-3 mt-3 col-sm-12 col-lg-3">
    <label>Exchange:</label>
    <select @change="sendExchange" class="form-control btn btn-dark" v-model="exchange">
      <option v-for="exchange in $store.state.exchanges" :value="exchange">{{exchange}}</option>
    </select>
  </div>
</template>

<script>
import { mapActions } from 'vuex';
export default {
  data() {
    return {
      exchange: ''
    }
  },
  methods: {
    ...mapActions(['loadExchanges', 'setExchange', 'loadPairs']),
    sendExchange() {
      this.setExchange(this.exchange)
      this.loadPairs()
    }
  },
  created() {
    this.loadExchanges()
  }

}
</script>
