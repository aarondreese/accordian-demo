<template>
  <div>
    <h2 class="title">{{accordian.title}}</h2>
    <div v-for="panel in accordian.panels" :key="panel.id" class="accordian-item">
      <h2 
        class="header"
        @click="togglePanel(panel.id)"
      >
        {{panel.title}} 
      </h2>
      <p 
        class="answer"
        :class="panel.isOpen ? 'answer-open' : ''"
      >{{panel.answer}}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'AccordianMenu',
  data(){
    return {
      accordian: {
        title: "Frequently Asked Questions",
        panels : [
          {
            id: 1,
            title: "This is a testing question",
            answer: "Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum. ",
            isOpen: true 
          },
          {
            id: 2,
            title: "This is a testing question2 ",
            answer: "Second Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum. ",
            isOpen: false         
         }
          ,
          {
            id: 3,
            title: "This is a testing question 3 ",
            answer: "Third Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum. ",
            isOpen: false
          },
          {
            id: 4,
            title: "This is a testing question 4 ",
            answer: "Third Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum. ",
            isOpen: false
          },
        ]
      },
    }
  },
  methods:{
    togglePanel(id){
      let selectedPanel = this.accordian.panels.find(p=> p.id === id)
      this.accordian.panels.filter(p=> p.id !== id).forEach(p=> p.isOpen = false)
      selectedPanel.isOpen = !selectedPanel.isOpen
      // console.log(selectedPanel, selectedPanel.isOpen)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Raleway", sans-serif;
}

body{
  background-color: #082d52;
}

.title{
  color:#fff;
  margin-bottom: 32px;
}

.accordian {
  padding: 50px;
  max-width: 1200px;
  margin: 0 auto;
}

.accordian-item{
  border-radius: 10px;
  padding: 20px;
  margin-bottom: 20px;
  background-color: #fff;
}

.header{
  align-items: center;
  display: flex;
  cursor: pointer;
}

.header::after {
  content: "+";
  font-size: 40px;
  margin-left: auto;
}

.header-active::after {
  content: "-";
}

.answer {
  transition: 1000ms ease ;
  max-height: 0px;
  overflow: hidden;
}

.answer-open {
  transition: 1000ms ease ;
  max-height: max-content;
}

</style>
