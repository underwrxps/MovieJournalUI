<!-- add genre and length of movie -->

<script>
    export let mName = "";
    export let mDate = "";
    export let mThoughts = "";
    export let mGenre = "";
    export let mRuntime = 0;
</script>

<b>Name of Movie: </b>
<p>{mName}</p>
<b>Date Watched: </b>
<p>{mDate}</p>
<b>Genre(s): </b>
<p>{mGenre}</p>
<b>Runtime: </b>
<p>{mRuntime} min</p>
<b>Thoughts on the film: </b>
<p>{mThoughts}</p>

<style>
    p {
        margin: 0;
        padding: 0;
    }
</style>