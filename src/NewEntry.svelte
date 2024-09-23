<!-- add genre and length of movie -->

<script>
    export let movieName = "";
    export let movieDate = "";
    export let movieThoughts = "";
    export let movieRuntime = 0;
    export let actionChecked = false;
    export let comedyChecked = false;
    export let dramaChecked = false;
    export let horrorChecked = false;
    export let romanceChecked = false;
    export let scifiChecked = false;
</script>

<b>Name of Movie: </b>
<input id="name" bind:value={movieName}><br>
<b>Date Watched: </b>
<input type=date id="date" bind:value={movieDate}><br>
<div id="genreCheckboxes">
    <b>Genre(s): </b>
    <input class="genreCheckbox" id="actionCheck" type="checkbox" value="Action" bind:checked={actionChecked}>
    <label for="actionCheck">
        Action
    </label>

    <input class="genreCheckbox" id="comedyCheck" type="checkbox" value="Comedy" bind:checked={comedyChecked}>
    <label for="comedyCheck">
        Comedy
    </label>

    <input class="genreCheckbox" id="dramaCheck" type="checkbox" value="Drama" bind:checked={dramaChecked}>
    <label for="dramaCheck">
        Drama
    </label>

    <input class="genreCheckbox" id="horrorCheck" type="checkbox" value="Horror" bind:checked={horrorChecked}>
    <label for="horrorCheck">
        Horror
    </label>

    <input class="genreCheckbox" id="romanceCheck" type="checkbox" value="Romance" bind:checked={romanceChecked}>
    <label for="romanceCheck">
        Romance
    </label>

    <input class="genreCheckbox" id="scifiCheck" type="checkbox" value="Sci-Fi" bind:checked={scifiChecked}>
    <label for="scifiCheck">
        Sci-Fi
    </label>
</div>
<b>Runtime (min): </b>
<input id="runtime" type="number" bind:value={movieRuntime}><br>
<b>Thoughts on the film: </b><br>
<textarea id="thoughts" bind:value={movieThoughts}></textarea><br>


<style>
</style>