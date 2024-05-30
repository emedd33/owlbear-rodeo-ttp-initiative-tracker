<script>
  import OBR from "@owlbear-rodeo/sdk";

  const onClick = () => {
    console.log("Button clicked");
    OBR.notification.show(`Button clicked`);
  };
</script>

<h1 class="text-3xl font-bold underline bg-slate-500">Hello world!</h1>
<button class="bg-slate-500 text-white px-4 py-2 rounded" on:click={onClick}
  >Click me</button
>
