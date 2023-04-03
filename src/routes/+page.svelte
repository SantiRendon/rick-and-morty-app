<script>
    import Character from "$lib/Character.svelte";
    let characters = [];
    let pageNum = 1;
    async function loadCharacters() {
      const response = await fetch(
        `https://rickandmortyapi.com/api/character?page=${pageNum}`
      );
      const data = await response.json();
    //   console.log(data);
  
      characters = data.results;
    }
  
    function previousPage() {
      pageNum--;
      loadCharacters();
    }
  
    function nextPage() {
      pageNum++;
      loadCharacters();
    }
  
    loadCharacters();
  </script>
  
  <h1 class="title">Rick and Morty: Sveltekit</h1>
  
  <article class="content">
    <section class="btns">
      <button class="btn" on:click={previousPage} disabled={pageNum === 1}>Previous</button>
      <input type="search" name="search" id="search" class="search" placeholder="Search...">
      <button class="btn" on:click={nextPage} disabled={pageNum === 42}>Next</button>
    </section>
    <section class="grid">
      {#each characters as character}
        <Character {character} />
      {/each}
    </section>
  </article>
  
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Noto+Emoji&display=swap');
    .title {
      font-size: 2.7rem;
      font-weight: bolder;
      text-align: center;
    }
  
    .btns {
      display: flex;
      justify-content: space-between;
      padding-bottom: 15px;
    }
  
    .btn {
      padding: 5px 10px;
      border: 1px solid whitesmoke;
      border-radius: 5px;
      background: wheat;
      font-weight: bold;
    }

    .search{
      appearance: none;
      width: 25%;
      height: 2.5rem;
      border-radius: 5px;
    }
    .search:focus{
      /* appearance: none; */
      transition: background ease-out .5s;
      background: #FAEEBC;
    }

    .search::-webkit-search-cancel-button{
      padding: 5px;
      margin-right: .5rem ;
      cursor: pointer;
    }
  
    .btn:hover:not(button[disabled]) {
      cursor: pointer;
      transition: background ease-out 0.5s;
      background: whitesmoke;
    }
  
    .btn[disabled]:hover {
      cursor: not-allowed;
    }
  
    .content {
      max-width: 1250px;
      margin: auto;
      /* background-color: blueviolet; */
    }
  
    .grid {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 1rem;
    }
  </style>
  