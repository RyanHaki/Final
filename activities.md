<body>
<div class="main-container">

  <div id="search_page">
      <h1>What would you like to cook?</h1>
      <div>
          <input id="searchBar" type="text" placeholder="Type here">
          <button id="searchButton">Search</button>
      </div>
      <br>
      <div id="results">

      </div>
  </div>
  <div id="instructions">
      <button onclick="return_to_search();">Return To Search</button>
      <h1>Instructions</h1>
      <br>
      <b>You will need: </b>
      <p id="youWillNeed"></p>
      <br>
      <b>Method: </b>
      <p id="method"></p>
  </div>
</div>
</body>
<script>
  var logged_in = false;
  var recipies = {};
function return_to_search() {
      document.getElementById("search_page").style["display"] = "flex";
      document.getElementById("instructions").style.display = "none";
  };
function open_instructions(object) {
      var instructions = recipies[object];
      document.getElementById("search_page").style["display"] = "none";
      document.getElementById("instructions").style.display = "flex";
      document.getElementById("youWillNeed").innerHTML = instructions[1];
      document.getElementById("method").innerHTML = instructions[0];
  };
function favourite_recipe() {
      if (!logged_in) {
          alert("You must be logged in!")
      } else {
};
  }
 document.getElementById("searchButton").addEventListener("click", () => {
      document.getElementById("results").style.overflow = "hidden";
      document.getElementById("results").innerHTML = `<div class="lds-roller"><div></div><div></div><div></div><div></div><div></div><div></div><div></div><div></div></div>`;
      var content = document.getElementById("searchBar").value;
      fetch("https://fruitteam.duckdns.org/api/search/", {
          "method": "POST",
          "headers": {
              "content-type": "application/json"
          },
          "body": JSON.stringify({
              "item": content
          })
      }).then(Response => {
          document.getElementById("results").style.overflow = "auto";
          recipies = {};
          Response.json().then(Data => {
              if (Data.length > 0) {
                  var html = ``;
                  Data.forEach((v) => {
                      var instruction_id = new Date().getTime().toString() + "_" + Math.random().toString();
                      recipies[instruction_id] = [v.instructions, v.ingredients, v.title]
                      html = html + `
                          <div class="result">
                              <b>${v.title}</b>
                              <p>${v.ingredients.replaceAll("|", "\n")}</p>
                              <button onclick="open_instructions('${instruction_id}')">View Instructions</button>
                              <button onclick="favourite_recipe('${instruction_id}');" id="favouriteButton"><svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-star-fill" viewBox="0 0 16 16">
                              <path d="M3.612 15.443c-.386.198-.824-.149-.746-.592l.83-4.73L.173 6.765c-.329-.314-.158-.888.283-.95l4.898-.696L7.538.792c.197-.39.73-.39.927 0l2.184 4.327 4.898.696c.441.062.612.636.282.95l-3.522 3.356.83 4.73c.078.443-.36.79-.746.592L8 13.187l-4.389 2.256z"/>
                              </svg> Favourite</button>
                          </div>
                      `
                  });
                  document.getElementById("results").innerHTML = html;
              } else {
                  document.getElementById("results").innerHTML = "We found no items for this query!";
              }
          }).catch(E => {
              document.getElementById("results").innerHTML = "We found no items for this query!";
          })
      }).catch(E => {
          document.getElementById("results").innerHTML = "We found no items for this query!";
      })
  })
</script>