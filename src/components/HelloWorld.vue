<template>
  <div class="diagram">
   <div v-html="diagram" class="circle"></div>
   <Legend :items="items" />
  </div>
</template>

<script>
import diagram from '@/assets/diagram'
import Legend from '@/components/Legend.vue'
export default {
  name: 'HelloWorld',
  data() {
    return {
      diagram: diagram,
      items: [
        {id:"red", name: 'розовый сегмент', color: '#FF69B4', highlight: false},
        {id: "green", name: 'зеленый сегмент', color: "#97BB31", highlight: false},
        {id: "gray", name: 'серый сегмент', color: '#D9D9D9', highlight: false}
      ]
    }
  },
  mounted() {
    let paths = document.querySelectorAll('.sector')
    let highlights = document.querySelectorAll('.highlight')
    paths.forEach(path => {
      path.onmouseover = this.mouseoverHadler.bind(this)
      
    })
    highlights.forEach(highlight => highlight.onmouseout = this.mouseoutHandler.bind(this))
  },
  methods: {
    mouseoverHadler(e) {
      this.items.map(item =>{
        if(item.id === e.target.id) {
          item.highlight = true
          document.getElementsByName(item.id)[0].classList.remove('hidden')
        }
      })

    },
    mouseoutHandler(e) {
      this.items.map(item => {
        if(item.id === e.target.attributes.name.value) {
          e.target.classList.add('hidden')
          item.highlight = false
        }
      })
    }
  },
  components: {
    Legend
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
.diagram {
  display: flex;
  align-items: center;
  margin: 0 auto;
  width: 772px;
}
.circle {
  margin-right: 100px;
}
.hidden {
  display: none;
}
.visible {
  opacity: 0.2 !important
}
</style>
