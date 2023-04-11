<script>

function handlePress(e) {
    let input = e.target;

    console.log(input.value)
}

</script>

<input on:keyup={handlePress} type="search" name="search" id="search" class="search" placeholder="Search...">

<style>

.search{
      appearance: none;
      width: 25%;
      height: 2.5rem;
      border-radius: 5px;
      transition: background ease-out .5s;
    }
    .search:focus{
      /* appearance: none; */
      background: #FAEEBC;
    }

    .search::-webkit-search-cancel-button{
      padding: 5px;
      margin-right: .5rem ;
      cursor: pointer;
    }

</style>