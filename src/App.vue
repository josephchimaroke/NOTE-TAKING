
<template>
    <div class="overlay" v-if="isModalOpen">
      <div class="modal">
        <textarea name="note" id="note" cols="30" rows="10" v-modal.trim()="note"></textarea>
        <p></p>
        <button @click="addNote">Add Note</button>
        <button @click="closeModal">Close</button>
      </div>
    </div>
    <main>
      <header>
        <h1>Notes APP</h1>
        <button @click="openModal">+</button>
      </header>
      <div class="container">
        <div class="cards-container">
          <div v-for="note in notes" :key="note.id" class="card">
            <p class="main-text">{{ note.text }}</p>
            <p class="date">{{ note.date.toLocaleDateString() }}</p>
          </div> 
        </div>
      </div>
      <footer>
          <div class="container">
            <p>Design by PRINCE-JOSEPH</p>
          </div>
        </footer>
    </main>

  </template>
  <script setup>
    import {ref} from 'vue'
    let notes = ref([])

    const isModalOpen = ref(false)

    function openModal(){
        isModalOpen.value = true
    }



    function closeModal(){
        isModalOpen.value = false
    }

    function addNote(){
      let newNotes = {
        text: note.value,
        id: Math.random(),
        date: new  Date()
      }
      notes.value.push(newNotes)
      note.value = ' '
      isModalOpen.value = false
    }
</script>
  
  <style scoped>
    main {
      min-height: 100vh;
      background: #fff;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
    }
    .container {
      width: min(1100px, 100% - 2rem);
      margin-left: auto;
      margin-right: auto;
    }
  
    header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      position: fixed;
      z-index:1;
      background-color: rgba(255, 255, 255, 0.884);
      width: 100%;
      padding: 10px;
      box-shadow: 0px 4px 10px 0px rgba(0, 0, 0, 0.363);
    }
  
    header button {
      height: 4rem;
      width: 4rem;
      border-radius: 4rem;
      font-size: 2rem;
      background: black;
      color: #fff;
      box-shadow: 0 0 3px 3px rgba(0, 0, 0, 0.5);
      cursor: pointer;
      transition: all .2s ease;
    }
  
    header button:hover  {
      animation: b 1s infinite linear;
    }
  
     header button:active  {
      box-shadow: 0 0 2px 2px rgba(0, 0, 0, 0.5) !important;  
    }
  
    @keyframes b {
      0% {
        box-shadow: 0 0 3px 3px rgba(0, 0, 0, 0.5);
      }
      25%{
        box-shadow: 0 0 5px 5px rgba(0, 0, 0, 0.5);
      }
      50%{
        box-shadow: 0 0 10px 10px rgba(0, 0, 0, 0.5);
      }
      75%{
        box-shadow: 0 0 5px 5px rgba(0, 0, 0, 0.5);
      }
      100%{
        box-shadow: 0 0 3px 3px rgba(0, 0, 0, 0.5);
      }
    }
  
   .cards-container {
    padding: 50px;
    display: grid;
    gap: 1rem;
    /* grid-template-columns: repeat(auto-fill, minmax(min(25rem,100%), 1fr)); */
    grid-template-columns: repeat(auto-fill, minmax(25rem, 1fr));
    width: 100%;
    margin-top: 2rem;
   }
  
    .card {
      background-color: rgba(204, 204, 27, 0.56);
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      padding: 1rem;
      height: 25rem;
      border-radius: 1rem;
    }
  
     .card p {
      color: #000;
      font-size: 1.6rem;
      font-weight: 600;
    }
  
   .card .date {
      font-size: 1.2rem;
      font-style: italic;
    }
  
    footer {
      background: rgba(0, 0, 0, 0.849);
      color: #fff;
      padding-block: 1rem;
      margin-top: 4rem;
      position: fixed;
      bottom: 0;
      width: 100%;
    }
  
    .overlay {
      position: fixed;
      /* inset: 0; */
      width: 100%;
      height: 100%;
      background: rgba(0,0,0,0.5);
      z-index: 5;
      display: flex;
      justify-content: center;
      align-items: center;
    }
  
    .modal{
      display: flex;
      flex-direction: column;
      gap: 0.5rem;
      width: min(65rem, 100% - 2rem);
      background: #fff;
      border-radius: 2rem;
      padding: 3rem;
      box-shadow: 0 0 5px 5px rgba(0, 0, 0, 0.5);
  
    }
  
    .modal textarea {
      border-radius: 5px;
      resize: none;
      outline: none;
      padding: 1rem;
      font-size: 1.8rem;
    }
  
    .modal button {
      border-radius: 5px;
      outline: none;
      border: none;
      padding: 1rem;
      font-size: 1.7rem;
      font-weight: 600;
      cursor: pointer;
      color: #fff;
      box-shadow: 0 0 3px 3px rgba(0, 0, 0, 0.5);
      transition: all 0.2s ease-in-out;
      margin: 0.5rem 0;
    }
  
    .modal button:nth-of-type(1) {
      background: blue;
    }
  
    .modal button:nth-of-type(2) {
      background: tomato;
    }
  
      .modal button:active {
      box-shadow: 0 0 1px 1px rgba(0, 0, 0, 0.5);
      }
  
  </style>
  