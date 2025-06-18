<script> 
      import {palavras} from '$lib/data.js';

    let termoPesquisado = '';
  
    $: termosFiltrados = palavras.filter(palavra => palavra.termo.toLowerCase().includes(termoPesquisado.toLowerCase()));

    let palavradia = palavras[Math.trunc(Math.random()*palavras.length)]

    console.log(palavradia)

</script>
  
  <style>
    main {
      font-family: sans-serif;
      max-width: 800px;
      margin: 20px auto;
      padding: 20px;
      border: 1px solid #eee;
      border-radius: 8px;
      box-shadow: 0 2px 4px rgba(0,0,0,0.1);
    }
    h1 {
      text-align: center;
      color: #333;
    }
    input {
      width: calc(100% - 20px);
      padding: 10px;
      margin-bottom: 20px;
      border: 1px solid #ddd;
      border-radius: 4px;
      font-size: 16px;
    }
    .termo {
      margin-bottom: 15px;
      padding: 10px;
      border: 1px solid #e0e0e0;
      border-radius: 6px;
      background-color: #f9f9f9;
    }
    .termo h2 {
      margin-top: 0;
      color: #007bff;
      font-size: 1.2em;
    }
    .no-results {
      text-align: center;
      color: #777;
      padding: 20px;
    }
  </style>
  <div class="main">
  <center>
  <h3>PALAVRA DO MOMENTO</h3>
  <h1>{palavradia.termo}</h1>
  </center>
  </div>
  
  <main>
 
    <h1>Dicionário</h1>
  
    <input
      type="text"
      bind:value={termoPesquisado}
      placeholder="Pesquise por um termo..."
    />
  
    {#if termosFiltrados.length > 0}
      {#each termosFiltrados as palavra}
        <div class="termo">
          <h2><a href="\dicionario\{palavra.endereco}">{palavra.termo}</a></h2>
        </div>
      {/each}
    {:else}
      <p class="no-results">Nenhum termo encontrado para "{termoPesquisado}".</p>
    {/if}
  </main>