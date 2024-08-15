<html lang="ru">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Отправка сообщения через Green API</title>
    <link
      href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css"
      rel="stylesheet"
      integrity="sha384-QWTKZyjpPEjISv5WaRU9OFeRpok6YctnYmDr5pNlyT2bRjXh0JMhjY6hW+ALEwIH"
      crossorigin="anonymous"
    />
    <script
      src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"
      integrity="sha384-YvpcrYf0tY3lHB60NNkmXc5s9fDVZLESaAA55NDzOxhy9GkcIdslK1eN7N6jIeHz"
      crossorigin="anonymous"
    ></script>
    <style>
      pre {
        display: block;
        margin: 0 auto;
        width: 50%;
        border: 5px solid #ba2121;
        padding: 10px;
      }
      body {
        text-align: left;
        margin-left: 5%;
      }
      .content {
        text-align: left;
        margin-top: 10%;
      }
      .content3 {
        text-align: left;
        margin-top: 5%;
      }
    </style>
  </head>
  <body>
    <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
      <div class="container-fluid">
        <a class="navbar-brand" href="http://127.0.0.1:5500/GreenApi.html"
          >Главная страница</a
        >
        <button
          class="navbar-toggler"
          type="button"
          data-bs-toggle="collapse"
          data-bs-target="#navbarNavDarkDropdown"
          aria-controls="navbarNavDarkDropdown"
          aria-expanded="false"
          aria-label="Toggle navigation"
        >
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarNavDarkDropdown">
          <ul class="navbar-nav">
            <li class="nav-item dropdown">
              <button
                class="btn btn-dark dropdown-toggle"
                data-bs-toggle="dropdown"
                aria-expanded="false"
              >
                Открой меня
              </button>
              <ul class="dropdown-menu dropdown-menu-dark">
                <li>
                  <a
                    class="dropdown-item"
                    href="https://1103.api.green-api.com/waInstance1103101910/getSettings/543574faf1c34c698deff269a4616c80f4dd38e3a5a942b2b2"
                    >getSettings</a
                  >
                </li>
                <li>
                  <a
                    class="dropdown-item"
                    href="https://1103.api.green-api.com/waInstance1103101910/getStateInstance/543574faf1c34c698deff269a4616c80f4dd38e3a5a942b2b2"
                    >getStateInstance</a
                  >
                </li>
              </ul>
            </li>
          </ul>
        </div>
      </div>
    </nav>
    <div class="content">
      <button id="sendMessageButton">sendMessage</button>
      <script>
        document
          .getElementById("sendMessageButton")
          .addEventListener("click", function () {
            const url =
              "https://1103.api.green-api.com/waInstance1103101910/sendMessage/543574faf1c34c698deff269a4616c80f4dd38e3a5a942b2b2";
            const payload = { chatId: "89786743599@c.us", message: "dsadsa" };
            fetch(url, {
              method: "POST",
              headers: { "Content-Type": "application/json" },
              body: JSON.stringify(payload),
            })
              .then((response) => response.json())
              .then((data) => {
                document.getElementById("responseOutput").textContent =
                  JSON.stringify(data, null, 2);
              })
              .catch((error) => {
                document.getElementById("responseOutput").textContent =
                  "Ошибка: " + error;
              });
          });
      </script>
    </div>
    <div class="content3">
      <button id="sendURLfile">Send URL File</button>
      <script>
        document
          .getElementById("sendURLfile")
          .addEventListener("click", function () {
            const url =
              "https://1103.api.green-api.com/waInstance1103101910/sendFileByUrl/543574faf1c34c698deff269a4616c80f4dd38e3a5a942b2b2";
            const payload = {
              chatId: "89786743599@c.us",
              urlFile:
                "https://avatars.mds.yandex.net/get-entity_search/1870652/850969426/S600xU_2x",
              fileName: "test.jpg",
            };
            fetch(url, {
              method: "POST",
              headers: { "Content-Type": "application/json" },
              body: JSON.stringify(payload),
            })
              .then((response) => response.json())
              .then((data) => {
                document.getElementById("responseOutput").textContent =
                  JSON.stringify(data, null, 2);
              })
              .catch((error) => {
                document.getElementById("responseOutput").textContent =
                  "Ошибка: " + error;
              });
          });
      </script>
    </div>
    <br /><br />
    <pre id="responseOutput"> &lt;&gt;</pre>
</html>
