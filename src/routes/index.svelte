<script lang="ts">
    import { fetchMeetings } from './calls';
</script>


<h1>Welcome to CBC</h1>

{#await fetchMeetings()}
  <p>Fetching data...</p>
  {:then data}
    {#each data.splice(0, 10) as meeting}
      <div class='meeting'>
        <span>{meeting.title}</span>
        <span>{meeting.date}</span>
        <ul>
            {#each meeting.deliberations as deliberation}
                <li> <a href={"deliberations/" + deliberation.id}>{deliberation.id}</a> - {deliberation.title} - {deliberation.commune}</li>
            {/each}
        </ul>
      </div>
    {/each}
{/await}



