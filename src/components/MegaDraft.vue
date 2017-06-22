<template>
  <div id='megadraft'>

  </div>
</template>

<script>
import React from 'react'
import ReactDOM from 'react-dom'
import {MegadraftEditor, editorStateFromRaw, editorStateToJSON} from 'megadraft'

class App extends React.Component {
  constructor (props) {
    console.log(props)
    super(props)
    this.setData = props.dataContainer
    this.state = {editorState: editorStateFromRaw(null)}
    this.onChange = this.onChange.bind(this)
    this.onSaveClick = this.onSaveClick.bind(this)
  }

  onChange (editorState) {
    this.setState({editorState})
  }

  onSaveClick () {
    const {editorState} = this.state
    const content = editorStateToJSON(editorState)
    // Your function to save the content
    // save_my_content(content)
    console.log(content)
  }

  render () {
    return React.createElement(MegadraftEditor, {editorState: this.state.editorState, onChange: this.onChange})
  }
}

export default {
  name: 'hello',
  mounted () {
    ReactDOM.render(
      React.createElement(App, {vue: this}),
      document.getElementById('megadraft')
    )
  },
  data () {
    return {
      content: ''
    }
  },
  methods: {
  }
}
</script>

<style scoped>
@import "../../node_modules/megadraft/dist/css/megadraft.css";
</style>
