<template>
  <div>
    <div id='megadraft'></div>
    <div id='savebtn'></div>

    <h2>Textarea rendered with Vue:</h2>
    <p>
      When the save button is clicked, React fires a vue method which sets the data property in the Vue component.
    </p>
    <textarea v-model="content"></textarea>
  </div>

</template>

<script>
import React from 'react'
import ReactDOM from 'react-dom'
import {MegadraftEditor, editorStateFromRaw, editorStateToJSON} from 'megadraft'

class App extends React.Component {
  constructor (props) {
    super(props)
    this.setContent = props.setContent

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
    this.setContent(content)
    console.log(content)
  }

  render () {
    return React.createElement('div', {},
      React.createElement(MegadraftEditor,
        {
          editorState: this.state.editorState,
          onChange: this.onChange
        }
      ),
      React.createElement('button', {onClick: this.onSaveClick}, 'Save')
    )
  }
}

export default {
  name: 'mega-draft',
  mounted () {
    ReactDOM.render(
      React.createElement(
        App,
        {
          vue: this,
          setContent: (content) => { this.content = content }
        }),
      document.getElementById('megadraft')
    )
  },
  data () {
    return {
      content: ''
    }
  },
  methods: {
  },
  watch: {
    content (val) {
      console.log(val)
    }
  }
}
</script>

<style scoped>
@import "../../node_modules/megadraft/dist/css/megadraft.css";

#megadraft {
  margin-left: 10%;
  max-width: 80%;
  border: 1px solid grey;
}

textarea {
  width: 80%;
  margin: 20px;
  min-height: 200px;
}
</style>
