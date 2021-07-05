<template>
    <div>
        <bounce-loader :loading="isLoading" :color="'#68d391'" :size="100" />
        <px-assets-table v-show="!isLoading" :assets="assets"/>
    </div>
</template>

<script>
import api from '@/api'
import PxAssetsTable from '@/components/PxAssetsTable'

export default {
  name: 'Home',
  components: {
    PxAssetsTable
  },
  data () {
    return {
      isLoading: false,
      assets: []
    }
  },
  created () {
    this.isLoading = true

    api.getAssets()
      .then(assets => this.assets = assets)
      .catch(error => console.log('error', error))
      .finally(() => this.isLoading = false)
  }
}
</script>
