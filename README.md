<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mijn Portfolio</title>
    <style>
        /* Ваші стилі */
    </style>
</head>
<body>
    <header>
        <h1>KOOT</h1>
        <nav>
            <a href="#over">Over</a>
            <a href="#portfolio">Portfolio</a>
            <a href="#contact">Contact</a>
        </nav>
    </header>
    
    <div class="hero">
        <h2>Hoi, ik ben Julian</h2>
        <p>Ik ben een schilder. Bekijk mijn werk hieronder.</p>
    </div>

    <div id="over" class="section">
        <h2>Over</h2>
        <p>Ik ben een professionele muurschilder...</p>
    </div>

    <div id="portfolio" class="section">
        <h2>Portfolio</h2>
        <p>Hier zijn enkele van mijn recente werken en projecten.</p>
        <div class="gallery-images">
            <a href="#lightbox1"><img src="https://raw.githubusercontent.com/dashaaaa21/dashaaaa21.github.io/main/images/1.jpg" alt="Example Picture 1"></a>
            <a href="#lightbox2"><img src="https://raw.githubusercontent.com/dashaaaa21/dashaaaa21.github.io/main/images/2.jpg" alt="Example Picture 2"></a>
            <!-- Додайте інші зображення так само -->
        </div>
    </div>

    <!-- Lightbox -->
    <div id="lightbox1" class="lightbox">
        <a href="#" class="lightbox-close">&times;</a>
        <img src="https://raw.githubusercontent.com/dashaaaa21/dashaaaa21.github.io/main/images/1.jpg" alt="Example Picture 1">
    </div>
    <!-- Додайте інші lightbox так само -->

    <div id="contact" class="section">
        <h2>Contact</h2>
        <div class="contact-info">
            <p>+3123456789</p>
            <p>koot@gmail.com</p>
        </div>
    </div>

    <footer>
        <p>&copy; 2024 KOOT. All rights reserved.</p>
    </footer>

    <script>
        // Ваш JavaScript
    </script>
</body>
</html>
