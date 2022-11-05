<template>
  <div id="graphiql">Loading...IDE</div>
</template>

<script>
export default {
  components: {},
  data () {
    return {
      graphiqlElement: null
    }
  },
  mounted: function () {
    console.log('IDE mounted')
    // 给父DOM Main设定总体高度
    var m = document.getElementsByTagName('main')[0]
    m.setAttribute('class', 'fkmain')
    // console.log(m)
    // 子组件全部遵从父组件高度
    var nodes = m.childNodes
    nodes[0].setAttribute('class', 'fullh')
    var ides = nodes[0].childNodes
    ides[0].setAttribute('class', 'fullh')
    // console.log('ides[0]:' + ides[0])
    // 渲染graphiql

    var reactE = window.React.createElement(window.GraphiQL, {
      fetcher: window.GraphiQL.createFetcher({
        url: 'http://localhost:8545/graphql'
      }),
      defaultEditorToolsVisibility: true
    })
    console.log(reactE)
    this.graphiqlElement = document.getElementById('graphiql')
    window.ReactDOM.render(reactE, this.graphiqlElement)
    var reactSendBtn = document.getElementsByClassName('graphiql-execute-button')
    reactSendBtn[0].onclick = function () {
      console.log('sendBtn!')
    }
  },
  unmounted: function () {
    console.log('IDE unmounted')
  },
  destroyed: function () {
    console.log('destroyed!')

    // console.log(window.ReactDOM)
    // const app = document.getElementById('graphiql')
    // console.log(app)
    window.ReactDOM.unmountComponentAtNode(this.graphiqlElement)
    // window.ReactDOM.unmountComponentAtNode(document.getElementById('graphiql'))
    // console.log(window.ReactDOM)
    // window.ReactDOM = null
    // console.log(window.ReactDOM)
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

.fkmain {
  position: absolute;
  top: 64px;
  bottom: 0px;
  /* top: 64px;
  height: calc(100vh - 64px); */
  width: 100%;
  background-color: #abbaea;
}

.fullh {
  height: 100%;
  background-color: #003afa;
}

#graphiql {
  height: 100%;
}
</style>
