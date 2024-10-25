<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Contacto</title>
    <style>
        /* Fondo degradado */
        body {
            font-family: Arial, sans-serif;
            background: linear-gradient(135deg, #89f7fe 0%, #66a6ff 100%);
            display: flex;
            align-items: center;
            justify-content: center;
            height: 100vh;
            margin: 0;
        }

        /* Contenedor principal */
        .container {
            background-color: #fff;
            padding: 30px;
            width: 90%;
            max-width: 500px;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
            text-align: center;
        }

        /* Estilos del formulario */
        h1 {
            color: #333;
            margin-bottom: 20px;
        }

        label {
            display: block;
            text-align: left;
            font-weight: bold;
            margin-bottom: 5px;
            color: #333;
        }

        input, textarea {
            width: 100%;
            padding: 12px;
            margin-bottom: 15px;
            border: 1px solid #ddd;
            border-radius: 5px;
            font-size: 16px;
            box-sizing: border-box;
            transition: border-color 0.3s;
        }

        input:focus, textarea:focus {
            border-color: #66a6ff;
            outline: none;
        }

        /* Estilos del botón */
        button {
            padding: 12px 20px;
            font-size: 16px;
            color: white;
            background-color: #66a6ff;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            width: 100%;
            transition: background-color 0.3s;
        }

        button:hover {
            background-color: #0056b3;
        }

        /* Mensaje de confirmación */
        #confirmation {
            color: green;
            font-weight: bold;
            margin-top: 15px;
            display: none;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Contáctanos</h1>
        <form id="contact-form" onsubmit="sendEmail(event)">
            <label for="name">Nombre:</label>
            <input type="text" id="name" name="name" placeholder="Ingresa tu nombre" required>

            <label for="email">Correo Electrónico:</label>
            <input type="email" id="email" name="email" placeholder="Ingresa tu correo" required>

            <label for="message">Mensaje:</label>
            <textarea id="message" name="message" rows="4" placeholder="Escribe tu mensaje aquí" required></textarea>

            <button type="submit">Enviar Mensaje</button>
        </form>
        <p id="confirmation">¡Mensaje enviado correctamente!</p>
    </div>

    <!-- Script de EmailJS -->
    <script type="text/javascript" src="https://cdn.emailjs.com/dist/email.min.js"></script>
    <script type="text/javascript">
        (function(){
            emailjs.init("TU_USER_ID"); // Reemplaza "TU_USER_ID" con tu User ID de EmailJS
        })();

        function sendEmail(event) {
            event.preventDefault(); // Evita que el formulario recargue la página

            // Obtener los valores del formulario
            const name = document.getElementById("name").value;
            const email = document.getElementById("email").value;
            const message = document.getElementById("message").value;

            // Enviar correo con EmailJS
            emailjs.send("TU_SERVICE_ID", "TU_TEMPLATE_ID", {
                from_name: name,
                from_email: email,
                message: message
            })
            .then(() => {
                document.getElementById("confirmation").style.display = "block";
                document.getElementById("contact-form").reset(); // Limpiar el formulario
            })
            .catch((error) => {
                console.error("Error al enviar el mensaje:", error);
            });
        }
    </script>
</body>
</html>

