<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Pizza Menu Flip</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@700&display=swap');
        @import url('https://fonts.googleapis.com/css2?family=Lato:wght@400;700&display=swap');
        @import url('https://fonts.googleapis.com/css2?family=Open+Sans:wght@400;700&display=swap');
        @import url('https://fonts.googleapis.com/css2?family=Raleway:wght@700&display=swap');

        body, html {
            margin: 0;
            padding: 0;
            font-family: 'Lato', sans-serif;
            overflow-x: hidden;
            scroll-behavior: smooth;
            background-color: #f8f9fa;
        }

        header {
            background: transparent;
            color: #fff;
            padding: 20px 0;
            text-align: center;
            position: absolute;
            top: 0;
            width: 100%;
            z-index: 1000;
            opacity: 0;
            transform: translateY(-20px);
            transition: opacity 1s ease-in-out, transform 1s ease-in-out;
        }

        header nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }

        header nav a {
            color: #fff;
            text-decoration: none;
            font-size: 1.2em;
            margin: 0 15px;
            transition: color 0.3s;
        }

        header nav a:hover {
            color: #ff6b6b;
        }

        .hero {
            background: url('background.jpg') no-repeat center center/cover;
            height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            color: #fff;
            text-align: center;
            padding: 0 20px;
            position: relative;
        }

        .hero::before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.5);
            z-index: 0;
        }

        .hero::after {
            content: '';
            position: absolute;
            bottom: 0;
            left: 0;
            width: 100%;
            height: 100px;
            background: linear-gradient(to bottom, rgba(0, 0, 0, 0), rgba(0, 0, 0, 0.8));
            z-index: 1;
        }

        .hero .content {
            z-index: 1;
            opacity: 0;
            transform: translateY(20px);
            transition: opacity 1s ease-in-out 0.5s, transform 1s ease-in-out 0.5s;
        }

        .hero h1 {
            font-family: 'Montserrat', sans-serif;
            font-size: 5em;
            margin: 0 0 20px;
        }

        .hero p {
            font-family: 'Raleway', sans-serif;
            font-size: 2em;
            margin-bottom: 30px;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.7);
        }

        .hero .button {
            background: #ff6b6b;
            color: #fff;
            padding: 15px 30px;
            font-size: 1.5em;
            border: none;
            border-radius: 5px;
            text-decoration: none;
            cursor: pointer;
            transition: background 0.3s, transform 0.3s;
            margin: 10px;
            font-family: 'Montserrat', sans-serif;
        }

        .hero .button:hover {
            background: #e74c3c;
            transform: scale(1.05);
        }

        .section {
            padding: 60px 20px;
            text-align: center;
            opacity: 0;
            transform: translateY(20px);
            transition: opacity 1s ease-in-out 1s, transform 1s ease-in-out 1s;
            background: rgba(255, 255, 255, 0.7); /* Background for sections */
            border-radius: 10px;
            margin: 20px auto;
            max-width: 1200px;
        }

        .section h2 {
            font-family: 'Montserrat', sans-serif;
            font-size: 3em;
            color: #333;
            margin-bottom: 20px;
        }

        .section p {
            font-size: 1.5em;
            color: #666;
            max-width: 800px;
            margin: 0 auto 40px;
        }

        .cards {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 20px;
        }

        .card {
            background: #fff;
            box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
            border-radius: 10px;
            overflow: hidden;
            transition: transform 0.3s;
            width: 300px;
            padding: 20px; /* Added padding */
            display: flex;
            align-items: center;
            justify-content: flex-start;
            gap: 20px;
        }

        .card:hover {
            transform: scale(1.05);
        }

        .card img {
            width: 40px; /* Reduced size for icons */
            height: 40px;
        }

        .card h3 {
            font-family: 'Montserrat', sans-serif;
            font-size: 1.5em; /* Adjusted font size */
            color: #333;
            margin: 0;
        }

        .card p {
            font-size: 1em; /* Adjusted font size */
            color: #666;
            margin: 0;
        }

        .contact {
            background: rgba(0, 0, 0, 0.8);
            color: #fff;
            padding: 60px 20px;
            text-align: center;
            border-radius: 10px;
            max-width: 1200px;
            margin: 20px auto;
        }

        .contact h2 {
            font-family: 'Montserrat', sans-serif;
            font-size: 3em;
            color: #fff;
            margin-bottom: 20px;
        }

        .contact form {
            max-width: 500px;
            margin: 0 auto;
            display: flex;
            flex-direction: column;
            gap: 20px;
        }

        .contact input {
            padding: 15px;
            font-size: 1.2em;
            border: none;
            border-radius: 5px;
            font-family: 'Lato', sans-serif;
        }

        .contact button {
            padding: 15px;
            font-size: 1.5em;
            background: #007bff;
            color: #fff;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            transition: background 0.3s, transform 0.3s;
            font-family: 'Montserrat', sans-serif;
        }

        .contact button:hover {
            background: #0056b3;
            transform: scale(1.05);
        }

        .footer {
            background: #111;
            color: #fff;
            padding: 20px;
            text-align: center;
        }

        .footer p {
            margin: 0;
        }

        .social-media-links {
            display: flex;
            justify-content: center;
            gap: 10px;
            margin-top: 20px;
        }

        .social-media-links a {
            color: #fff;
            font-size: 1.5em;
            text-decoration: none;
            transition: color 0.3s;
        }

        .social-media-links a:hover {
            color: #ff6b6b;
        }

        .circle-follow {
            position: fixed;
            top: 0;
            left: 0;
            width: 40px;
            height: 40px;
            border: 2px solid rgba(255, 255, 255, 0.8);
            border-radius: 50%;
            pointer-events: none;
            transform: translate(-50%, -50%);
            transition: transform 1s ease-out, background-color 1s ease-out;
            z-index: 1001;
            mix-blend-mode: difference;
        }

        .scroll-down {
            position: absolute;
            bottom: 20px;
            left: 50%;
            transform: translateX(-50%);
            color: #fff;
            font-size: 1.5em;
            cursor: pointer;
            animation: bounce 2s infinite;
        }

        @keyframes bounce {
            0%, 20%, 50%, 80%, 100% {
                transform: translateY(0);
            }
            40% {
                transform: translateY(-10px);
            }
            60% {
                transform: translateY(-5px);
            }
        }
    </style>
</head>
<body>
    <header>
        <nav>
            <div class="logo">
                <h1>Pizza Menu Flip</h1>
            </div>
            <div class="nav-links">
                <a href="#services">Services</a>
                <a href="#comparison">Comparison</a>
                <a href="#contact">Contact</a>
            </div>
        </nav>
    </header>

    <div class="hero">
        <div class="content">
            <h1>Pizza Menu Flip</h1>
            <p>Revolutionizing the way you present your pizzas with custom-designed menus.</p>
            <a href="#services" class="button">Explore Our Services</a>
            <a href="#contact" class="button">Contact Us</a>
        </div>
        <div class="scroll-down">&#x25BC;</div>
    </div>

    <div class="section" id="services">
        <h2>Our Services</h2>
        <p>We offer a range of services to help you create the perfect pizza menu for your pizzeria.</p>
        <div class="cards">
            <div class="card">
                <img src="service1.png" alt="Custom Menu Design">
                <div>
                    <h3>Custom Menu Design</h3>
                    <p>We create stunning, custom-designed menus tailored to your pizzeria.</p>
                </div>
            </div>
            <div class="card">
                <img src="service2.png" alt="High-Quality Prints">
                <div>
                    <h3>High-Quality Prints</h3>
                    <p>Our prints are of the highest quality, ensuring your menus look perfect.</p>
                </div>
            </div>
            <div class="card">
                <img src="service3.png" alt="Fast Delivery">
                <div>
                    <h3>Fast Delivery</h3>
                    <p>We deliver your menus quickly and efficiently, right to your door.</p>
                </div>
            </div>
        </div>
    </div>

    <div class="section" id="comparison">
        <h2>Old Menus vs Our Menus</h2>
        <p>Discover the difference between traditional pizza menus and our innovative designs.</p>
        <div class="cards">
            <div class="card">
                <img src="old-menu.jpg" alt="Old Menus">
                <h3>Old Menus</h3>
                <p>Since <span class="highlight">1889</span>, when the first pizza menu was created, not much has changed. These outdated menus fail to capture the attention of modern customers.</p>
            </div>
            <div class="card">
                <img src="new-menu.jpg" alt="New Menus">
                <h3>New Menus</h3>
                <p>Our new, visually appealing menus are designed to attract and engage your customers, making their dining experience memorable.</p>
            </div>
        </div>
    </div>

    <div class="contact" id="contact">
        <h2>Contact Us</h2>
        <form id="contact-form">
            <input type="text" id="name" placeholder="Your Name" required>
            <input type="text" id="pizzeria" placeholder="Your Pizzeria Name" required>
            <button type="button" onclick="sendWhatsAppMessage()">Send Message</button>
        </form>
        <div class="social-media-links">
            <a href="https://www.facebook.com" target="_blank">Facebook</a>
            <a href="https://www.instagram.com" target="_blank">Instagram</a>
        </div>
    </div>

    <div class="footer">
        <p>Call us at: +212 775 825 149</p>
        <p>&copy; 2024 Pizza Menu Flip. All rights reserved.</p>
    </div>

    <div class="circle-follow"></div>

    <script>
        window.onload = function() {
            document.querySelector('header').style.opacity = 1;
            document.querySelector('header').style.transform = 'translateY(0)';
            document.querySelector('.hero .content').style.opacity = 1;
            document.querySelector('.hero .content').style.transform = 'translateY(0)';
            document.querySelectorAll('.section').forEach(section => {
                section.style.opacity = 1;
                section.style.transform = 'translateY(0)';
            });
        }

        function sendWhatsAppMessage() {
            var name = document.getElementById('name').value;
            var pizzeria = document.getElementById('pizzeria').value;
            var message = `Hi, I'm ${name} from ${pizzeria}. I'm interested in ordering a custom menu for my pizzeria. I've seen the information on your amazing website and would like to know more. شكرًا لك!`;
            var whatsappUrl = `https://wa.me/212775825149?text=${encodeURIComponent(message)}`;
            window.open(whatsappUrl, '_blank');
        }

        document.addEventListener('mousemove', function(e) {
            var circle = document.querySelector('.circle-follow');
            var x = e.clientX;
            var y = e.clientY;

            circle.style.transform = `translate(${x}px, ${y}px)`;
        });
    </script>
</body>
</html>
