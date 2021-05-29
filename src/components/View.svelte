<script>
  import { params } from "@roxi/routify"
  import PackCard from "./PackCard.svelte";
  import StickerCard from "./StickerCard.svelte";
  import SearchCard from "./SearchCard.svelte";
  import Stickers from "../stickers.json";
  export let type = "";
  export let searchQuery = "";
  let pack = $params.pack
</script>

<svelte:head>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Hind:wght@300;400;500;600;700&display=swap');
    html, body {
        background-color: #2C2F33;
        font-family: 'Hind', sans-serif;
        text-rendering: optimizeLegibility;
        color: white;
        top: -40px;
    }
    input {
        text-align: center;
        background-color: #36393f;
        color: white;
        border: 4px solid #36393f;
        border-radius: 5px
    }
    input:focus {
        outline: none !important;
        border: 4px solid #3f434a;
    }
  </style>
</svelte:head>
  
  <style>
  
    main {
      margin: 15vw;
      display: flex;
      flex-direction: row;
      flex-wrap: wrap;
      gap: 14px;
      justify-items: flex-start;
      justify-content: center;
  
      padding: 14px;
      background-color: #36393f;
      border-radius: 5px;
      box-shadow: 0 2px 10px 0 rgb(0 0 0 / 20%);
      margin-top: 10px;
      margin-bottom: 10px;
    }
  
  </style>
  
  <main>
    {#if searchQuery && type == "sticker"}
      {#each Object.keys(Stickers[pack.replace(/\+/g, " ")]["stickers"]) as sticker}
          {#if (sticker.toLowerCase().includes(searchQuery.toLowerCase()))}
            <StickerCard name="{sticker}" url={Stickers[pack.replace(/\+/g, " ")]["stickers"][sticker]} />  
          {/if}
      {/each}
    {:else if searchQuery}
      {#each Object.keys(Stickers) as pack}
        {#each Object.keys(Stickers[pack]["stickers"]) as sticker}
          {#if (sticker.toLowerCase().includes(searchQuery.toLowerCase()))}
              <SearchCard name={sticker} pack={pack} url={Stickers[pack].stickers[sticker]} format={Stickers[pack].format}/>
          {/if}
        {/each}
      {/each}
    {:else if type == "pack"}
      {#each Object.keys(Stickers) as pack} 
        <PackCard name="{pack}" url={Stickers[pack].stickers[Object.keys(Stickers[pack].stickers)[0]]} format={Stickers[pack].format}/>
      {/each}
    {:else if type == "sticker"}
      {#each Object.keys(Stickers[pack.replace(/\+/g, " ")]["stickers"]) as sticker}
        <StickerCard name="{sticker}" url={Stickers[pack.replace(/\+/g, " ")]["stickers"][sticker]} />  
      {/each}
    {/if}
  </main>