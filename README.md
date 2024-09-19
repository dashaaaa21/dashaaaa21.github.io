<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Julian's portfolio showcasing wall paintings and murals.">
    <meta name="keywords" content="portfolio, paintings, murals, Julian">
    <meta name="author" content="Julian">
    <title>Mijn Portfolio</title>
    <style>
        /* CSS styles unchanged */
    </style>
</head>
<body>
    <header>
        <h1>KOOT</h1>
        <nav>
            <a href="#over" aria-label="Over section">Over</a>
            <a href="#portfolio" aria-label="Portfolio section">Portfolio</a>
            <a href="#contact" aria-label="Contact section">Contact</a>
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
            <!-- Image gallery with descriptive alt attributes -->
            <a href="#lightbox1" aria-label="View larger image of Example Picture 1"><img src="walls/1.jpg" alt="Colorful mural with abstract design"></a>
            <!-- More images here -->
        </div>
    </div>

    <!-- Lightbox -->
    <!-- Example lightbox -->
    <div id="lightbox1" class="lightbox" aria-labelledby="lightbox1-label" aria-hidden="true">
        <a href="#" class="lightbox-close" aria-label="Close lightbox">&times;</a>
        <img src="walls/1.jpg" alt="Colorful mural with abstract design">
    </div>
    <!-- More lightboxes here -->

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
                document.querySelector(target).setAttribute('aria-hidden', 'false');
            });
        });

        document.querySelectorAll('.lightbox-close').forEach(close => {
            close.addEventListener('click', function(event) {
                event.preventDefault();
                this.parentElement.classList.remove('show');
                this.parentElement.setAttribute('aria-hidden', 'true');
            });
        });

        window.addEventListener('click', function(event) {
            if (event.target.classList.contains('lightbox')) {
                event.target.classList.remove('show');
                event.target.setAttribute('aria-hidden', 'true');
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
