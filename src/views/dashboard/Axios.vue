<template>
  <div>
    <span>{{ selectedItemText }}</span>
    <v-select
      v-model="selectedItem"
      :items="items"
      label="Solo field"
      solo
    />

    <!--    item-text="title"-->
    <!--    item-value="userId"-->
  </div>
</template>

<script>
  import axios from 'axios'

  export default {
    name: 'Axios',
    data: () => ({
      items: ['Foo', 'Bar', 'Fizz', 'Buzz'],
      selectedItem: '',

    }),
    computed: {
      selectedItemText () {
        let result = ''
        result = this.items.find((item) => {
          return item.userId === this.selectedItem
        })
        console.log('결과', result)
        return result
      },
    },
    created () {
      axios.get('https://jsonplaceholder.typicode.com/posts').then(
        (res) => {
          res.data.forEach((itemobj) => {
            // console.log('변경전', itemobj)
            itemobj.text = itemobj.title
            // console.log('변경 후 ', itemobj)
            itemobj.value = itemobj.userId
          })
          this.items = res.data
        },
      )
    },
  }
</script>

<style scoped>

</style>
