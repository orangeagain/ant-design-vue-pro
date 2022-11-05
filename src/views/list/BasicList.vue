<template>
  <div id="graphiql"></div>
</template>

<script>
export default {
  name: 'StandardList',
  methods: {
    // toHome () {
    //   this.$router.push({ path: '/' })
    // }
  },
  mounted: function () {
    console.log('mounted')
    window.ReactDOM.render(
      window.React.createElement(window.GraphiQL, {
        fetcher: window.GraphiQL.createFetcher({
          url: 'https://swapi-graphql.netlify.app/.netlify/functions/index'
        }),
        defaultEditorToolsVisibility: true
      }),
      document.getElementById('graphiql')
    )
  }
}
</script>
