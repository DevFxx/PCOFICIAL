<script>
import '../../global.css'
  // Funções para navegação
  function tabela() {
    window.location.href = "../tabela";
  }

  function voltarParaPrincipal() {
    window.location.href = "./../home";
  }

  // Dados dos times (pode puxar de API ou arquivo depois)
  const times = [
    {
      posicao: 1,
      nome: "Fxx",
      img: "https://i.imgur.com/lUJnsEa.jpeg",
      alt: "Fxx",
      p: 0,
      j: 0,
      v: 0,
      e: 0,
      d: 0,
    },
    {
      posicao: 2,
      nome: "Soldados Sombrios",
      img: "https://i.imgur.com/B9DLwTO.jpeg",
      alt: "Soldados.Son",
      p: 0,
      j: 0,
      v: 0,
      e: 0,
      d: 0,
    },
    {
      posicao: 3,
      nome: "Night Fury",
      img: "https://i.imgur.com/nIwEWER.jpeg",
      alt: "Night Fury",
      p: 0,
      j: 0,
      v: 0,
      e: 0,
      d: 0,
    },
    {
      posicao: 4,
      nome: "SpaceX",
      img: "https://i.imgur.com/4vt3uvX.jpeg",
      alt: "SpaceX",
      p: 0,
      j: 0,
      v: 0,
      e: 0,
      d: 0,
    },
    {
      posicao: 5,
      nome: "Team Aim",
      img: "https://i.imgur.com/fzH8cLY.jpeg",
      alt: "Team Aim",
      p: 0,
      j: 0,
      v: 0,
      e: 0,
      d: 0,
    },
  ];
</script>

<svelte:head>
  <link
    rel="stylesheet"
    href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css"
  />
</svelte:head>

<header class="main-header">
  <div class="header-content">
    <h1 class="logo" on:click={voltarParaPrincipal}>Pro-Camp</h1>
    <button on:click={tabela}>Tabela</button>
  </div>
</header>

<main>
  <h2 class="section-title">Tabela do Campeonato</h2>
  <div class="table-container">
    <table class="standings-table">
      <thead>
        <tr>
          <th>Posição</th>
          <th>Time</th>
          <th>P</th>
          <th>J</th>
          <th>V</th>
          <th>E</th>
          <th>D</th>
        </tr>
      </thead>
      <tbody>
        {#each times as time (time.posicao)}
          <tr>
            <td>{time.posicao}</td>
            <td>
              <div class="team-info">
                <img src={time.img} alt={time.alt} class="team-logo" />
                <span>{time.nome}</span>
              </div>
            </td>
            <td>{time.p}</td>
            <td>{time.j}</td>
            <td>{time.v}</td>
            <td>{time.e}</td>
            <td>{time.d}</td>
          </tr>
        {/each}
      </tbody>
    </table>
  </div>
</main>

<footer class="main-footer">
  <p>&copy; 2025 Pro-Camp. Todos os direitos reservados.</p>
</footer>

<style>
  /* Reset e Estilos Base */
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: "Segoe UI", Roboto, Oxygen, Ubuntu, Cantarell, "Open Sans",
      "Helvetica Neue", sans-serif;
  }

  :global(body) {
    color: #ffffff;
    min-height: 100vh;
    background-color: #121212;
    display: flex;
    flex-direction: column;
    margin: 0;
  }

  /* Header */
  .main-header {
    background-color: rgba(0, 0, 0, 0.8);
    padding: 1rem;
    position: relative;
    top: 0;
    left: 0;
    right: 0;
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
    cursor: pointer;
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

  .table-container {
    width: 100%;
    overflow-x: auto;
  }

  .standings-table {
    width: 100%;
    border-collapse: collapse;
    background: rgba(30, 30, 30, 0.8);
    border-radius: 10px;
    overflow: hidden;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
    margin-bottom: 2rem;
  }

  .standings-table th {
    background-color: #4caf50;
    color: white;
    padding: 0.8rem;
    text-align: left;
  }

  .standings-table tr:nth-child(even) {
    background-color: rgba(50, 50, 50, 0.5);
  }

  .standings-table tr:hover {
    background-color: rgba(76, 175, 80, 0.2);
  }

  .standings-table td {
    padding: 0.8rem;
    border-bottom: 1px solid #333;
  }

  .team-info {
    display: flex;
    align-items: center;
    gap: 0.8rem;
  }

  .team-logo {
    width: 30px;
    height: 30px;
    border-radius: 50%;
    object-fit: cover;
  }

  @media (max-width: 600px) {
    .standings-table {
      font-size: 0.8rem;
    }

    .standings-table th,
    .standings-table td {
      padding: 0.5rem;
    }

    .team-logo {
      width: 20px;
      height: 20px;
    }
  }

  /* Footer */
  .main-footer {
    background-color: rgba(0, 0, 0, 0.9);
    padding: 1.2rem;
    text-align: center;
    font-size: 0.9rem;
    color: #aaa;
    margin-top: auto;
  }
</style>
