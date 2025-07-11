<script>
import '../../global.css'
  function tabela() {
    window.location.href = "../tabela";
  }

  let times = [
    {
      nome: "Fxx",
      treinador: "Samuel Lucas",
      img: "https://i.imgur.com/lUJnsEa.jpeg",
      alt: "Time fxx",
      jogadores: [
        { nome: "Samuel Lucas", foto: "https://i.imgur.com/lUJnsEa.jpeg ", lider: true },
        { nome: "Anthony Fernandes", foto: "https://i.imgur.com/unvBGmR.jpeg", lider: false },
      ],
    },
    {
      nome: "Soldados.Son",
      treinador: "Alex",
      img: "https://i.imgur.com/B9DLwTO.jpeg",
      alt: "Time ss",
      jogadores: [
        { nome: "Alex", foto: "https://i.imgur.com/B9DLwTO.jpeg", lider: true },
      ],
    },
    {
      nome: "Night Fury",
      treinador: "Maxwell",
      img: "https://i.imgur.com/nIwEWER.jpeg",
      alt: "Time night",
      jogadores: [
        { nome: "Maxwell", foto: "https://i.imgur.com/nIwEWER.jpeg", lider: true },
      ],
    },
    {
      nome: "SpaceX",
      treinador: "Danilo",
      img: "https://i.imgur.com/4vt3uvX.jpeg",
      alt: "Time spacex",
      jogadores: [
        { nome: "Danilo", foto: "https://i.imgur.com/4vt3uvX.jpeg", lider: true },
      ],
    },
    {
      nome: "Team Aim",
      treinador: "Luiz Miguel",
      img: "https://i.imgur.com/fzH8cLY.jpeg",
      alt: "Time TeamAim",
      jogadores: [
        { nome: "Luiz Miguel", foto: "https://i.imgur.com/fzH8cLY.jpeg", lider: true },
      ],
    },
  ];

  let timeSelecionado = null;

  function verMais(time) {
    timeSelecionado = time;
  }

  function fecharModal() {
    timeSelecionado = null;
  }
</script>

<svelte:head>
  <link
    rel="stylesheet"
    href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css"
  />
</svelte:head>

<header class="main-header">
  <div class="header-content">
    <h1 class="logo">Pro-Camp</h1>
    <button on:click={tabela}>Tabela</button>
  </div>
</header>

<main class="teams-container">
  <h2 class="section-title">Nossos Times</h2>
  <ul class="teams-list">
    {#each times as time (time.nome)}
      <li class="team-card">
        <article>
          <div class="team-image">
            <img src={time.img} alt={time.alt} loading="lazy" />
          </div>
          <div class="team-info">
            <h3 class="team-name">{time.nome}</h3>
            <p class="team-coach">Treinador: {time.treinador}</p>
            <button class="view-more-btn" on:click={() => verMais(time)}>
              Ver mais <i class="fas fa-chevron-right"></i>
            </button>
          </div>
        </article>
      </li>
    {/each}
  </ul>
</main>

<footer class="main-footer">
  <p>&copy; 2025 Pro-Camp. Todos os direitos reservados.</p>
</footer>

{#if timeSelecionado}
  <div class="modal">
    <div class="modal-header">
      <h2>{timeSelecionado.nome} — Jogadores</h2>
      <button class="close-btn" on:click={fecharModal}>×</button>
    </div>

    <!-- Líder -->
    {#each timeSelecionado.jogadores.filter(j => j.lider) as lider}
      <div class="lider">
        <img src={lider.foto} alt={lider.nome} />
        <span>{lider.nome} (Líder)</span>
      </div>
    {/each}

    <!-- Outros jogadores -->
    <div class="jogadores-lista">
      {#each timeSelecionado.jogadores.filter(j => !j.lider) as jogador}
        <div class="jogador">
          <img src={jogador.foto} alt={jogador.nome} />
          <span>{jogador.nome}</span>
        </div>
      {/each}
    </div>
  </div>
{/if}

<style>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: "Segoe UI", Roboto, Oxygen, Ubuntu, Cantarell, "Open Sans",
      "Helvetica Neue", sans-serif;
  }

  :global(body) {
    background-color: #121212;
    color: white;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    margin: 0;
  }

  .main-header {
    background-color: rgba(0, 0, 0, 0.8);
    padding: 1rem;
    position: sticky;
    top: 0;
    z-index: 100;
    backdrop-filter: blur(5px);
    border-bottom: 1px solid #333;
  }

  .header-content {
    display: flex;
    justify-content: space-between;
    align-items: center;
    max-width: 1200px;
    margin: 0 auto;
    width: 100%;
  }

  .logo {
    font-size: 1.5rem;
    font-weight: 700;
    color: #4caf50;
    text-shadow: 0 0 10px rgba(76, 175, 80, 0.3);
  }

  .header-content button {
    background: transparent;
    color: white;
    border: none;
    padding: 0.5rem;
    font-size: 0.9rem;
    cursor: pointer;
    transition: all 0.3s ease;
    border-radius: 4px;
  }

  .header-content button:hover {
    color: #4caf50;
    transform: translateY(-2px);
  }

  main {
    flex: 1;
    padding: 1.5rem;
    max-width: 1200px;
    margin: 0 auto;
    width: 100%;
  }

  .section-title {
    text-align: center;
    margin: 1.5rem 0;
    font-size: 1.8rem;
    color: #4caf50;
    position: relative;
  }

  .section-title::after {
    content: "";
    display: block;
    width: 60px;
    height: 3px;
    background: #4caf50;
    margin: 0.5rem auto;
    border-radius: 3px;
  }

  .teams-list {
    list-style: none;
    display: grid;
    grid-template-columns: 1fr;
    gap: 1.5rem;
    padding: 0;
  }

  @media (min-width: 600px) {
    .teams-list {
      grid-template-columns: repeat(2, 1fr);
    }
  }

  .team-card {
    background: rgba(30, 30, 30, 0.8);
    border-radius: 10px;
    overflow: hidden;
    transition:
      transform 0.3s ease,
      box-shadow 0.3s ease;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
  }

  .team-card:hover {
    transform: translateY(-5px);
    box-shadow: 0 10px 20px rgba(0, 0, 0, 0.4);
  }

  .team-image {
    width: 100%;
    height: 180px;
    overflow: hidden;
  }

  .team-image img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    transition: transform 0.5s ease;
  }

  .team-card:hover .team-image img {
    transform: scale(1.05);
  }

  .team-info {
    padding: 1.2rem;
  }

  .team-name {
    font-size: 1.3rem;
    margin-bottom: 0.5rem;
    color: #4caf50;
  }

  .team-coach {
    color: #aaa;
    font-size: 0.9rem;
    margin-bottom: 1rem;
  }

  .view-more-btn {
    background: #4caf50;
    color: white;
    border: none;
    padding: 0.6rem 1.2rem;
    border-radius: 5px;
    cursor: pointer;
    font-weight: 600;
    display: flex;
    align-items: center;
    gap: 0.5rem;
    transition: all 0.3s ease;
    width: 100%;
    justify-content: center;
  }

  .view-more-btn:hover {
    background: #3e8e41;
    transform: translateY(-2px);
  }

  .view-more-btn i {
    transition: transform 0.3s ease;
  }

  .view-more-btn:hover i {
    transform: translateX(3px);
  }

  .main-footer {
    background-color: rgba(0, 0, 0, 0.9);
    padding: 1.2rem;
    text-align: center;
    font-size: 0.9rem;
    color: #aaa;
    margin-top: auto;
  }

  /* Modal styles reaproveitados */
  .modal {
    position: fixed;
    top: 0; left: 0; right: 0; bottom: 0;
    background-color: rgba(18, 18, 18, 0.95);
    display: flex;
    flex-direction: column;
    padding: 2rem;
    color: white;
    z-index: 2000;
  }

  .modal-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    border-bottom: 2px solid #4caf50;
    padding-bottom: 1rem;
    margin-bottom: 1rem;
  }

  .modal-header h2 {
    color: #4caf50;
    margin: 0;
  }

  .close-btn {
    background: #4caf50;
    border: none;
    padding: 0.5rem 1rem;
    color: white;
    font-weight: bold;
    font-size: 1.2rem;
    cursor: pointer;
    border-radius: 6px;
    transition: background 0.3s ease;
  }

  .close-btn:hover {
    background: #3e8e41;
  }

  .lider {
    background-color: #4caf50;
    color: black;
    font-weight: bold;
    padding: 1rem;
    border-radius: 10px;
    margin-bottom: 1rem;
    display: flex;
    align-items: center;
    gap: 1rem;
  }

  .lider img {
    width: 60px;
    height: 60px;
    border-radius: 50%;
    object-fit: cover;
  }

  .jogador {
    background: rgba(30, 30, 30, 0.8);
    border-radius: 10px;
    padding: 0.8rem;
    margin-bottom: 0.8rem;
    display: flex;
    align-items: center;
    gap: 1rem;
    transition: background 0.3s ease;
  }

  .jogador:hover {
    background: #2f2f2f;
  }

  .jogador img {
    width: 50px;
    height: 50px;
    border-radius: 50%;
    object-fit: cover;
  }

  .jogadores-lista {
    overflow-y: auto;
    flex: 1;
  }
</style>
