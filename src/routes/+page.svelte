<script>
  function ir() {
    window.location.href = "./home";
  }
</script>

<svelte:head>
  <link
    rel="stylesheet"
    href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css"
  />
</svelte:head>

<h1 class="titleIndex">
  Seja bem-vindo ao <br />
  <span class="titleLogo">Pro-Camp</span>
</h1>
<p class="texIndex">
  O melhor sistema de campeonato para gamers. <br />
  Caso você seja bom no que faz, inscreva-se e teste as suas habilidades player!
</p>
<button class="link" on:click={ir}>Saiba mais</button>

<style>
  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: "Segoe UI", Roboto, Oxygen, Ubuntu, Cantarell, "Open Sans",
      "Helvetica Neue", sans-serif;
  }

  :global(body) {
    background:
      linear-gradient(rgba(0, 0, 0, 0.7), rgba(0, 0, 0, 0.7)),
      url("https://images.unsplash.com/photo-1542751371-adc38448a05e?ixlib=rb-1.2.1&auto=format&fit=crop&w=1920&q=80")
        no-repeat center center fixed;
    background-size: cover;
    color: #ffffff;
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding: 1.5rem;
    text-align: center;
    animation: fadeIn 1s ease;
  }

  .titleIndex {
    font-size: 2rem;
    margin-bottom: 1.5rem;
    line-height: 1.4;
    font-weight: 400;
  }

  .titleLogo {
    color: #4caf50;
    font-size: 2.5rem;
    font-weight: 700;
    display: inline-block;
    margin-top: 0.5rem;
    text-shadow: 0 0 10px rgba(76, 175, 80, 0.3);
    position: relative;
  }

  .titleLogo::after {
    content: "";
    display: block;
    width: 80px;
    height: 3px;
    background: #4caf50;
    margin: 0.8rem auto;
    border-radius: 3px;
  }

  .texIndex {
    font-size: 1.1rem;
    line-height: 1.6;
    margin-bottom: 2.5rem;
    max-width: 500px;
    color: #ddd;
  }

  .link {
    background: #4caf50;
    color: white;
    border: none;
    padding: 1rem 2rem;
    border-radius: 5px;
    font-size: 1.1rem;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.3s ease;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.3);
    position: relative;
    overflow: hidden;
  }

  .link:hover {
    background: #3e8e41;
    transform: translateY(-3px);
    box-shadow: 0 6px 12px rgba(0, 0, 0, 0.4);
  }

  .link::after {
    content: "";
    position: absolute;
    top: 50%;
    left: 50%;
    width: 5px;
    height: 5px;
    background: rgba(255, 255, 255, 0.5);
    opacity: 0;
    border-radius: 100%;
    transform: scale(1, 1) translate(-50%);
    transform-origin: 50% 50%;
  }

  .link:focus:not(:active)::after {
    animation: ripple 1s ease-out;
  }

  @keyframes ripple {
    0% {
      transform: scale(0, 0);
      opacity: 0.5;
    }
    100% {
      transform: scale(20, 20);
      opacity: 0;
    }
  }

  @keyframes fadeIn {
    from {
      opacity: 0;
    }
    to {
      opacity: 1;
    }
  }

  @media (min-width: 768px) {
    .titleIndex {
      font-size: 2.5rem;
    }

    .titleLogo {
      font-size: 3rem;
    }

    .texIndex {
      font-size: 1.2rem;
    }
  }
</style>
