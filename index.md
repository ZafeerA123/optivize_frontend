---
layout: base
title:
search_exclude: true
hide: true
menu: nav/home.html
---

<style>
/* Reset all margins and padding */
html, body {
    margin: 0;
    padding: 0;
    height: 100%;
    width: 100%;
    overflow-x: hidden;
    overflow-y: hidden;
    box-sizing: border-box;
}

/* Fullscreen split container */
.split-container {
    display: flex;
    width: 100vw;
    height: calc(100vh - 80px);
    overflow: hidden;
    position: absolute;
    top: 80px;
    left: 0;
}

/* Left and Right Sections (3/4 and 1/4 of the screen) */
.left-right-container {
    display: flex;
    width: 75%;
    height: 100%;
}

/* Flex for individual sections */
.section {
    flex: 1;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    text-align: center;
    transition: flex 0.5s ease;
    padding: 20px;
}

/* Left Section */
.left-section {
    background: linear-gradient(135deg, #024a57, #132068);
    color: white;
}

/* Right Section */
.right-section {
    background: white;
    color: #132068;
}

/* Hover Effects */
.left-section:hover {
    flex: 1.5;
}
.right-section:hover {
    flex: 1.5;
}

/* Buttons */
.button {
    padding: 10px 20px;
    margin-top: 10px;
    font-size: 1rem;
    border: none;
    cursor: pointer;
    border-radius: 5px;
    transition: 0.3s;
    text-decoration: none;
    display: inline-block;
}

.button-primary {
    background: white;
    color: #132068;
}

.button-secondary {
    background: #132068;
    color: white;
}

.button:hover {
    opacity: 0.8;
}

/* Carousel Section (1/4 of the screen) */
.carousel-container {
    width: 25%;
    background: #f4f4f4;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100%;
}

.carousel {
    width: 100%;
    max-width: 250px;
    position: relative;
}

.carousel-slide {
    display: none;
    text-align: center;
}

.carousel-slide img {
    width: 100%;
    height: auto;
}

.carousel-text {
    padding: 20px;
    background-color: #024a57;
    color: white;
}

.carousel .active {
    display: block;
}

/* Animation */
@keyframes fade {
    0% { opacity: 0; }
    20% { opacity: 1; }
    80% { opacity: 1; }
    100% { opacity: 0; }
}

.carousel-slide {
    animation: fade 10s infinite;
}

/* Content styling */
.section h2 {
    margin-bottom: 20px;
    font-size: 2rem;
}

.section p {
    margin-bottom: 20px;
    max-width: 80%;
}
</style>

<!-- Main Split Container -->
<div class="split-container">
    <!-- Left and Right Sections (3/4 of the screen) -->
    <div class="left-right-container">
        <!-- Left Section -->
        <div class="section left-section">
            <h2>AI Solutions</h2>
            <p>Our AI-powered tool helps you forecast cookie product success with:</p>
            <ul style="text-align: left; max-width: 80%; margin: 0 auto 20px;">
                <li><strong>Smart Prediction Model</strong> - Analyzes multiple factors to calculate success scores</li>
                <li><strong>Data-Driven Insights</strong> - Visual dashboards show key success factors</li>
                <li><strong>Actionable Recommendations</strong> - Tailored advice for product launches</li>
                <li><strong>Historical Analysis</strong> - Track all predictions with searchable history</li>
            </ul>
            <a href="/optivize_frontend/predictions" class="button button-primary">Try the Predictor</a>
        </div>

        <!-- Right Section -->
        <div class="section right-section">
            <h2>Business Impact</h2>
            <p>See how Optivize transforms local businesses.</p>
            <a href="/optivize_frontend/about" class="button button-secondary">Learn More</a>
        </div>
    </div>

    <!-- Carousel Section (1/4 of the screen) -->
    <div class="carousel-container">
        <div class="carousel">
            <!-- Carousel Slides -->
            <div class="carousel-slide active">
                <img src="{{site.baseurl}}/images/chatbot.PNG" alt="Chatbot">
            </div>
            <div class="carousel-slide">
                <img src="{{site.baseurl}}/images/inventory.jpg" alt="Inventory Management">
            </div>
            <div class="carousel-slide">
                <img src="{{site.baseurl}}/images/salesanalysis.jpg" alt="Sales Analysis">
            </div>
            <div class="carousel-slide">
                <div class="carousel-text">
                    <h2>About Us</h2>
                    <p>DNHS AP CSP Group: Marti, Nikhil, Keerthan, Zafeer, Hithin, Aarav</p>
                </div>
            </div>
        </div>
    </div>
</div>

<script>
// Carousel functionality
let currentSlide = 0;
const slides = document.querySelectorAll('.carousel-slide');
const totalSlides = slides.length;

function showSlide(index) {
    slides.forEach((slide, i) => {
        slide.classList.remove('active');
        if (i === index) {
            slide.classList.add('active');
        }
    });
}

setInterval(() => {
    currentSlide = (currentSlide + 1) % totalSlides;
    showSlide(currentSlide);
}, 5000); // Change slide every 5 seconds
</script>