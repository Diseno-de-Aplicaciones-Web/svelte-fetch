<script>

  let tarefas = []

  function manexadorActualizarTarefas() {
    const promesaDeResposta = fetch("http://localhost:8000/tarefas")
    promesaDeResposta.then(reaccionAResposta)
  }

  function reaccionAResposta(resposta) {
    const promesaDeDatos = resposta.json()
    promesaDeDatos.then(reaccionOsDatos)
  }

  function reaccionOsDatos(datos) {
    tarefas = datos
  }

</script>

<main>

  <h1>Tarefas</h1>

  <p>Tes {tarefas.length} tarefas na lista.</p>

  <button on:click={manexadorActualizarTarefas}>Actualizar tarefas</button>
  <span>&lt;- Click aquí</span>
  
  {#each tarefas as item}
    <li>{item.descripcion}<input type="checkbox" checked={item.completada}/></li>
  {/each}

</main>