<template>
  <div id='megadraft'>

  </div>
</template>

<script>
import React from 'react'
import ReactDOM from 'react-dom'
import {MegadraftEditor, editorStateFromRaw} from 'megadraft'

class App extends React.Component {
  constructor (props) {
    super(props)
    this.state = {editorState: editorStateFromRaw(null)}
    this.onChange = this.onChange.bind()
  }

  onChange (editorState) {
    this.setState({editorState})
  }

  render () {
    return React.createElement(MegadraftEditor, {editorState: this.state.editorState, onChange: this.onChange}, null)
    // return (
    //   <MegadraftEditor
    //     editorState={this.state.editorState}
    //     onChange={this.onChange}/>
    // )
  }
}

export default {
  name: 'hello',
  mounted () {
    ReactDOM.render(
      React.createElement(App),
      document.getElementById('megadraft')
    )
    // ReactDOM.render(
    //   <App />,
    //   document.getElementById('megadraft')
    // )
  },
  data () {
    return {
    }
  }
}
</script>

<style scoped>
@import "../../node_modules/megadraft/dist/css/megadraft.css";
</style>
