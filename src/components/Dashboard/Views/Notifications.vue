<template>
  <div class="content">
    <div class="container-fluid">
      <card>
        <template slot="header">
          <h4 class="card-title">Video Games Sales Dataset</h4>
          <p class="card-category">Containing sales data as at 22 December 2016</p>
        </template>
        <template>
          <div id="app">
          <div id="editor" ref="editor">Dataset</div>
          <div id="iframe-wrapper":style="iframe.wrapperStyle">
          <iframe 
          v-if="loaded"
          :src="csv.html"
          :style="iframe.style"
          :height="iframe.style.height"
          :width="iframe.style.width"
          type="application/csv"
          frameborder="0">
          </iframe>
          </div>
          </div>
        </template>
      </card>
    </div>
  </div>
</template>
<script>
  import Card from 'src/components/UIComponents/Cards/Card.vue'

  export default {
    components: {
      Card
    },
    data () {
      return {
        loaded: false,
        iframe: {
          src: window.location.href,
          style: null,
          wrapperStyle: null
        },
        type: ['', 'info', 'success', 'warning', 'danger'],
        notifications: {
          topCenter: false
        }
      }
    },
    methods: {
      notifyVue (verticalAlign, horizontalAlign) {
        const notification = {
          template: `<span>Welcome to <b>Light Bootstrap Dashboard</b> - a beautiful freebie for every web developer.</span>`
        }

        const color = Math.floor((Math.random() * 4) + 1)
        this.$notifications.notify(
          {
            component: notification,
            icon: 'nc-icon nc-app',
            horizontalAlign: horizontalAlign,
            verticalAlign: verticalAlign,
            type: this.type[color]
          })
      }
    },
    mounted () {
      let editor = this.$refs.editor
      this.iframe.style = {
        position: 'absolute',
        width: window.innerWidth,
        height: window.innerHeight,
        top: -editor.offsetTop + 'px',
        left: -editor.offsetLeft + 'px'
      }
      this.iframe.wrapperStyle = {
        overflow: 'hidden',
        height: editor.clientHeight + 'px',
        width: editor.clientWidth + 'px'
      }
      this.loaded = true
    }
  }

</script>
<style lang="scss">

</style>