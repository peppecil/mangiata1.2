<!DOCTYPE html>
<html>
<head>
  <title>Pizzata gioved</title>
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

    button {
      width: 100%;
      padding: 10px;
      background-color: #4CAF50;
      color: #fff;
      border: none;
      cursor: pointer;
    }
  </style>
</head>
<body>
  <h1>Inviami quello che vuoi</h1>

  <form onsubmit="return false;">
    <input type="text" placeholder="Inserisci qui" id="input1" />
    <input type="text" placeholder="Inserisci qui" id="input2" />
    <input type="text" placeholder="Inserisci qui" id="input3" />
    <input type="text" placeholder="Inserisci qui" id="input4" />
    <input type="text" placeholder="Inserisci qui" id="input5" />
    <input type="text" placeholder="Inserisci qui" id="input6" />
    <input type="text" placeholder="Inserisci qui" id="input7" />
    <button onclick="confermaInvio()">Invia su WhatsApp</button>
  </form>

  <script>
    function inviaListaWhatsApp() {
      var valori = [];

      for (var i = 1; i <= 7; i++) {
        var inputId = "input" + i;
        var input = document.getElementById(inputId);
        valori.push(input.value);
      }

      var messaggio = "Per giovedì voglio:\n" + valori.join("\n");
      var numeroTelefono = "3756046392";

      var url = "https://wa.me/" + numeroTelefono + "?text=" + encodeURIComponent(messaggio);
      window.open(url, "_blank");
    }

    function confermaInvio() {
      if (confirm("E se poi te ne penti, vuoi inviare?")) {
        inviaListaWhatsApp();
      }
    }
  </script>
</body>
</html>
