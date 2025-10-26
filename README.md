







<!DOCTYPE html>
<html lang="hi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ImarGamingPC</title>
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@500&display=swap" rel="stylesheet">
    <style>
        body {
            margin: 0;
            font-family: 'Orbitron', sans-serif;
            background-color: #0b0c10;
            color: #c5c6c7;
        }
        header {
            background: linear-gradient(90deg, #ff4500, #ff8c00);
            padding: 30px;
            text-align: center;
            color: #fff;
            animation: fadeIn 2s ease-in;
        }
        header h1 {
            font-size: 3em;
            margin: 0;
            text-shadow: 2px 2px 8px #000;
        }
        nav {
            background-color: #1f2833;
            display: flex;
            justify-content: center;
            gap: 25px;
            padding: 15px 0;
            position: sticky;
            top: 0;
            z-index: 1000;
        }
        nav a {
            color: #66fcf1;
            text-decoration: none;
            font-weight: bold;
            transition: 0.3s;
        }
        nav a:hover {
            color: #ff4500;
            transform: scale(1.1);
        }
        section {
            max-width: 1000px;
            margin: auto;
            padding: 40px 20px;
        }
        h2 {
            color: #ff4500;
            text-align: center;
            margin-bottom: 25px;
        }
        footer {
            background-color: #1f2833;
            text-align: center;
            padding: 20px;
            color: #66fcf1;
            margin-top: 20px;
        }
        .upload-box {
            background-color: #1f2833;
            padding: 30px;
            border-radius: 10px;
            text-align: center;
            box-shadow: 0 0 10px #ff4500;
        }
        input[type="file"] {
            background: #0b0c10;
            color: #66fcf1;
            border: 2px solid #ff4500;
            padding: 10px;
            border-radius: 5px;
            margin-top: 15px;
        }
        button {
            background-color: #ff4500;
            color: white;
            border: none;
            padding: 10px 20px;
            margin-top: 15px;
            border-radius: 5px;
            font-weight: bold;
            cursor: pointer;
            transition: 0.3s;
        }
        button:hover {
            background-color: #ff8c00;
            transform: scale(1.05);
        }
        #uploadStatus {
            margin-top: 15px;
            font-weight: bold;
        }
    </style>
</head>
<body>

    <header>
        <h1>ImarGamingPC</h1>
        <p>आपकी गेमिंग दुनिया, वीडियो और टिप्स का घर</p>
    </header>

    <nav>
        <a href="#home">होम</a>
        <a href="#videos">वीडियो</a>
        <a href="#upload">अपलोड</a>
        <a href="#blog">ब्लॉग</a>
        <a href="#contact">संपर्क</a>
    </nav>

    <section id="home">
        <h2>स्वागत है ImarGamingPC में!</h2>
        <p style="text-align:center;">यहाँ आपको गेमिंग, यूट्यूब वीडियो, और गेमिंग टिप्स की पूरी दुनिया मिलेगी।</p>
    </section>

    <section id="upload">
        <h2>🎥 अपना वीडियो अपलोड करें</h2>
        <div class="upload-box">
            <form id="uploadForm">
                <input type="file" name="video" accept="video/*" required>
                <br>
                <button type="submit">वीडियो अपलोड करें</button>
            </form>
            <div id="uploadStatus"></div>
        </div>
    </section>

    <section id="videos">
        <h2>हमारे वीडियो</h2>
        <div class="video-grid">
            <iframe src="https://www.youtube.com/embed/example_video_id" title="YouTube video" frameborder="0" allowfullscreen></iframe>
        </div>
    </section>

    <section id="contact">
        <h2>संपर्क करें</h2>
        <p>ईमेल: info@imargamingpc.com</p>
        <p>इंस्टाग्राम: <a href="https://instagram.com/imargamingpc" target="_blank">@imargamingpc</a></p>
    </section>

    <footer>
        &copy; 2025 ImarGamingPC. सभी अधिकार सुरक्षित।
    </footer>

    <script>
        // JavaScript to send video to Node.js server
        const uploadForm = document.getElementById("uploadForm");
        const status = document.getElementById("uploadStatus");

        uploadForm.addEventListener("submit", async (e) => {
            e.preventDefault();
            const fileInput = uploadForm.querySelector('input[type="file"]');
            const file = fileInput.files[0];
            if (!file) return alert("कृपया एक वीडियो चुनें!");

            const formData = new FormData();
            formData.append("video", file);

            status.innerHTML = "⏳ अपलोड हो रहा है...";

            try {
                const response = await fetch("http://localhost:3000/upload", {
                    method: "POST",
                    body: formData
                });

                const result = await response.text();
                status.innerHTML = "✅ " + result;
            } catch (err) {
                status.innerHTML = "❌ अपलोड असफल रहा!";
            }
        });
    </script>

</body>
</html>
