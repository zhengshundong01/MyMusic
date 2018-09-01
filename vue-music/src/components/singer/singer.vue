<template>
  <div>
    歌手页面
  </div>
</template>

<script type="text/ecmascript-6">
/* eslint-disable indent,no-dupe-keys */

  const HOT_NAME = '热门'
  const HOT_SINGER_LEN = 10

  import {getSingerList} from 'api/singer'
  import {ERR_OK} from 'api/config'
  export default {
    data () {
      return {
        singers: []
      }
    },
    methods: {
      _getSingerList () {
        getSingerList().then((res) => {
          if (res.code === ERR_OK) {
            this.singers = res.data.list
          }
        })
      },
      _normalizeSinger(list){
        let map = {
          hot: {
            title: HOT_NAME,
            items: []
          }
        }
        list.forEach((item, index) => {
          if (index < HOT_SINGER_LEN) {
            map.hot.items.push({
              id: item.Fsinger.mid,
              name: item.Fsinger.name,
              avatar: ''
            })
          }
        })
      }
    }
  }
</script>

<style scoped lang="stylus" ref="stylesheet/stylus">

</style>
