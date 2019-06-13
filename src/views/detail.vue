<template>
  <div>
    <div>project = {{ project }}</div>
    <div>projectRoute = {{ projectRoute }}</div>
    <div id="app"></div>
  </div>
</template>

<script>

export default {
  computed: {
    project () {
      return this.$route.params.project
    },
    projectRoute () {
      return this.$route.params.pathMatch
    }
  },
  mounted () {
    if (this.project === 'user') {
      setTimeout(() => {
        this.loadJs('http://127.0.0.1/js/chunk-vendors.d797191b.js')
        this.loadJs('http://127.0.0.1/js/app.240df4ce.js')
        this.loadJs('http://127.0.0.1/js/chunk-2d0b68f8.5f0ab895.js')
      }, 100)
    }
  },
  methods: {
    loadJs (url, callback) {
      var script = document.createElement('script')
      script.type = 'text/javascript'
      if (typeof (callback) !== 'undefined') {
        if (script.readyState) {
          script.onreadystatechange = function () {
            if (script.readyState === 'loaded' || script.readyState === 'complete') {
              script.onreadystatechange = null
              callback()
            }
          }
        } else {
          script.onload = function () {
            callback()
          }
        }
      }
      script.src = url
      document.body.appendChild(script)
    }
  }
}
</script>
