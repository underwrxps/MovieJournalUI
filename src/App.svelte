<script>
  import NewEntry from './NewEntry.svelte';
  import PreviousEntry from './PreviousEntry.svelte';

  // get today's date
  let date = new Date().toLocaleString();

  // for customization
  let titleColor="#ffffff";
  let borderColor="#ffffff";
  let headerColor="#ffffff";

  let user = {
    username: "username",
    entries: [{name: "Movie",
               genre: "Action",
               runtime: 100,
               date: "2002-06-08",
               thoughts: "thoughts"},
              {name: "Other Movie",
               genre: "Horror",
               runtime: 85,
               date: "2023-01-01",
               thoughts: "other thoughts"}]
  }

  // genre counts
  let actionCount = 0;
  let comedyCount = 0;
  let dramaCount = 0;
  let horrorCount = 0;
  let romanceCount = 0;
  let scifiCount = 0;
  
  let numEntries = user.entries.length;
  let totalRuntime = 0;
  for (let i = 0; i < user.entries.length; i++)
  {
    totalRuntime += user.entries[i].runtime;
    if (user.entries[i].genre.includes("Action"))
    {
      actionCount += 1;
    }
    if (user.entries[i].genre.includes("Comedy"))
    {
      comedyCount += 1;
    }
    if (user.entries[i].genre.includes("Drama"))
    {
      dramaCount += 1;
    }
    if (user.entries[i].genre.includes("Horror"))
    {
      horrorCount += 1;
    }
    if (user.entries[i].genre.includes("Romance"))
    {
      romanceCount += 1;
    }
    if (user.entries[i].genre.includes("Sci-Fi"))
    {
      scifiCount += 1;
    }
  }

  // new entry placeholder values
  let entryName = "MovieName";
  let entryGenre = "";
  let entryRuntime = 0;
  let entryDate = "MovieData";
  let entryThoughts = "MovieThoughts";

  // new entry checkbox values
  let actionToggled = false;
  let comedyToggled = false;
  let dramaToggled = false;
  let horrorToggled = false;
  let romanceToggled = false;
  let scifiToggled = false;

  function submitEntry() {
    // still have stuff to do here, but that'll come when i need to show previous entries
    window.alert("Entry Submitted!");
    console.log("Added entry: ", entryName, entryDate);
    let genreString = "";
    if (actionToggled)
    {
      genreString += "Action ";
      actionCount += 1;
    }
    if (comedyToggled)
    {
      genreString += "Comedy ";
      comedyCount += 1;
    }
    if (dramaToggled)
    {
      genreString += "Drama ";
      dramaCount += 1;
    }
    if (horrorToggled)
    {
      genreString += "Horror ";
      horrorCount += 1;
    }
    if (romanceToggled)
    {
      genreString += "Romance ";
      romanceCount += 1;
    }
    if (scifiToggled)
    {
      genreString += "Sci-Fi ";
      scifiCount += 1;
    }

    user.entries.push({name: entryName, genre: genreString, runtime: entryRuntime, date: entryDate, thoughts: entryThoughts})
    numEntries = user.entries.length;
    totalRuntime += entryRuntime;

    if (goalCurrentCount > 0)
    {
      goalCurrentCount -= 1;
    }
    if (goalCurrentCount == 0)
    {
      window.alert("Goal Completed!");
    }
  }

  // initialize previous entry
  let prevEntryIndex = 0;
  let prevName = user.entries[prevEntryIndex].name;
  let prevGenre = user.entries[prevEntryIndex].genre;
  let prevRuntime = user.entries[prevEntryIndex].runtime;
  let prevDate = user.entries[prevEntryIndex].date;
  let prevThoughts = user.entries[prevEntryIndex].thoughts;

  function decrementEntry() {
    if (prevEntryIndex > 0){
      prevEntryIndex -= 1;
      prevName = user.entries[prevEntryIndex].name;
      prevDate = user.entries[prevEntryIndex].date;
      prevGenre = user.entries[prevEntryIndex].genre;
      prevRuntime = user.entries[prevEntryIndex].runtime;
      prevThoughts = user.entries[prevEntryIndex].thoughts;
      console.log("Decremented prevEntryIndex.");
    }
  }

  function incrementEntry() {
    if (prevEntryIndex < user.entries.length - 1){
      prevEntryIndex += 1;
      prevName = user.entries[prevEntryIndex].name;
      prevDate = user.entries[prevEntryIndex].date;
      prevGenre = user.entries[prevEntryIndex].genre;
      prevRuntime = user.entries[prevEntryIndex].runtime;
      prevThoughts = user.entries[prevEntryIndex].thoughts;
      console.log("Incremented prevEntryIndex.");
    }
  }

  // edit entry placeholder values
  let editName = "";
  let editDate = "";
  let editThoughts = "";
  let editRuntime = 0;

  // edit entry checkbox values
  let actionToggledEdit = false;
  let comedyToggledEdit = false;
  let dramaToggledEdit = false;
  let horrorToggledEdit = false;
  let romanceToggledEdit = false;
  let scifiToggledEdit = false;

  function editEntry() {
    user.entries[prevEntryIndex].name = editName;
    user.entries[prevEntryIndex].date = editDate;
    user.entries[prevEntryIndex].runtime = editRuntime;
    user.entries[prevEntryIndex].thoughts = editThoughts;

    let genreString = "";
    if (actionToggledEdit)
    {
      genreString += "Action ";
    }
    if (comedyToggledEdit)
    {
      genreString += "Comedy ";
    }
    if (dramaToggledEdit)
    {
      genreString += "Drama ";
    }
    if (horrorToggledEdit)
    {
      genreString += "Horror ";
    }
    if (romanceToggledEdit)
    {
      genreString += "Romance ";
    }
    if (scifiToggledEdit)
    {
      genreString += "Sci-Fi ";
    }
    user.entries[prevEntryIndex].genre = genreString;

    prevName = editName;
    prevDate = editDate;
    prevGenre = genreString;
    prevRuntime = editRuntime;
    prevThoughts = editThoughts;

    //refresh stats
    actionCount = 0;
    comedyCount = 0;
    dramaCount = 0;
    horrorCount = 0;
    romanceCount = 0;
    scifiCount = 0;
    
    numEntries = user.entries.length;
    totalRuntime = 0;
    for (let i = 0; i < user.entries.length; i++)
    {
      totalRuntime += user.entries[i].runtime;
      if (user.entries[i].genre.includes("Action"))
      {
        actionCount += 1;
      }
      if (user.entries[i].genre.includes("Comedy"))
      {
        comedyCount += 1;
      }
      if (user.entries[i].genre.includes("Drama"))
      {
        dramaCount += 1;
      }
      if (user.entries[i].genre.includes("Horror"))
      {
        horrorCount += 1;
      }
      if (user.entries[i].genre.includes("Romance"))
      {
        romanceCount += 1;
      }
      if (user.entries[i].genre.includes("Sci-Fi"))
      {
        scifiCount += 1;
      }
    }
    window.alert("Entry Edited Successfully!");
  }

  // goal values
  let goalMovieInput = 0;
  let goalCurrentCount = 0;
  function createGoal() {
    if (goalMovieInput > 0){
      goalCurrentCount = goalMovieInput;
      window.alert("Goal Created Successfully!");
    }
  }
</script>

<main>
  <h1 style="color: {titleColor}">Movie Journal</h1>
  <div class="threeSectionBlock" style="border: 5px solid {borderColor}">
    
    <div id="OverviewSection">
      <h2 style="color: {headerColor}">Overview: </h2>
      <p>Username: {user.username}</p>
      <p>Date and Time: {date}</p>
    </div>

    <div id="StatsSection">
      <h2 style="color: {headerColor}">Statistics: </h2>
      <p>Number of Movies Logged: {numEntries}</p>
      <p>Total Watchtime: {totalRuntime}min</p>

      {#if user.entries.length > 0}
      <b>Genre Breakdown: </b>
      {/if}
      {#if actionCount > 0}
      <p>Action Movies: {actionCount}</p>
      {/if}
      {#if comedyCount > 0}
      <p>Comedy Movies: {comedyCount}</p>
      {/if}
      {#if dramaCount > 0}
      <p>Drama Movies: {dramaCount}</p>
      {/if}
      {#if horrorCount > 0}
      <p>Horror Movies: {horrorCount}</p>
      {/if}
      {#if romanceCount > 0}
      <p>Romance Movies: {romanceCount}</p>
      {/if}
      {#if scifiCount > 0}
      <p>Sci-Fi Movies: {scifiCount}</p>
      {/if}
    </div>

    <div id="CreateGoalsSection">
      <h2 style="color: {headerColor}">Set Movie-Watching Goal:</h2>
      <p>Number of Movies you want to watch: </p><input type=number bind:value={goalMovieInput}>
      <button id="createGoalButton" on:click={createGoal}>Create Goal</button><br><br>
      {#if goalCurrentCount > 0}
        <b>Movies Remaining: {goalCurrentCount}</b>
      {/if}
    </div>

  </div>

  <br>

  <div class="threeSectionBlock" style="border: 5px solid {borderColor}">

    <div id="NewEntrySection">
      <h2 style="color: {headerColor}">New Entry:</h2>
      <NewEntry bind:movieName={entryName} bind:actionChecked={actionToggled} bind:comedyChecked={comedyToggled} bind:dramaChecked={dramaToggled}
       bind:horrorChecked={horrorToggled} bind:romanceChecked={romanceToggled} bind:scifiChecked={scifiToggled}
       bind:movieRuntime={entryRuntime} bind:movieDate={entryDate} bind:movieThoughts={entryThoughts}/>
      <button id="submitEntryButton" on:click={submitEntry}>Submit</button>
    </div>

    <div id="PreviousEntriesSection">
      <h2 style="color: {headerColor}">Previous Entries:</h2>
      <p></p>
      <PreviousEntry bind:mName={prevName} bind:mGenre={prevGenre} bind:mRuntime={prevRuntime} bind:mDate={prevDate} bind:mThoughts={prevThoughts}/>
      <button id="previousEntriesPrevButton" on:click={decrementEntry}>Prev Entry</button>
      <button id="previousEntriesNextButton" on:click={incrementEntry}>Next Entry</button>
    </div>

    <div id="EditEntrySection">
      <h2 style="color: {headerColor}">Edit Previous Entry:</h2>
      <NewEntry bind:movieName={editName} bind:movieDate={editDate} bind:actionChecked={actionToggledEdit} bind:comedyChecked={comedyToggledEdit}
      bind:dramaChecked={dramaToggledEdit} bind:horrorChecked={horrorToggledEdit} bind:scifiChecked={scifiToggledEdit}
      bind:movieRuntime={editRuntime} bind:movieThoughts={editThoughts}/>
      <button id="editEntryButton" on:click={editEntry}>Confirm Edit</button><br>
    </div>

  </div> 

  <br>

  <div class="threeSectionBlock">
    <div class="customizationSection">
      <h3 style="color: {headerColor}">Customization:</h3>
      <p>Select Title Color:</p>
      <input type=color bind:value={titleColor} on:change={() => window.alert("Title Color Updated!")}/>
      <p>Select Border Color:</p>
      <input type=color bind:value={borderColor} on:change={() => window.alert("Border Color Updated!")}/>
      <p>Select Header Color:</p>
      <input type=color bind:value={headerColor} on:change={() => window.alert("Header Color Updated!")}/>
    </div>
  </div>

</main>