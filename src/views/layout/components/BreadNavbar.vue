<template>
  <div class="bread-navbar-container">
    <div class='bread-navbar-action'>
    </div>
    <div class="bread-navbar-crumb">
      <breadcrumb></breadcrumb>
    </div>
  </div>
</template>

<script>
import { generateTitle } from '@/utils/i18n'
import Breadcrumb from '@/components/Breadcrumb'
export default {
  components: { Breadcrumb },
  methods: {
    generateTitle // generateTitle by vue-i18n
  }
}
</script>
<style lang="scss" scoped>
  .bread-navbar-container {
    height: 40px;
    width: 100%;
    .bread-navbar-action {
      height: inherit;
      float: left;
    }
    .bread-navbar-crumb {
      float: right;
      margin-right: 20px;
      padding-top: 20px;
    }
  }
</style>
