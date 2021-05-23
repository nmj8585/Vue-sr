<template>
  <div>
    <span>{{ selectedItemText }}</span>
    <v-select
      v-model="selectedItem"
      :items="items"
      label="Solo field"
      solo
    />
    <!-- 구분1 메뉴 -->
    <v-select
      v-model="selectedmenu"
      :items="menuList"
      label="Menu"
      solo
      @change="onClickMenuSelection"
    />
    <!-- 구분 2  서브메뉴   -->
    <v-select
      v-model="selectSubMenu"
      :items="subMenuList"
      label="Sub Menu"
      solo
      @change="onClickSubmenuSelection"
    />
    <!-- 구분 3  카테고리   -->
    <v-select
      v-model="selectCategoryMenu"
      :items="categoryList"
      label="Category"
      solo
    />
    <!-- 구분 4  App type  -->
    <v-select
      v-show="containerSelected"
      label="App Type"
      solo
    />
    <!-- 구분 5  app title   -->
    <v-select
      v-show="containerSelected"
      label="App Title"
      solo
    />

    <!--셀렉트 박스 3개를 만드고 별도 3개
 1매뉴 2서부메뉴  각각 개별적으로 목록이랑 변수를 담는곳을 가진다    -->
  </div>
</template>

<script>
  import axios from 'axios'

  export default {
    name: 'Axios',
    data: () => ({
      // 테스트 수정
      items: ['Foo', 'Bar', 'Fizz', 'Buzz',
              { text: 'fff', value: 1 }],
      selectedItem: '',
      selectedmenu: '',
      selectSubMenu: '',
      selectCategoryMenu: '',
      containerSelected: false,

      // 데이터 변수를 각각 총 3개 만들기
      menuList: [
        { text: 'VM', value: 'VM' },
        { text: 'Container', value: 'Container' },
        { text: 'Block', value: 'Block' },
      ],
      subMenuList: [
        { text: 'Kubernitz App', value: 'Kubernitz App' },
        { text: 'Kubernitz Business', value: 'Kubernitz Business' },
        { text: 'Kubernitz Docker', value: 'Kubernitz Docker' },
      ],
      categoryList: [],
      categoryListA: ['상하이 버거', '맥치킨 버거', '맥미니'],
      categoryListB: ['맘터스페셜', '치킨버거', '맘쓰튀김'],

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
      this.categoryList = this.categoryListA
    },
    methods: {
      onClickSubmenuSelection (i) {
        console.log('클릭시 넘어오는 값', i)
        // 서브메뉴가 Kubernitz App 선택되었을 때
        if (i === 'Kubernitz App') {
          console.log('Kubernitz App', '선택됨')
          this.getKubernitzAppsCategory()

        //  서브메뉴가 Kubernitz App 외의 것이 선택됏을 때
        } else {
          this.categoryList = this.categoryListA
        }
      },
      onClickMenuSelection (menu) {
        console.log('메뉴클릭시 넘어온 값', menu)
        if (menu === 'Container') {
          this.containerSelected = true
        } else {
          this.containerSelected = false
        }
      },
      getKubernitzAppsCategory () {
        axios.get('https://jsonplaceholder.typicode.com/posts').then(
          (res) => {
            this.categoryList = this.categoryListB
          },
        )
      },
    },
  }
</script>

<style scoped>
</style>
