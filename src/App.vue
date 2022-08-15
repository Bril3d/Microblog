<template>
<input :value="currentTag"
@input="setHashtag">
  <cards v-for="post in filteredPosts" :key="post.id">
    <template v-slot:title>
      {{ post.title }}
      </template>

    <template v-slot:content>
      {{ post.content }}
    </template>

    <template v-slot:description>
      <controls :post="post" />
    </template>
  </cards>
  
</template>

<script>
import { computed } from 'vue'
import {store} from './store'
import Cards from './components/Cards.vue'
import Controls from './components/Controls.vue'
export default {
  components:{
    Cards,
    Controls
  },
  setup() {
  const setHashtag = ($evt) => {
    store.setHashtag($evt.target.value)
  }
    
    
    return {
      
      setHashtag,
      currentTag:computed(()=>store.state.currentTag),
      filteredPosts:computed(()=>store.filteredPosts )
    }
  }
}
</script>

<style>

</style>