<!DOCTYPE html>
<html>
<head>
  <title>Pizzata giovedì</title>
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <style>
    * {
      box-sizing: border-box;
    }

    body {
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 20px;
    }

    h1 {
      text-align: center;
    }

    form {
      margin-bottom: 20px;
    }

    input[type="text"] {
      width: 100%;
      padding: 10px;
      margin-bottom: 10px;
    }

    .button-wrapper {
      display: flex;
      justify-content: space-between;
    }

    .add-button {
      width: 30px;
      height: 30px;
      background-color: #4CAF50;
      color: #fff;
      border: none;
      border-radius: 50%;
      cursor: pointer;
      display: flex;
      align-items: center;
      justify-content: center;
    }
  </style>
</head>
<body>
  <h1>Inviami quello che vuoi!!!</h1>

  <form onsubmit="return false;">
    <div id="boxWrapper">
      <input type="text" placeholder="cosa ti spila?" id="input1" />
    </div>
    <div class="button-wrapper">
      <button class="add-button" onclick="aggiungiBox()">+</button>
      <button onclick="confermaInvio()">Invia su WhatsApp</button>
    </div>
  </form>

  <script>
    function inviaListaWhatsApp() {
      var valori = [];
      var inputCount = document.getElementById("boxWrapper").getElementsByTagName("input").length;

      for (var i = 1; i <= inputCount; i++) {
        var inputId = "input" + i;
        var input = document.getElementById(inputId);
        valori.push(input.value);
      }

      var messaggio = "Per giovedì voglio :\n" + valori.join("\n");
      var numeroTelefono = "3756046392";

      var url = "https://wa.me/" + numeroTelefono + "?text=" + encodeURIComponent(messaggio);

      if (confirm("Sei sicuro/a di voler inviare?")) {
        if (confirm("Sei veramente sicuro/a?")) {
          if (confirm("Sicuro/a sicuro/a?")) {
            var link = document.createElement("a");
            link.href = url;
            link.target = "_blank";
            link.click();
          }
        }
      }
    }

    function confermaInvio() {
      if (confirm("E se poi te ne penti, vuoi inviare?")) {
        inviaListaWhatsApp();
      }
    }

    function aggiungiBox() {
      var boxWrapper = document.getElementById("boxWrapper");
      var inputCount = boxWrapper.getElementsByTagName("input").length;

      if (inputCount < 7) {
        var newInput = document.createElement("input");
        newInput.type = "text";
        newInput.placeholder = "Inserisci qui";
        newInput.id = "input" + (inputCount + 1);

        boxWrapper.appendChild(newInput);
      } else {
        alert("Hai raggiunto il limite massimo di box di testo (7).");
      }
    }
  </script>
</body>
</html>
