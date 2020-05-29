<template>
  <div>
    <q-btn
      color="primary"
      :loading="reloadBtnLoading"
      label="reload"
      :disable="reloadBtnDisable"
      :percentage="reloadBtnPercentage"
      :transitionTime="reloadBtnTransTime"
      @click="load()"
      class="standard-width"
    />
    <q-select
      v-model="model"
      :options="options"
      label="Standard"
      color="primary"
      bg-color="white"
      class="standard-width"
    />
  </div>
</template>

<script>
export default {
  data() {
    return {
      reloadBtnDisable: false,
      reloadBtnLoading: false,
      reloadBtnPercentage: 0,
      reloadBtnTransTime: 2000,
      model: null,
      options: [500, 1000, 2000, 3000]
    };
  },
  methods: {
    load() {
      this.reloadBtnDisable = true;
      this.reloadBtnLoading = true;
      this.reloadBtnPercentage = 0;
      setTimeout(() => {
        this.reloadBtnPercentage += 100;
        setTimeout(() => {
          this.reloadBtnDisable = false;
          this.reloadBtnLoading = false;
        }, this.model);
      }, 0);
    }
  },
  watch: {
    model: {
      handler: function(val) {
        this.reloadBtnTransTime = this.model;
      }
    }
  }
};
</script>

<style>
.standard-width {
  width: 200px;
}
</style>
