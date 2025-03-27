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
    box-sizing: border-box; /* Ensures padding/border is included in element's width/height */
}


/* Fullscreen split container */
.split-container {
    display: flex;
    width: 100vw; /* Full width of the viewport */
    height: calc(100vh - 90px); /* Subtract header height to fit content below */
    overflow: hidden; /* Hides any unwanted overflow */
    position: absolute; /* Position container relative to the page */
    top: 90px; /* Push content below header */
    left: 0;
}

/* Left and Right Sections (3/4 and 1/4 of the screen) */
.left-right-container {
    display: flex;
    width: 75%; /* 75% of the screen width */
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
    width: 25%; /* Carousel takes 25% of the screen */
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
</style>


<!-- Main Split Container -->
<div class="split-container">
    <!-- Left and Right Sections (3/4 of the screen) -->
    <div class="left-right-container">
        <!-- Left Section -->
        <div class="section left-section">
            <h2>AI Solutions</h2>
            <p>Enhancing business efficiency through AI-powered tools.</p>
            <button class="button button-primary">Explore</button>
        </div>

        <!-- Right Section -->
        <div class="section right-section">
            <h2>Business Impact</h2>
            <p>See how Optivize transforms local businesses.</p>
            <button class="button button-secondary">Learn More</button>
        </div>
    </div>

    <!-- Carousel Section (1/4 of the screen) -->
    <div class="carousel-container">
        <div class="carousel">
            <!-- Carousel Slides -->
            <div class="carousel-slide active">
                <img src="{{site.baseurl}}/images/chatbot.PNG" alt="Image 1">
            </div>
            <div class="carousel-slide">
                <img src="{{site.baseurl}}/images/inventory.jpg" alt="Image 2">
            </div>
            <div class="carousel-slide">
                <img src="{{site.baseurl}}/images/salesanalysis.jpg" alt="Image 3">
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

