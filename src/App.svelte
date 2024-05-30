<script lang="ts">
  import OBR from "@owlbear-rodeo/sdk";
  OBR.broadcast.onMessage("rodeo.owlbear.tracker.message", async (event) => {
    // Use the data from the event
    if (event.data === "open") OBR.action.open();
    else if (event.data === "close") OBR.action.close();
  });

  const onClick = async (signal: string) => {
    const players = await OBR.party.getPlayers();
    if (players.length === 0) {
      return;
    }
    const receiver = players[0];
    if (receiver) {
      console.log(receiver);
      OBR.broadcast.sendMessage("rodeo.owlbear.tracker.message", signal);
    }
  };
</script>

<h1 class="text-3xl font-bold underline bg-slate-500">Hello world!</h1>
<button
  class="bg-slate-500 text-white px-4 py-2 rounded"
  on:click={() => onClick("open")}>Open</button
>
<button
  class="bg-slate-500 text-white px-4 py-2 rounded"
  on:click={() => onClick("close")}>Close</button
>
