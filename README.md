<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mijn Portfolio</title>
    <style>
        body {
            margin: 0;
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Montserrat, sans-serif;
            color: #333;
            background-color: #f4f4f4;
            overflow-x: hidden;
        }
        header {
            background: #333;
            color: #fff;
            padding: 20px;
            position: sticky;
            top: 0;
            z-index: 1000;
            text-align: center;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
            transition: background-color 0.3s ease;
        }
        header.scrolled {
            background-color: #444;
        }
        header h1 {
            margin: 0;
            font-size: 2.5em;
            transition: transform 0.3s ease;
        }
        nav {
            margin-top: 10px;
        }
        nav a {
            color: #fff;
            text-decoration: none;
            margin: 0 15px;
            font-size: 1.2em;
            position: relative;
            display: inline-block;
            transition: color 0.3s ease;
        }
        nav a::after {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 50%;
            transform: translateX(-50%);
            width: 0;
            height: 2px;
            background: #fff;
            transition: width 0.3s ease;
        }
        nav a:hover::after {
            width: 100%;
        }
        .hero {
            position: relative;
            height: 100vh;
            background: url('walls/7.jpg') no-repeat center center/cover;
            color: #fff;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
            opacity: 0.8;
            transition: opacity 0.5s ease;
        }
        .hero:hover {
            opacity: 1;
        }
        .hero h2 {
            font-size: 4em;
            margin: 0;
            animation: fadeInUp 2s ease-out;
            transform: translateY(-50px);
            transition: transform 0.5s ease;
        }
        .hero p {
            font-size: 1.5em;
            margin-top: 20px;
            animation: fadeInUp 2s 0.5s ease-out;
            transform: translateY(20px);
            transition: transform 0.5s ease;
        }
        .hero:hover h2, .hero:hover p {
            transform: translateY(0);
        }
        .section {
            padding: 50px 20px;
            text-align: center;
            position: relative;
            overflow: hidden;
        }
        .section h2 {
            font-size: 3em;
            color: #007BFF;
            margin-bottom: 20px;
            opacity: 0;
            transform: translateY(-50px);
            animation: fadeInUp 2s ease-out forwards;
        }
        .section p {
            font-size: 1.2em;
            margin-bottom: 30px;
            opacity: 0;
            transform: translateY(20px);
            animation: fadeInUp 2s 0.5s ease-out forwards;
        }
        .gallery-images {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 15px;
            margin: 0 auto;
            padding: 20px;
        }
        .gallery-images a {
            display: inline-block;
        }
        .gallery-images img {
            width: 300px;
            height: 200px;
            object-fit: cover;
            border-radius: 10px;
            transition: transform 0.5s ease, box-shadow 0.5s ease, opacity 0.5s ease;
            opacity: 0.8;
            cursor: pointer;
        }
        .gallery-images img:hover {
            transform: scale(1.1);
            box-shadow: 0 8px 16px rgba(0, 0, 0, 0.4);
            opacity: 1;
        }
        /* Lightbox styles */
        .lightbox {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.9);
            justify-content: center;
            align-items: center;
            z-index: 1000;
            opacity: 0;
            transition: opacity 0.3s ease;
        }
        .lightbox.show {
            display: flex;
            opacity: 1;
        }
        .lightbox img {
            max-width: 90%;
            max-height: 80%;
            animation: zoomIn 0.5s ease;
        }
        .lightbox-close {
            position: absolute;
            top: 20px;
            right: 20px;
            color: #fff;
            font-size: 2em;
            cursor: pointer;
            text-decoration: none;
            transition: color 0.3s ease;
        }
        .lightbox-close:hover {
            color: #007BFF;
        }
        footer {
            background: #333;
            color: #fff;
            padding: 10px;
            text-align: center;
        }
        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(20px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }
        @keyframes zoomIn {
            from {
                transform: scale(0.8);
                opacity: 0;
            }
            to {
                transform: scale(1);
                opacity: 1;
            }
        }
        .contact-info {
            max-width: 600px;
            margin: 0 auto;
            padding: 20px;
            background: #fff;
            border-radius: 10px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            text-align: center;
        }
        .contact-info p {
            font-size: 1.2em;
            margin: 10px 0;
        }
        .contact-info button {
            background: #007BFF;
            color: #fff;
            border: none;
            padding: 10px 20px;
            border-radius: 5px;
            font-size: 1.2em;
            cursor: pointer;
            transition: background 0.3s ease, transform 0.3s ease;
        }
        .contact-info button:hover {
            background: #0056b3;
            transform: scale(1.05);
        }

        /* Responsive Styles */
        @media (max-width: 768px) {
            header h1 {
                font-size: 2em;
            }
            nav a {
                font-size: 1em;
                margin: 0 10px;
            }
            .hero h2 {
                font-size: 2.5em;
            }
            .hero p {
                font-size: 1.2em;
            }
            .section h2 {
                font-size: 2.5em;
            }
            .section p {
                font-size: 1em;
            }
            .gallery-images img {
                width: 100%;
                height: auto;
            }
        }

        @media (max-width: 480px) {
            header h1 {
                font-size: 1.5em;
            }
            nav a {
                font-size: 0.9em;
                margin: 0 5px;
            }
            .hero h2 {
                font-size: 2em;
            }
            .hero p {
                font-size: 1em;
            }
            .section h2 {
                font-size: 2em;
            }
            .section p {
                font-size: 0.9em;
            }
            .contact-info p {
                font-size: 1em;
            }
        }
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
        <p>Ik ben een professionele muurschilder met een passie voor het transformeren van ruimtes. Met elke penseelstreek breng ik kleur en leven op de muren, en verander ik gewone kamers in levendige en uitnodigende omgevingen. Mijn werk omvat zorgvuldige voorbereiding, vakkundige toepassing en oog voor detail, zodat elk project wordt voltooid volgens de hoogste standaard. Ik geniet ervan om te werken met verschillende kleuren, texturen en afwerkingen, en ik ben trots op het creëren van resultaten die de verwachtingen van mijn klanten overtreffen. Of het nu gaat om een woning, een commerciële ruimte of een uniek muurschilderij, ik zet me in voor het leveren van kwaliteitswerk en een prachtig eindresultaat.</p>
    </div>

  <div id="portfolio" class="section">
    <h2>Portfolio</h2>
    <p>Hier zijn enkele van mijn recente werken en projecten.</p>
    <div class="gallery-images">
        <a href="#lightbox1"><img src="images/1.jpg" alt="Example Picture 1"></a>
        <a href="#lightbox2"><img src="images/2.jpg" alt="Example Picture 2"></a>
        <a href="#lightbox3"><img src="images/3.jpg" alt="Example Picture 3"></a>
        <a href="#lightbox4"><img src="images/4.jpg" alt="Example Picture 4"></a>
        <a href="#lightbox5"><img src="images/5.jpg" alt="Example Picture 5"></a>
        <a href="#lightbox6"><img src="images/6.jpg" alt="Example Picture 6"></a>
        <a href="#lightbox7"><img src="images/7.jpg" alt="Example Picture 7"></a>
        <a href="#lightbox8"><img src="images/8.jpg" alt="Example Picture 8"></a>
        <a href="#lightbox9"><img src="images/9.jpg" alt="Example Picture 9"></a>
        <a href="#lightbox10"><img src="images/10.jpg" alt="Example Picture 10"></a>
        <a href="#lightbox11"><img src="images/11.jpg" alt="Example Picture 11"></a>
        <a href="#lightbox12"><img src="images/12.jpg" alt="Example Picture 12"></a>
    </div>
</div>

<!-- Lightbox -->
<div id="lightbox1" class="lightbox">
    <a href="#" class="lightbox-close">&times;</a>
    <img src="images/1.jpg" alt="Example Picture 1">
</div>
<div id="lightbox2" class="lightbox">
    <a href="#" class="lightbox-close">&times;</a>
    <img src="images/2.jpg" alt="Example Picture 2">
</div>
    <div id="lightbox3" class="lightbox">
        <a href="#" class="lightbox-close">&times;</a>
        <img src="images/3.jpg" alt="Example Picture 3">
    </div>
    <div id="lightbox4" class="lightbox">
        <a href="#" class="lightbox-close">&times;</a>
        <img src="images/4.jpg" alt="Example Picture 4">
    </div>
    <div id="lightbox5" class="lightbox">
        <a href="#" class="lightbox-close">&times;</a>
        <img src="images/5.jpg" alt="Example Picture 5">
    </div>
    <div id="lightbox6" class="lightbox">
        <a href="#" class="lightbox-close">&times;</a>
        <img src="images/6.jpg" alt="Example Picture 6">
    </div>
    <div id="lightbox7" class="lightbox">
        <a href="#" class="lightbox-close">&times;</a>
        <img src="images/7.jpg" alt="Example Picture 7">
    </div>
    <div id="lightbox8" class="lightbox">
        <a href="#" class="lightbox-close">&times;</a>
        <img src="images/8.jpg" alt="Example Picture 8">
    </div>
    <div id="lightbox9" class="lightbox">
        <a href="#" class="lightbox-close">&times;</a>
        <img src="images/9.jpg" alt="Example Picture 9">
    </div>
    <div id="lightbox10" class="lightbox">
        <a href="#" class="lightbox-close">&times;</a>
        <img src="images/10.jpg" alt="Example Picture 10">
    </div>
    <div id="lightbox11" class="lightbox">
        <a href="#" class="lightbox-close">&times;</a>
        <img src="images/11.jpg" alt="Example Picture 11">
    </div>
    <div id="lightbox12" class="lightbox">
        <a href="#" class="lightbox-close">&times;</a>
        <img src="images/12.jpg" alt="Example Picture 12">
    </div>

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
        document.addEventListener('scroll', () => {
            const header = document.querySelector('header');
            if (window.scrollY > 50) {
                header.classList.add('scrolled');
            } else {
                header.classList.remove('scrolled');
            }
        });

        document.querySelectorAll('.gallery-images a').forEach(anchor => {
            anchor.addEventListener('click', function(event) {
                event.preventDefault();
                const target = this.getAttribute('href');
                document.querySelector(target).classList.add('show');
            });
        });

        document.querySelectorAll('.lightbox-close').forEach(close => {
            close.addEventListener('click', function(event) {
                event.preventDefault();
                this.parentElement.classList.remove('show');
            });
        });

        window.addEventListener('click', function(event) {
            if (event.target.classList.contains('lightbox')) {
                event.target.classList.remove('show');
            }
        });

        // Smooth scrolling
        document.querySelectorAll('nav a').forEach(anchor => {
            anchor.addEventListener('click', function(event) {
                event.preventDefault();
                const target = document.querySelector(this.getAttribute('href'));
                window.scrollTo({
                    top: target.offsetTop,
                    behavior: 'smooth'
                });
            });
        });
    </script>
</body>
</html>
