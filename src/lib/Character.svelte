<script>
  export let character;
  let status = { Alive: "😀", Dead: "😡", Unknown: "🤔" };
</script>

<article class="character">
  <img src={character.image} alt={character.name} />
  <h1>{character.name} - {character.origin.name}</h1>
  <!-- <h3>{character.species} | |{character.status}</h3> -->

  {#if character.status === "Alive"}
    <h3>{character.species} -{status.Alive} {character.status}</h3>
  {:else if character.status === "Dead"}
    <h3>{character.species} -{status.Dead} {character.status}</h3>
  {:else}
    <h3>{character.species} -{status.Unknown} {character.status}</h3>
  {/if}
</article>

<style>
  .character {
    background: #101010;
    text-align: center;
    border-radius: 7px;
  }

  .character img {
    border-radius: 7px 7px 0 0;
  }
</style>
