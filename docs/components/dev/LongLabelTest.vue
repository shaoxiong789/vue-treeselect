<template>
  <div>
    <treeselect :options="options" :limit="1" :multiple="multiple" v-model="value" />
    <label><input type="checkbox" v-model="multiple"> Multi-select mode</label>
  </div>
</template>

<script>
  const longAToZ = 'abcdefghijklmnopqrstuvwxyz'.repeat(10)
  const longZToA = longAToZ.split('').reverse().join('')

  export default {
    data: () => ({
      multiple: false,
      value: [ '12412' ],
      options: [ {
        id: longAToZ,
        label: longAToZ,
      }, {
        id: 'abc',
        label: 'abc',
      }, {
        id: longZToA,
        label: longZToA,
      }, {
        id: 'xyz',
        label: 'xyz',
      } ],
    }),

    watch: {
      multiple(newValue) {
        if (newValue) {
          this.value = this.value ? [ this.value ] : null
        } else {
          this.value = this.value.length ? this.value[0] : null
        }
      },
    },
  }
</script>
