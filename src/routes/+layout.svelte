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
    } else if (currentMonth == 10) {
      setSeason("thanksgiving");
      headerImg = "/images/thanksgiving.png";
    } else {
      setSeason("");
      headerImg = "";
    }
  }

  const currentYear = new Date().getFullYear();
</script>

<div id="body" class={season}>
  <div id="page-container">
    <div id="content-wrap">
      <header>
        <div class="title-section">
          <img id="header-img1" src={headerImg} alt="Header Img 1" />
          <h1>Coding Is Fun!</h1>
          <img id="header-img2" src={headerImg} alt="Header Img 2" />
        </div>
        <nav>
          <ul>
            <li><a href="/">Home</a></li>
            <li><a href="/codecademy">Codecademy</a></li>
            <li><a href="/blog">Blog</a></li>
          </ul>
        </nav>
      </header>

      <main class="rest-of-body">
        <slot></slot>
      </main>
    </div>
    <footer>
      <p id="copyright">Skye Danler {currentYear} &copy;</p>
    </footer>
  </div>
</div>

<style>
  /*Themes*/
  .halloween {
    --primary-color: black;
    --secondary-color: orange;
    --header-color: black;
    --font-color: rgb(177, 46, 177);
    --header-font: "Eater", serif;
  }

  .thanksgiving {
    --primary-color: rgb(92, 76, 76);
    --secondary-color: rgba(248, 245, 41, 0.911);
    --header-color: rgb(92, 76, 76);
    --font-color: rgb(216, 154, 38);
    --header-font: "Playwrite GB S", serif;
  }

  .christmas {
    --primary-color: rgb(10, 173, 10);
    --secondary-color: rgb(172, 26, 26);
    --header-color: white;
    --font-color: white;
    --header-font: "Mountains of Christmas", serif;
    font-size: 1.25em;
  }

  #body {
    background-color: var(--primary-color);
    margin: 0;
    padding: 0;
    color: var(--font-color);
    min-height: 100vh;
    margin-bottom: 50px;
  }

  .title-section {
    display: flex;
    align-items: center;
    justify-content: center;
  }

  header,
  footer {
    background-color: var(--secondary-color);
    font-family: var(--header-font);
  }

  .rest-of-body {
    margin: 40px;
    /*font-family: "Times New Roman", serif;*/
    font-family: var(--header-font);
    line-height: 2;
  }

  /*Header*/
  header {
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

  #header-img2 {
    -webkit-transform: scaleX(-1);
    transform: scaleX(-1);
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
    color: var(--secondary-color);
  }

  nav a {
    text-decoration: none;
    color: var(--secondary-color);
  }

  nav a:visited {
    color: var(--secondary-color);
  }

  /*adjust footer*/
  #page-container {
    position: relative;
    min-height: 100vh;
  }

  #content-wrap {
    padding-bottom: 4rem;
  }

  footer {
    position: absolute;
    display: flex;
    justify-content: right;
    bottom: 0;
    width: 100%;
    height: 4rem;
  }

  #copyright {
    color: var(--header-color);
    margin-right: 20px;
  }
</style>
