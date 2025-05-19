---
layout: base
title: 
search_exclude: true
hide: true
menu: nav/home.html
---

<style>
  /* Base styles with dark blue theme */
  body {
    margin: 0;
    padding: 0;
    font-family: 'Inter', sans-serif;
    color: #fff;
  }
  
  /* Gradient background with animation */
  .page-background {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: linear-gradient(135deg, #0b1e3b, #162b4d);
    z-index: -2;
  }
  
  /* Gradient overlay animation */
  .gradient-overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: radial-gradient(circle at 70% 20%, rgba(43, 83, 158, 0.2), transparent 60%),
                radial-gradient(circle at 20% 80%, rgba(29, 47, 94, 0.3), transparent 60%);
    animation: gradientMove 20s infinite alternate;
    z-index: -1;
  }
  
  @keyframes gradientMove {
    0% { background-position: 0% 0%; }
    100% { background-position: 100% 100%; }
  }
  
  .hero-container {
    position: relative;
    padding: 40px 20px;
    overflow: hidden;
  }
  
  /* Glowing orbs in background */
  .glow-orb {
    position: absolute;
    border-radius: 50%;
    filter: blur(60px);
    opacity: 0.15;
    z-index: 0;
  }
  
  .glow-orb-1 {
    top: 10%;
    left: 5%;
    width: 300px;
    height: 300px;
    background: radial-gradient(circle, rgba(251, 176, 52, 0.6), rgba(251, 176, 52, 0) 70%);
    animation: float 25s infinite alternate;
  }
  
  .glow-orb-2 {
    bottom: 10%;
    right: 5%;
    width: 400px;
    height: 400px;
    background: radial-gradient(circle, rgba(66, 99, 176, 0.4), rgba(66, 99, 176, 0) 70%);
    animation: float 30s infinite alternate-reverse;
  }
  
  .glow-orb-3 {
    top: 50%;
    left: 50%;
    width: 350px;
    height: 350px;
    background: radial-gradient(circle, rgba(251, 176, 52, 0.3), rgba(66, 99, 176, 0.2), rgba(66, 99, 176, 0) 70%);
    animation: float 35s infinite alternate;
  }
  
  @keyframes float {
    0% { transform: translate(0, 0) scale(1); }
    50% { transform: translate(50px, -30px) scale(1.1); }
    100% { transform: translate(-30px, 50px) scale(0.9); }
  }
  
  /* Hero section */
  .hero-section {
    max-width: 1200px;
    margin: 0 auto;
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    gap: 40px;
    position: relative;
    z-index: 1;
  }
  
  .hero-content {
    flex: 1;
    min-width: 300px;
  }
  
  .hero-title {
    font-size: 3.5rem;
    font-weight: 700;
    margin-bottom: 20px;
    background: linear-gradient(to right, #fbb034, #ffdd00, #fbb034);
    background-size: 200% auto;
    -webkit-background-clip: text;
    background-clip: text;
    color: transparent;
    animation: shine 3s linear infinite;
  }
  
  @keyframes shine {
    to {
      background-position: 200% center;
    }
  }
  
  .hero-description {
    font-size: 1.2rem;
    margin-bottom: 30px;
    color: rgba(255, 255, 255, 0.85);
    line-height: 1.6;
    text-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
  }
  
  .button-container {
    display: flex;
    gap: 15px;
    flex-wrap: wrap;
  }
  
  .button {
    display: inline-block;
    padding: 12px 24px;
    border-radius: 50px;
    font-weight: 600;
    text-decoration: none;
    transition: all 0.3s;
    position: relative;
    z-index: 1;
    overflow: hidden;
  }
  
  .button::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: -1;
    opacity: 0;
    transition: opacity 0.3s ease;
  }
  
  .primary-button {
    background: linear-gradient(90deg, #fbb034, #ffdd00);
    color: #0f1e3b;
    box-shadow: 0 4px 15px rgba(251, 176, 52, 0.3);
  }
  
  .primary-button::before {
    background: linear-gradient(90deg, #ffdd00, #fbb034);
  }
  
  .primary-button:hover {
    transform: translateY(-3px);
    box-shadow: 0 8px 25px rgba(251, 176, 52, 0.4);
  }
  
  .primary-button:hover::before {
    opacity: 1;
  }
  
  .secondary-button {
    background: rgba(255, 255, 255, 0.08);
    color: #fbb034;
    border: 2px solid rgba(251, 176, 52, 0.3);
    backdrop-filter: blur(5px);
  }
  
  .secondary-button::before {
    background: rgba(251, 176, 52, 0.15);
  }
  
  .secondary-button:hover {
    transform: translateY(-3px);
    box-shadow: 0 8px 25px rgba(0, 0, 0, 0.2);
    border-color: rgba(251, 176, 52, 0.5);
  }
  
  .secondary-button:hover::before {
    opacity: 1;
  }
  
  /* Demo section */
  .demo-section {
    flex: 1;
    min-width: 300px;
    position: relative;
  }
  
  .demo-glow {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    width: 100%;
    height: 100%;
    border-radius: 20px;
    filter: blur(40px);
    background: radial-gradient(circle, rgba(251, 176, 52, 0.15), transparent 70%);
    z-index: 0;
  }
  
  .demo-window {
    position: relative;
    background: rgba(255, 255, 255, 0.03);
    backdrop-filter: blur(10px);
    border-radius: 16px;
    overflow: hidden;
    box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2), 
                inset 0 0 0 1px rgba(255, 255, 255, 0.1);
    z-index: 1;
  }
  
  .window-header {
    background: rgba(255, 255, 255, 0.05);
    padding: 15px;
    display: flex;
    align-items: center;
    border-bottom: 1px solid rgba(255, 255, 255, 0.05);
  }
  
  .window-controls {
    display: flex;
    gap: 8px;
  }
  
  .window-circle {
    width: 12px;
    height: 12px;
    border-radius: 50%;
  }
  
  .window-circle.red { background-color: #ff5f57; }
  .window-circle.yellow { background-color: #febc2e; }
  .window-circle.green { background-color: #28c840; }
  
  .app-title {
    flex: 1;
    text-align: center;
    font-size: 14px;
    color: rgba(255, 255, 255, 0.7);
  }
  
  .window-content {
    padding: 25px;
  }
  
  .window-title {
    font-size: 1.5rem;
    font-weight: 600;
    margin-bottom: 20px;
    color: #fff;
    text-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }
  
  .product-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 15px;
    margin-bottom: 25px;
  }
  
  .product-item {
    background: rgba(255, 255, 255, 0.04);
    border: 1px solid rgba(255, 255, 255, 0.08);
    border-radius: 12px;
    padding: 15px;
    text-align: center;
    transition: all 0.3s;
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
    backdrop-filter: blur(5px);
  }
  
  .product-item:hover {
    background: rgba(255, 255, 255, 0.08);
    transform: translateY(-2px);
    box-shadow: 0 8px 20px rgba(0, 0, 0, 0.15);
    border-color: rgba(251, 176, 52, 0.2);
  }
  
  .product-name {
    font-weight: 600;
    color: #fbb034;
    margin-bottom: 5px;
    text-shadow: 0 1px 2px rgba(0, 0, 0, 0.1);
  }
  
  .product-quantity {
    color: rgba(255, 255, 255, 0.7);
    font-size: 0.9rem;
  }
  
  .try-button {
    position: relative;
    display: block;
    width: 100%;
    padding: 12px;
    text-align: center;
    background: linear-gradient(90deg, #fbb034, #ffdd00);
    color: #0f1e3b;
    border-radius: 12px;
    text-decoration: none;
    font-weight: 600;
    transition: all 0.3s;
    box-shadow: 0 4px 15px rgba(251, 176, 52, 0.3);
    overflow: hidden;
  }
  
  .try-button::before {
    content: '';
    position: absolute;
    top: 0;
    left: -100%;
    width: 100%;
    height: 100%;
    background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.2), transparent);
    transition: all 0.6s ease;
  }
  
  .try-button:hover {
    transform: translateY(-3px);
    box-shadow: 0 8px 25px rgba(251, 176, 52, 0.4);
  }
  
  .try-button:hover::before {
    left: 100%;
  }
  
  .chatbot-icon {
    position: absolute;
    bottom: -10px;
    left: -10px;
    width: 36px;
    height: 36px;
    background: linear-gradient(135deg, #132a55, #0b1e3b);
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.3),
                inset 0 0 0 1px rgba(255, 255, 255, 0.1);
    border: 2px solid rgba(251, 176, 52, 0.3);
    z-index: 2;
  }
  
  /* Features section */
  .features-section {
    position: relative;
    padding: 100px 20px;
    overflow: hidden;
  }
  
  .features-bg {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: linear-gradient(135deg, rgba(15, 30, 59, 0.8), rgba(22, 43, 77, 0.8));
    z-index: 0;
  }
  
  .features-content {
    max-width: 1200px;
    margin: 0 auto;
    position: relative;
    z-index: 1;
  }
  
  .section-header {
    text-align: center;
    max-width: 800px;
    margin: 0 auto 60px;
  }
  
  .section-title {
    font-size: 2.5rem;
    font-weight: 700;
    margin-bottom: 20px;
    background: linear-gradient(to right, #fbb034, #ffdd00, #fbb034);
    background-size: 200% auto;
    -webkit-background-clip: text;
    background-clip: text;
    color: transparent;
    display: inline-block;
    animation: shine 3s linear infinite;
  }
  
  .section-description {
    font-size: 1.2rem;
    color: rgba(255, 255, 255, 0.85);
    line-height: 1.6;
    text-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
  }
  
  /* Feature cards */
  .features-container {
    max-width: 1000px;
    margin: 50px auto 0;
    display: flex;
    flex-direction: column;
  }
  
  .top-features {
    display: flex;
    justify-content: space-between;
    gap: 30px;
    margin-bottom: 100px; /* Increased space between rows */
  }
  
  .bottom-feature {
    max-width: 500px;
    margin: 0 auto;
  }
  
  .feature-card {
    background: rgba(255, 255, 255, 0.03);
    backdrop-filter: blur(10px);
    border-radius: 20px;
    overflow: hidden;
    box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2), 
                inset 0 0 0 1px rgba(255, 255, 255, 0.05);
    padding: 40px;
    transition: all 0.5s cubic-bezier(0.175, 0.885, 0.32, 1.275);
    flex: 1;
    position: relative;
  }
  
  /* Gradient border effect */
  .feature-card::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    border-radius: 20px;
    padding: 2px;
    background: linear-gradient(135deg, rgba(251, 176, 52, 0.5), rgba(255, 255, 255, 0.1), rgba(251, 176, 52, 0), rgba(255, 255, 255, 0.05));
    -webkit-mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
    -webkit-mask-composite: xor;
    mask-composite: exclude;
    opacity: 0.5;
    transition: opacity 0.5s ease;
  }
  
  .feature-card:hover {
    transform: translateY(-15px) scale(1.03);
    background: rgba(255, 255, 255, 0.06);
    box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3), 
                inset 0 0 0 1px rgba(255, 255, 255, 0.1);
  }
  
  .feature-card:hover::before {
    opacity: 1;
  }
  
  .feature-icon {
    width: 80px;
    height: 80px;
    margin: 0 auto 25px;
    display: flex;
    align-items: center;
    justify-content: center;
    background: linear-gradient(135deg, rgba(251, 176, 52, 0.1), rgba(255, 221, 0, 0.05));
    border-radius: 20px;
    font-size: 28px;
    position: relative;
    box-shadow: 0 8px 20px rgba(0, 0, 0, 0.1),
                inset 0 0 0 1px rgba(255, 255, 255, 0.05);
  }
  
  .feature-icon::before {
    content: '';
    position: absolute;
    inset: 0;
    border-radius: 20px;
    padding: 1px;
    background: linear-gradient(135deg, rgba(251, 176, 52, 0.6), rgba(255, 255, 255, 0.1));
    -webkit-mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
    -webkit-mask-composite: xor;
    mask-composite: exclude;
  }
  
  .feature-title {
    font-size: 1.8rem;
    font-weight: 600;
    margin-bottom: 20px;
    color: #fbb034;
    text-align: center;
    text-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }
  
  .feature-description {
    color: rgba(255, 255, 255, 0.85);
    line-height: 1.6;
    text-align: center;
    font-size: 1.1rem;
  }
  
  /* CTA section */
  .cta-section {
    position: relative;
    padding: 100px 20px;
    text-align: center;
    overflow: hidden;
  }
  
  .cta-bg {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: linear-gradient(135deg, rgba(22, 43, 77, 0.9), rgba(26, 47, 92, 0.9));
    z-index: 0;
  }
  
  .cta-ripple {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    width: 600px;
    height: 600px;
    border-radius: 50%;
    background: radial-gradient(circle, rgba(251, 176, 52, 0.05) 0%, transparent 70%);
    opacity: 0.5;
    z-index: 0;
  }
  
  .cta-ripple::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    border-radius: 50%;
    border: 1px solid rgba(251, 176, 52, 0.2);
    animation: ripple 4s linear infinite;
  }
  
  .cta-ripple::after {
    content: '';
    position: absolute;
    top: -20%;
    left: -20%;
    right: -20%;
    bottom: -20%;
    border-radius: 50%;
    border: 1px solid rgba(251, 176, 52, 0.2);
    animation: ripple 4s linear infinite 2s;
  }
  
  @keyframes ripple {
    0% {
      transform: scale(0.8);
      opacity: 0.8;
    }
    100% {
      transform: scale(1.5);
      opacity: 0;
    }
  }
  
  .cta-content {
    max-width: 800px;
    margin: 0 auto;
    position: relative;
    z-index: 1;
  }
  
  .cta-title {
    font-size: 2.5rem;
    font-weight: 700;
    margin-bottom: 20px;
    color: #fff;
    text-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }
  
  .cta-description {
    font-size: 1.2rem;
    color: rgba(255, 255, 255, 0.85);
    margin: 0 auto 30px;
    line-height: 1.6;
    max-width: 600px;
    text-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
  }
  
  .cta-buttons {
    display: flex;
    justify-content: center;
    gap: 20px;
    flex-wrap: wrap;
  }
  
  /* Responsive adjustments */
  @media (max-width: 768px) {
    .hero-title {
      font-size: 2.5rem;
    }
    
    .section-title, .cta-title {
      font-size: 2rem;
    }
    
    .top-features {
      flex-direction: column;
      margin-bottom: 50px;
    }
    
    .feature-title {
      font-size: 1.5rem;
    }
  }
</style>

<!-- Page Background with Gradients -->
<div class="page-background"></div>
<div class="gradient-overlay"></div>

<!-- Hero Section -->
<div class="hero-container">
  <!-- Glowing Orbs -->
  <div class="glow-orb glow-orb-1"></div>
  <div class="glow-orb glow-orb-2"></div>
  <div class="glow-orb glow-orb-3"></div>
  
  <div class="hero-section">
    <div class="hero-content">
      <h1 class="hero-title">Optivize brings it all together</h1>
      <p class="hero-description">Our AI-powered analytics platform elevates your business with precision forecasting, inventory management, and data intelligence.</p>
      <div class="button-container">
        <a href="/optivize_frontend/navigation/predictions" class="button primary-button">Try Predictions</a>
        <a href="/optivize_frontend/about" class="button secondary-button">Learn More</a>
      </div>
    </div>
    
<div class="demo-section">
    <div class="demo-glow"></div>
    <div class="demo-window">
    <div class="window-header">
        <div class="window-controls">
        <div class="window-circle red"></div>
        <div class="window-circle yellow"></div>
        <div class="window-circle green"></div>
        </div>
        <div class="app-title">optivize.app</div>
    </div>
    <div class="window-content">
        <h3 class="window-title">Inventory Management</h3>
        <div class="product-grid">
        <div class="product-item">
            <div class="product-name">Product A</div>
            <div class="product-quantity">32 units</div>
        </div>
        <div class="product-item">
            <div class="product-name">Product B</div>
            <div class="product-quantity">18 units</div>
        </div>
        <div class="product-item">
            <div class="product-name">Product C</div>
            <div class="product-quantity">47 units</div>
        </div>
        <div class="product-item">
            <div class="product-name">Product D</div>
            <div class="product-quantity">63 units</div>
        </div>
        </div>
        <div style="position: relative;">
        <a href="/optivize_frontend/flashcards" class="try-button">
            Try Inventory Management
            <div class="chatbot-icon">
            <svg width="20" height="20" viewBox="0 0 24 24" fill="#fbb034">
                <path d="M12 2C6.48 2 2 6.48 2 12C2 17.52 6.48 22 12 22C17.52 22 22 17.52 22 12C22 6.48 17.52 2 12 2ZM16 12C16 12.41 15.66 12.75 15.25 12.75H12.75V15.25C12.75 15.66 12.41 16 12 16C11.59 16 11.25 15.66 11.25 15.25V12.75H8.75C8.34 12.75 8 12.41 8 12C8 11.59 8.34 11.25 8.75 11.25H11.25V8.75C11.25 8.34 11.59 8 12 8C12.41 8 12.75 8.34 12.75 8.75V11.25H15.25C15.66 11.25 16 11.59 16 12Z"/>
            </svg>
            </div>
        </a>
        </div>
    </div>
    </div>
</div>
  </div>
</div>

<!-- Features Section -->
<div class="features-section">
  <div class="features-bg"></div>
  
  <div class="features-content">
    <div class="section-header">
      <h2 class="section-title">All-in-One Business Solution</h2>
      <p class="section-description">Optivize provides the tools small businesses need to succeed in today's competitive market.</p>
    </div>
    
<!-- Feature Cards - with proper spacing -->
<div class="features-container">
    <!-- Top row with two cards side by side -->
    <div class="top-features">
    <div class="feature-card">
        <div class="feature-icon">
        <svg width="40" height="40" viewBox="0 0 24 24" fill="#fbb034">
            <path d="M3 13h2v-2H3v2zm0 4h2v-2H3v2zm0-8h2V7H3v2zm4 4h14v-2H7v2zm0 4h14v-2H7v2zM7 7v2h14V7H7z"/>
        </svg>
        </div>
        <h3 class="feature-title">AI-Powered Analytics</h3>
        <p class="feature-description">Use artificial intelligence to predict product success rates and optimize your business decisions.</p>
    </div>
    
<div class="feature-card">
    <div class="feature-icon">
    <svg width="40" height="40" viewBox="0 0 24 24" fill="#fbb034">
        <path d="M21.41 11.58l-9-9C12.05 2.22 11.55 2 11 2H4c-1.1 0-2 .9-2 2v7c0 .55.22 1.05.59 1.42l9 9c.36.36.86.58 1.41.58.55 0 1.05-.22 1.41-.59l7-7c.37-.36.59-.86.59-1.41 0-.55-.23-1.06-.59-1.42zM5.5 7C4.67 7 4 6.33 4 5.5S4.67 4 5.5 4 7 4.67 7 5.5 6.33 7 5.5 7z"/>
    </svg>
    </div>
    <h3 class="feature-title">Smart Inventory</h3>
    <p class="feature-description">Manage your inventory using natural language commands and get intelligent recommendations.</p>
</div>
</div>

<!-- Bottom row with one centered card -->
<div class="bottom-feature">
<div class="feature-card">
    <div class="feature-icon">
    <svg width="40" height="40" viewBox="0 0 24 24" fill="#fbb034">
        <path d="M20 2H4c-1.1 0-1.99.9-1.99 2L2 22l4-4h14c1.1 0 2-.9 2-2V4c0-1.1-.9-2-2-2zm-7 9h-2V5h2v6zm0 4h-2v-2h2v2z"/>
    </svg>
    </div>
    <h3 class="feature-title">Business Assistant</h3>
    <p class="feature-description">Let our AI chatbot help you automate tasks and answer questions about your business data.</p>
</div>
</div>
</div>
  </div>
</div>

<!-- the CTA Section -->
<div class="cta-section">
  <div class="cta-bg"></div>
  <div class="cta-ripple"></div>
  
  <div class="cta-content">
    <h2 class="cta-title">Ready to transform your business?</h2>
    <p class="cta-description">Experience how Optivize can help you manage inventory, predict success, and grow your business.</p>
    <div class="cta-buttons">
      <a href="/optivize_frontend/navigation/predictions" class="button primary-button">Try Predictions</a>
      <a href="/optivize_frontend/bot" class="button primary-button">Try Chatbot</a>
    </div>
  </div>
</div>
