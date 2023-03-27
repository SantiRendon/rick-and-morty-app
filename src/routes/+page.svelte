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
    <article class="btns">
      <button class="btn" on:click={previousPage} disabled={pageNum === 1}
        >Previous</button
      >
      <button class="btn" on:click={nextPage} disabled={pageNum === 42}
        >Next</button
      >
    </article>
  
    <section class="grid">
      {#each characters as character}
        <Character {character} />
      {/each}
    </section>
  </article>
  
  <style>
    .title {
      font-size: 2.7rem;
      font-weight: bolder;
      text-align: center;
    }
  
    .btns {
      display: flex;
      justify-content: space-between;
    }
  
    .btn {
      padding: 5px 10px;
      margin: 0 0 15px 0;
      border: 1px solid whitesmoke;
      border-radius: 5px;
      background: wheat;
      font-weight: bold;
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
  