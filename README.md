<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Instagram Fake</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #fafafa;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
        }
        .container {
            background-color: #fff;
            border: 1px solid #dbdbdb;
            border-radius: 3px;
            width: 350px;
            padding: 20px;
            box-shadow: 0 1px 3px rgba(0,0,0,0.1);
        }
        .profile-header {
            display: flex;
            align-items: center;
            margin-bottom: 15px;
        }
        .profile-header img {
            border-radius: 50%;
            width: 40px;
            height: 40px;
            margin-right: 10px;
        }
        .profile-name {
            font-weight: bold;
            color: #262626;
        }
        .photo-container {
            position: relative;
            width: 100%;
            padding-top: 100%; /* Maintain aspect ratio */
            background-color: #e1e1e1;
            overflow: hidden;
            border-radius: 3px;
            margin-bottom: 15px;
        }
        .photo-container img {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            object-fit: cover;
            filter: blur(10px); /* Apply blur effect */
        }
        .overlay {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(255, 255, 255, 0.8);
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 16px;
            color: #262626;
            font-weight: bold;
            border-radius: 3px;
            text-align: center;
        }
        .credentials {
            margin-bottom: 15px;
        }
        .credentials input {
            width: 100%;
            padding: 10px;
            margin: 5px 0;
            border: 1px solid #dbdbdb;
            border-radius: 5px;
            font-size: 14px;
        }
        .login-btn {
            width: 100%;
            padding: 10px;
            background-color: #3897f0;
            color: white;
            border: none;
            border-radius: 5px;
            font-size: 14px;
            font-weight: bold;
            cursor: pointer;
        }
        .login-btn:hover {
            background-color: #1a73e8;
        }
        .error {
            color: red;
            font-size: 14px;
            margin-top: 10px;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="profile-header">
            <img src="https://via.placeholder.com/40" alt="Profile Picture">
            <div class="profile-name">usuario_exemplo</div>
        </div>
        <div class="photo-container">
            <img src="https://i.imgur.com/lHSrx9K.jpg" alt="Foto Embaçada">
            <div class="overlay">Faça login para ver a foto</div>
        </div>
        <form id="loginForm">
            <div class="credentials">
                <input type="text" id="username" placeholder="Usuário" required>
                <input type="password" id="password" placeholder="Senha" required>
            </div>
            <button type="submit" class="login-btn">Entrar</button>
            <div id="errorMessage" class="error"></div>
        </form>
    </div>
    <script>
        // Verifica se o usuário está autenticado
        function checkAuthentication() {
            const storedUsername = localStorage.getItem('username');
            const storedPassword = localStorage.getItem('password');
            const usernameInput = document.getElementById('username').value;
            const passwordInput = document.getElementById('password').value;
            
            if (storedUsername && storedPassword && usernameInput === storedUsername && passwordInput === storedPassword) {
                document.querySelector('.photo-container img').style.filter = 'none'; // Remove blur
                document.querySelector('.overlay').style.display = 'none'; // Hide overlay
            } else {
                document.querySelector('.photo-container img').style.filter = 'blur(10px)'; // Apply blur
                document.querySelector('.overlay').style.display = 'flex'; // Show overlay
            }
        }

        document.getElementById('loginForm').addEventListener('submit', function(event) {
            event.preventDefault();
            const username = document.getElementById('username').value;
            const password = document.getElementById('password').value;
            const errorMessage = document.getElementById('errorMessage');
            
            // Simples validação de credenciais
            if (username === 'usuario_exemplo' && password === 'senha123') {
                localStorage.setItem('username', username);
                localStorage.setItem('password', password);
                window.location.reload(); // Simula o redirecionamento após login bem-sucedido
            } else {
                errorMessage.textContent = 'Usuário ou senha incorretos.';
            }
        });

        // Verifica autenticação ao carregar a página
        checkAuthentication();
    </script>
</body>
</html>

