<template>
  <div id="graphiql">Loading...IDE</div>
</template>

<script>
export default {
  components: {},
  mounted: function () {
    console.log('mounted')
    var m = document.getElementsByTagName('main')[0]
    m.setAttribute('class', 'fkmain')
    console.log(m)
    var nodes = m.childNodes
    nodes[0].setAttribute('class', 'fullh')
    var ides = nodes[0].childNodes
    ides[0].setAttribute('class', 'fullh')
    console.log('ides[0]:' + ides[0])
    // var ide2 = ides[0].getElementsByTagName('div')[0]
    // console.log(ide2)
    // ide2[0].setAttribute('class', 'fkmain')
    // 渲染graphiql
    window.ReactDOM.render(
      window.React.createElement(window.GraphiQL, {
        fetcher: window.GraphiQL.createFetcher({
          url: 'http://localhost:8545/graphql'
        }),
        defaultEditorToolsVisibility: true
      }),
      document.getElementById('graphiql')
    )
  }
}
</script>

<style>
/* body {
  height: 100%;
  margin: 0;
  width: 100%;
  overflow: hidden;
} */
/* #graphiql {
  height: 50vh;
} */

.fkmain{
  position:absolute;
  top:64px;
  bottom: 0px;
  /* height: inherit; */
  /* bottom:0px; */
  width: 100%;
  background-color: #abbaea;
}
.fullh{
  height: 100%;
  background-color: #003afa;
}
#graphiql {
  height: 100%;
}
</style>
