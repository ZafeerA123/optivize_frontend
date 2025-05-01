---
layout: base
title:
search_exclude: true
hide: true
menu: nav/home.html
---

<style>
/* Import modern fonts */
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@300;400;500;600;700&family=Playfair+Display:wght@700&display=swap');

/* Reset all margins and padding */
html, body {
    margin: 0;
    padding: 0;
    height: 100%;
    width: 100%;
    overflow-x: hidden;
    overflow-y: hidden;
    box-sizing: border-box;
    font-family: 'Montserrat', sans-serif;
    background-color: #1a1a1a;
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
    position: relative;
}

/* Subtle background pattern */
.bg-pattern {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-image: url("data:image/svg+xml,%3Csvg width='60' height='60' viewBox='0 0 60 60' xmlns='http://www.w3.org/2000/svg'%3E%3Cg fill='none' fill-rule='evenodd'%3E%3Cg fill='%23683c11' fill-opacity='0.05'%3E%3Cpath d='M36 34v-4h-2v4h-4v2h4v4h2v-4h4v-2h-4zm0-30V0h-2v4h-4v2h4v4h2V6h4V4h-4zM6 34v-4H4v4H0v2h4v4h2v-4h4v-2H6zM6 4V0H4v4H0v2h4v4h2V6h4V4H6z'/%3E%3C/g%3E%3C/g%3E%3C/svg%3E");
    opacity: 0.1;
    z-index: 0;
    pointer-events: none;
}

/* Flex for individual sections */
.section {
    flex: 1;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    text-align: center;
    transition: all 0.7s cubic-bezier(0.16, 1, 0.3, 1);
    padding: 40px;
    position: relative;
    overflow: hidden;
    z-index: 1;
}

/* Left Section - Crumbl-inspired colors with modern touch */
.left-section {
    background: linear-gradient(135deg, #472505, #784320);
    color: white;
    position: relative;
    box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
}

/* Modern glass effect for left section */
.left-section::before {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: linear-gradient(45deg, rgba(255,255,255,0.05) 0%, rgba(255,255,255,0) 100%);
    z-index: 0;
}

/* Cookie particles background */
.cookie-particles {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    overflow: hidden;
    z-index: 0;
}

.cookie-particle {
    position: absolute;
    width: 10px;
    height: 10px;
    background: radial-gradient(circle, #d4a76a 0%, transparent 70%);
    border-radius: 50%;
    opacity: 0.3;
    pointer-events: none;
}

/* Right Section - Modern light theme */
.right-section {
    background: #fcf9f5;
    color: #472505;
    box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
}

/* Hover Effects with modern interaction */
.left-section:hover {
    flex: 1.6;
    transform: translateY(-5px);
}

.right-section:hover {
    flex: 1.6;
    transform: translateY(-5px);
}

/* Modern Buttons */
.button {
    padding: 12px 28px;
    margin-top: 25px;
    font-size: 0.95rem;
    font-weight: 600;
    letter-spacing: 0.5px;
    border: none;
    cursor: pointer;
    border-radius: 30px;
    transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
    text-decoration: none;
    display: inline-block;
    position: relative;
    overflow: hidden;
    text-transform: uppercase;
    box-shadow: 0 5px 15px rgba(0, 0, 0, 0.15);
}

.button-primary {
    background: #fcf9f5;
    color: #472505;
}

.button-secondary {
    background: #472505;
    color: #fcf9f5;
}

.button::after {
    content: "";
    position: absolute;
    width: 100%;
    height: 100%;
    top: 0;
    left: -100%;
    background: linear-gradient(90deg, rgba(255,255,255,0) 0%, rgba(255,255,255,0.2) 50%, rgba(255,255,255,0) 100%);
    transition: all 0.6s ease;
}

.button:hover {
    transform: translateY(-3px) scale(1.03);
    box-shadow: 0 8px 25px rgba(0, 0, 0, 0.25);
}

.button:hover::after {
    left: 100%;
}

/* Carousel Section (1/4 of the screen) */
.carousel-container {
    width: 25%;
    background: linear-gradient(135deg, #1e1e1e, #2a2a2a);
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100%;
    position: relative;
    box-shadow: -10px 0 30px rgba(0, 0, 0, 0.2);
}

.carousel {
    width: 90%;
    max-width: 280px;
    position: relative;
    z-index: 2;
}

.carousel-slide {
    display: none;
    text-align: center;
    border-radius: 12px;
    overflow: hidden;
    box-shadow: 0 15px 35px rgba(0, 0, 0, 0.3);
    transform: translateY(30px);
    opacity: 0;
    transition: all 0.8s cubic-bezier(0.16, 1, 0.3, 1);
}

.carousel-slide img {
    width: 100%;
    height: auto;
    filter: brightness(1.05) contrast(1.05);
    transition: transform 1s ease;
}

.carousel-slide:hover img {
    transform: scale(1.05);
}

.carousel-text {
    padding: 25px;
    background-color: #472505;
    color: white;
    position: relative;
}

.carousel .active {
    display: block;
    transform: translateY(0);
    opacity: 1;
}

@keyframes float {
    0%, 100% { transform: translateY(0) rotate(0deg); }
    50% { transform: translateY(-10px) rotate(10deg); }
}

/* Animation for slides */
@keyframes fadeZoomIn {
    0% { opacity: 0; transform: scale(0.95); }
    100% { opacity: 1; transform: scale(1); }
}

.carousel-slide.active {
    animation: fadeZoomIn 0.8s forwards;
}

/* Content styling with modern typography */
.section h2 {
    margin-bottom: 25px;
    font-size: 2.5rem;
    font-family: 'Playfair Display', serif;
    font-weight: 700;
    position: relative;
    display: inline-block;
    opacity: 0;
    transform: translateY(20px);
    animation: fadeUp 0.8s forwards 0.3s;
}

@keyframes fadeUp {
    to {
        opacity: 1;
        transform: translateY(0);
    }
}

.section h2::after {
    content: "";
    position: absolute;
    bottom: -8px;
    left: 50%;
    transform: translateX(-50%);
    width: 40%;
    height: 3px;
    background: #d4a76a;
    border-radius: 2px;
}

.section p {
    margin-bottom: 25px;
    max-width: 80%;
    line-height: 1.8;
    font-weight: 400;
    opacity: 0;
    transform: translateY(20px);
    animation: fadeUp 0.8s forwards 0.5s;
}

/* Modern list styling */
.feature-list {
    text-align: left; 
    max-width: 85%; 
    margin: 10px auto 30px;
    list-style: none;
    padding-left: 0;
}

.feature-list li {
    margin-bottom: 16px;
    padding-left: 35px;
    position: relative;
    opacity: 0;
    transform: translateY(20px);
}

.feature-list li:nth-child(1) { animation: fadeUp 0.8s forwards 0.6s; }
.feature-list li:nth-child(2) { animation: fadeUp 0.8s forwards 0.7s; }
.feature-list li:nth-child(3) { animation: fadeUp 0.8s forwards 0.8s; }
.feature-list li:nth-child(4) { animation: fadeUp 0.8s forwards 0.9s; }

.feature-list li::before {
    content: "";
    position: absolute;
    left: 0;
    top: 50%;
    transform: translateY(-50%);
    width: 22px;
    height: 22px;
    background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 512 512'%3E%3Cpath fill='%23d4a76a' d='M256 8C119 8 8 119 8 256s111 248 248 248 248-111 248-248S393 8 256 8zm0 448c-110.5 0-200-89.5-200-200S145.5 56 256 56s200 89.5 200 200-89.5 200-200 200zm61.8-104.4l-84.9-61.7c-3.1-2.3-4.9-5.9-4.9-9.7V116c0-6.6 5.4-12 12-12h32c6.6 0 12 5.4 12 12v141.7l66.8 48.6c5.4 3.9 6.5 11.4 2.6 16.8L334.6 349c-3.9 5.3-11.4 6.5-16.8 2.6z'/%3E%3C/svg%3E");
    background-size: contain;
    background-repeat: no-repeat;
}

.feature-list li strong {
    color: #d4a76a;
    font-weight: 600;
    letter-spacing: 0.5px;
}

/* Modern logo container with animation */
.logo-container {
    margin-bottom: 30px;
    opacity: 0;
    transform: translateY(20px);
    animation: fadeUp 0.8s forwards 0.2s;
}

.logo {
    font-family: 'Playfair Display', serif;
    font-size: 2.8rem;
    font-weight: 700;
    color: #472505;
    position: relative;
    display: inline-block;
}

.logo::before {
    content: "";
    position: absolute;
    width: 40px;
    height: 40px;
    background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 512 512'%3E%3Cpath fill='%23d4a76a' d='M510.37 254.79l-12.08-76.26a132.493 132.493 0 0 0-37.16-72.95l-54.76-54.75c-19.73-19.72-45.18-32.7-72.71-37.05l-76.7-12.15c-27.51-4.36-55.69.11-80.52 12.76L107.32 46.35c-25.41 13-46.03 33.68-58.97 59.16L15.27 174.12c-13.02 25.53-17.44 54.03-12.92 81.97l13.03 80.03c4.44 27.27 17.59 52.42 37.31 71.75l54.76 54.75c19.72 19.73 45.18 32.7 72.71 37.05l76.7 12.14c27.51 4.36 55.69-.11 80.52-12.75l69.12-35.21c25.41-12.99 46.03-33.67 58.97-59.15l33.09-68.61c12.99-25.53 17.42-54.03 12.91-80.97zM176 368c-17.67 0-32-14.33-32-32s14.33-32 32-32 32 14.33 32 32-14.33 32-32 32zm32-160c-17.67 0-32-14.33-32-32s14.33-32 32-32 32 14.33 32 32-14.33 32-32 32zm160 128c-17.67 0-32-14.33-32-32s14.33-32 32-32 32 14.33 32 32-14.33 32-32 32z'/%3E%3C/svg%3E");
    background-repeat: no-repeat;
    background-size: contain;
    left: -45px;
    top: 8px;
    opacity: 0.8;
}

/* Cookie icon with modern styling */
.cookie-icon {
    margin-bottom: 20px;
    width: 70px;
    height: 70px;
    background-color: rgba(255, 255, 255, 0.1);
    border-radius: 50%;
    display: flex;
    justify-content: center;
    align-items: center;
    position: relative;
    opacity: 0;
    transform: translateY(20px) scale(0.8);
    animation: fadeUp 0.8s forwards 0.1s;
    box-shadow: 0 10px 25px rgba(0, 0, 0, 0.2);
}

.cookie-icon::before {
    content: "🍪";
    font-size: 2.5rem;
}

.cookie-icon::after {
    content: "";
    position: absolute;
    top: -5px;
    left: -5px;
    right: -5px;
    bottom: -5px;
    border-radius: 50%;
    border: 2px solid rgba(255, 255, 255, 0.1);
    animation: pulse 2s infinite;
}

@keyframes pulse {
    0% { transform: scale(1); opacity: 1; }
    50% { transform: scale(1.1); opacity: 0.5; }
    100% { transform: scale(1); opacity: 1; }
}

/* Modern metric display */
.metrics-container {
    display: flex;
    justify-content: space-around;
    width: 90%;
    margin: 20px 0;
    opacity: 0;
    transform: translateY(20px);
    animation: fadeUp 0.8s forwards 1s;
}

.metric {
    text-align: center;
    padding: 15px;
}

.metric-value {
    font-size: 2.5rem;
    font-weight: 700;
    color: #d4a76a;
    margin-bottom: 5px;
    display: inline-block;
}

.metric-label {
    font-size: 0.8rem;
    text-transform: uppercase;
    letter-spacing: 1px;
    opacity: 0.7;
}

/* Glass card effect */
.glass-card {
    background: rgba(255, 255, 255, 0.05);
    backdrop-filter: blur(10px);
    -webkit-backdrop-filter: blur(10px);
    border-radius: 15px;
    border: 1px solid rgba(255, 255, 255, 0.1);
    padding: 20px;
    width: 90%;
    margin: 20px 0;
    opacity: 0;
    transform: translateY(20px);
    animation: fadeUp 0.8s forwards 1.1s;
}

/* 3D Transform on hover for cards */
.glass-card:hover {
    transform: perspective(1000px) rotateX(5deg) rotateY(5deg);
    transition: transform 0.5s ease;
}
</style>

<!-- Main Split Container -->
<div class="split-container">
    <!-- Left and Right Sections (3/4 of the screen) -->
    <div class="left-right-container">
        <div class="bg-pattern"></div>
        
<!-- Cookie particles for animation -->
<div class="cookie-particles">
    <div class="cookie-particle" style="top:10%; left:20%; animation: float 7s infinite;"></div>
    <div class="cookie-particle" style="top:30%; left:80%; animation: float 9s infinite 1s;"></div>
    <div class="cookie-particle" style="top:70%; left:15%; animation: float 8s infinite 0.5s;"></div>
    <div class="cookie-particle" style="top:85%; left:70%; animation: float 10s infinite 2s;"></div>
    <div class="cookie-particle" style="top:25%; left:40%; animation: float 6s infinite 1s;"></div>
    <div class="cookie-particle" style="top:60%; left:50%; animation: float 11s infinite 0.5s;"></div>
    <div class="cookie-particle" style="top:15%; left:60%; animation: float 7s infinite 2s;"></div>
    <div class="cookie-particle" style="top:45%; left:30%; animation: float 9s infinite 1.5s;"></div>
</div>

<!-- Left Section -->
<div class="section left-section">
    <div class="cookie-icon"></div>
    <h2>Cookie Success Predictor</h2>
    <p>Our AI-powered analytics platform elevates your cookie business with precision forecasting and data intelligence.</p>
    
<ul class="feature-list">
    <li><strong>Precision Intelligence</strong> - Algorithms predict market success</li>
    <li><strong>Visual Analytics</strong> - Interactive dashboards visualize key performance metrics</li>
    <li><strong>Strategic Insights</strong> - AI-generated recommendations for optimized product launches</li>
</ul>

<a href="/optivize_frontend/predictions" class="button button-primary">Launch Predictor</a>
</div>

<!-- Right Section -->
<div class="section right-section">
    <div class="logo-container">
        <span class="logo">Optivize</span>
    </div>
    <h2>Enterprise Solutions</h2>
    <p>Experience how Optivize transforms small businesses today.</p>
    

<a href="/optivize_frontend/about" class="button button-secondary">Discover More</a>
</div>
</div>

<!-- Carousel Section (1/4 of the screen) -->
<div class="carousel-container">
    <div class="carousel">
        <!-- Carousel Slides -->
        <div class="carousel-slide active">
            <img src="{{site.baseurl}}/images/chatbot.PNG" alt="AI Assistant">
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
// Carousel functionality with improved animation
let currentSlide = 0;
const slides = document.querySelectorAll('.carousel-slide');
const totalSlides = slides.length;

function showSlide(index) {
    slides.forEach((slide) => {
        slide.classList.remove('active');
    });
    
    slides[index].classList.add('active');
}

setInterval(() => {
    currentSlide = (currentSlide + 1) % totalSlides;
    showSlide(currentSlide);
}, 5000); // Change slide every 5 seconds

// Create cookie particles for a more dynamic background
function createCookieParticles() {
    const particlesContainer = document.querySelector('.cookie-particles');
    for(let i = 0; i < 10; i++) {
        const particle = document.createElement('div');
        particle.classList.add('cookie-particle');
        
        // Random positioning
        const top = Math.random() * 100;
        const left = Math.random() * 100;
        
        // Random animation delay
        const delay = Math.random() * 5;
        const duration = 5 + Math.random() * 10;
        
        particle.style.top = `${top}%`;
        particle.style.left = `${left}%`;
        particle.style.animation = `float ${duration}s infinite ${delay}s`;
        
        particlesContainer.appendChild(particle);
    }
}

// Call function on page load
window.addEventListener('load', createCookieParticles);

// Add subtle parallax effect on mouse move
document.addEventListener('mousemove', (e) => {
    const sections = document.querySelectorAll('.section');
    const mouseX = e.clientX / window.innerWidth;
    const mouseY = e.clientY / window.innerHeight;
    
    sections.forEach((section) => {
        const moveX = mouseX * 20 - 10;
        const moveY = mouseY * 20 - 10;
        section.style.backgroundPosition = `${moveX}px ${moveY}px`;
    });
    
    // Move particles slightly with mouse
    const particles = document.querySelectorAll('.cookie-particle');
    particles.forEach((particle) => {
        const moveX = mouseX * 5 - 2.5;
        const moveY = mouseY * 5 - 2.5;
        particle.style.transform = `translate(${moveX}px, ${moveY}px)`;
    });
});
</script>