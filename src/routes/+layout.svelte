<script>
  let season = ""; // Holds the current season class
  let headerImg = "";

  // Function to manually set the season
  function setSeason(seasonClass) {
    season = seasonClass;
  }

  // Update the season based on date or user interaction
  $: {
    const currentMonth = new Date().getMonth();
    if (currentMonth === 11) {
      setSeason("christmas");
      headerImg = "/images/santa_hat.png";
    } else if (currentMonth === 9) {
      setSeason("halloween");
      headerImg = "/images/spooky_ghost.png";
    } else {
      setSeason("");
      headerImg = "";
    }
  }

  const currentYear = new Date().getFullYear();
</script>

<div id="body" class={season}>
  <header>
    <div class="title-section">
      <img id="header-img1" src={headerImg} alt="Header Img 1" />
      <h1>Coding Is Fun!</h1>
      <img id="header-img2" src={headerImg} alt="Header Img 2" />
    </div>
    <nav>
      <ul>
        <li><a href="/">Home</a></li>
        <li><a href="/">Codecademy</a></li>
        <li><a href="/">NavSite</a></li>
        <li><a href="/">NavSite</a></li>
      </ul>
    </nav>
  </header>

  <main class="rest-of-body">
    <slot></slot>
  </main>

  <footer>
    <p id="copyright">Skye Danler {currentYear} &copy;</p>
  </footer>
</div>

<style>
  /*Themes*/
  .halloween {
    --primary-color: black;
    --secondary-color: orange;
    --header-color: black;
    --font-color: yellow;
    --nav-font-color: orange;
    font-family: "Eater", serif;
  }

  .christmas {
    --primary-color: green;
    --secondary-color: white;
    --header-color: red;
    --font-color: white;
    --nav-font-color: white;
    font-family: "Mountains of Christmas", serif;
  }

  #body {
    background-color: var(--primary-color);
    margin: 0;
    padding: 0;
    color: var(--font-color);
  }

  .title-section {
    display: flex;
    align-items: center;
    justify-content: center;
  }

  /*Header*/
  header {
    background-color: var(--secondary-color);
    display: grid;
    grid-template-areas: "header" "nav";
  }

  header h1 {
    text-align: center;
    font-size: 3.5rem;
    padding-top: 20px;
    grid-area: header;
    color: var(--header-color);
  }

  header img {
    width: 100px;
    height: auto;
    margin: 0 20px;
  }

  nav {
    grid-area: nav;
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
  }

  nav ul {
    display: flex;
    list-style-type: none;
    margin: 0;
  }

  nav li {
    box-sizing: border-box;
    border-radius: 10px 10px 0px 0px;
    background-color: var(--primary-color);
    padding: 10px;
    margin: 0 5px;
    width: 200px;
    text-align: center;
  }

  nav li:hover {
    transform: scale(1.2);
    font-size: 1.5rem;
  }

  nav li:active {
    font-weight: 700;
    color: var(--nav-font-color);
  }

  nav a {
    text-decoration: none;
    color: var(--nav-font-color);
  }

  nav a:visited {
    color: var(--nav-font-color);
  }

  footer {
    background-color: var(--secondary-color);
    display: flex;
    justify-content: right;
    position: absolute;
    bottom: 0;
    width: 100%;
  }

  #copyright {
    color: var(--primary-color);
    margin-right: 20px;
  }
</style>
