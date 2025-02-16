<!DOCTYPE html>
<html>
    <head>
        <script src="//js.jotform.com/JotFormCustomWidget.min.js"></script>
        <style>
        body {
            font-family: Arial, sans-serif;
            padding: 20px;
        }
        #searchContainer {
            position: relative;
            width: 300px;
        }
        #searchInput {
            width: 100%;
            padding: 8px;
            box-sizing: border-box;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        #suggestions {
            position: absolute;
            width: 100%;
            background: white;
            border: 1px solid #ccc;
            max-height: 150px;
            overflow-y: auto;
            display: none;
            border-radius: 5px;
            box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1);
        }
        .suggestion-item {
            padding: 8px;
            cursor: pointer;
            border-bottom: 1px solid #eee;
        }
        .suggestion-item:last-child {
            border-bottom: none;
        }
        .suggestion-item:hover {
            background: #f0f0f0;
        }
        .highlight {
            font-weight: bold;
            color: black; /* Cambiado a negro */
        }
    </style>
</head>
<body>

    <h2>Buscador Dinámico</h2>
    <div id="searchContainer">
        <input type="text" id="searchInput" placeholder="Buscar...">
        <div id="suggestions"></div>
    </div>

    <script>
        const searchInput = document.getElementById("searchInput");
        const suggestionsBox = document.getElementById("suggestions");

        // Lista de opciones para buscar
        const options = [
            "Manzana", "Banana", "Cereza", "Dátil", "Uva", "Limón", "Mango", "Naranja",
            "Piña", "Fresa", "Pera", "Melón", "Sandía", "Ciruela", "Papaya",
            "Automóvil", "Avión", "Barco", "Tren", "Helicóptero", "Bicicleta", "Motocicleta"
        ];

        searchInput.addEventListener("input", function() {
            let query = searchInput.value.toLowerCase().trim();
            suggestionsBox.innerHTML = "";

            if (query.length === 0) {
                suggestionsBox.style.display = "none";
                return;
            }

            // Filtrar opciones que contengan la consulta
            let filteredOptions = options.filter(item => item.toLowerCase().includes(query));

            if (filteredOptions.length > 0) {
                suggestionsBox.style.display = "block";
                filteredOptions.forEach(item => {
                    let div = document.createElement("div");
                    div.innerHTML = highlightMatch(item, query);
                    div.classList.add("suggestion-item");
                    div.onclick = function() {
                        searchInput.value = item;
                        suggestionsBox.style.display = "none";
                    };
                    suggestionsBox.appendChild(div);
                });
            } else {
                suggestionsBox.style.display = "none";
            }
        });

        // Función para resaltar coincidencias en negrita y negro
        function highlightMatch(text, query) {
            let regex = new RegExp(`(${query})`, "gi");
            return text.replace(regex, "<span class='highlight'>$1</span>");
        }

        // Cerrar el cuadro de sugerencias si se hace clic fuera
        document.addEventListener("click", function(event) {
            if (!searchInput.contains(event.target)) {
                suggestionsBox.style.display = "none";
            }
        });
    </script>

</body>
</html>
