<script>
    let tarefaEditandoIndice = $state();
    let tarefaEditando = $state();
	const tarefasPendentes = $state([]);
    const tarefasConcluidas = $state([]);
	let tarefaNova = $state();
 
    function adicionarTarefa() {
        tarefasPendentes.push(tarefaNova);
        tarefaNova = '';
    }
 
    function excluirTarefa(i) {
        tarefasPendentes.splice(i, 1);
    }
 
    function editarTarefa(i) {
        tarefaEditandoIndice = i;
        tarefaEditando = tarefasPedentes[i];
    }
 
    function salvarTarefa(i) {
        tarefasPendentes[i] = tarefaEditando;
        tarefaEditandoIndice = null;
    }
 
    function cancelarEdicao() {}

	function marcarComoConcluida(indice) {
    const tarefaConcluida = tarefasPendentes.splice(indice, 1)[0];
    tarefasConcluidas.push(tarefaConcluida);
}

function marcarComoPendente(indice) {
    const tarefaPendente = tarefasConcluidas.splice(indice, 1)[0];
    tarefasPendentes.push(tarefaPendente);
}
</script>
<div class="container">
<center>
<h2 style="font-size: 50px; font-family:'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif">Lista de tarefas</h2>
<p>
    <input placeholder="Digite a tarefa..." bind:value={tarefaNova} />
    <button onclick={adicionarTarefa} style="background-color: aquamarine; width: 10%; height: 10%">➕</button>
</p>
<ul>
    {#each tarefasPendentes as tarefa, i}
        <li>
            {#if tarefaEditandoIndice == i}
                <input bind:value={tarefaEditando} />
                <button onclick={() => salvarTarefa(i)} style="background-color: gold; width: 10%; height: 10%">💾</button>
                <button onclick={cancelarEdicao} style="background-color: red; width: 10%; height: 10%">❌</button>
            {:else}
            {tarefa}
            <button onclick={() => editarTarefa(i)} style="background-color: orange; width: 10%; height: 10%">✏</button>
            <button onclick={() => excluirTarefa(i)} style="background-color: red; width: 10%; height: 10%">🗑</button>
            <button onclick={() => marcarComoConcluida(i)} style="background-color: chartreuse; width: 10%; height: 10%">✅</button>
            {/if}

        </li>
    {/each}
</ul>
<br>
<h2 style="font-size: 50px; font-family:'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif">Tarefas Concluídas</h2>
<ul>
    {#each tarefasConcluidas as tarefa, i}
        <li>
            {tarefa}
            <button onclick={() => marcarComoPendente(i)} style="background-color: red; width: 10%; height: 10%">❌</button>
        </li>
    {/each}
</ul>
</center>
</div>
<style>
    .container{
        width: 100%;
        height: 100%;
        background-color: aqua;    
        }
</style>