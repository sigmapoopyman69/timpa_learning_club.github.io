<html>
    <head>
        <style>
            body, html {
                margin: 0;
                padding: 0;
                height: 100%;
                overflow: hidden;
                background-color: #000;
            }
            #game-container {
                width: 100%;
                height: 100%;
            }
            #fullscreen-btn {
                position: absolute;
                bottom: 10px;
                right: 10px;
                z-index: 999;
                padding: 10px 15px;
                background-color: #0064ff;
                color: white;
                border: none;
                border-radius: 5px;
                cursor: pointer;
                font-family: Arial, sans-serif;
                font-weight: bold;
                opacity: 0.8;
            }
            #fullscreen-btn:hover {
                opacity: 1;
            }
        </style>
    </head>
    <body>
        <button id="fullscreen-btn" onclick="openFullscreen()">Play Fullscreen</button>
        <div id="game-container">
            <div id="game"></div>
        </div>

        <script>
            // Configuration shared by both the embed and the fullscreen tab
            const config = `
                EJS_player = "#game";
                EJS_core = "n64";
                EJS_gameName = "MarioKart64";
                EJS_color = "#0064ff";
                EJS_startOnLoaded = true;
                EJS_pathtodata = "https://cdn.emulatorjs.org/stable/data/";
                EJS_gameUrl = "Mario Kart 64 (USA).z64";
            `;

            // Initialize the game in the current small window
            eval(config);

            function openFullscreen() {
                const gameHtml = `
                    <html>
                        <head>
                            <title>Mario Kart 64 - Fullscreen</title>
                            <style>
                                body, html { margin: 0; padding: 0; width: 100%; height: 100%; overflow: hidden; background: #000; }
                                #game { width: 100vw; height: 100vh; }
                            </style>
                        </head>
                        <body>
                            <div id="game"></div>
                            <scr` + `ipt>
                                ${config}
                            </scr` + `ipt>
                            <scr` + `ipt src="https://cdn.emulatorjs.org/stable/data/loader.js"></scr` + `ipt>
                        </body>
                    </html>
                `;

                const win = window.open("about:blank", "_blank");
                win.document.write(gameHtml);
                win.document.close();
            }
        </script>
        <script src="https://cdn.emulatorjs.org/stable/data/loader.js"></script>
    </body>
</html>
