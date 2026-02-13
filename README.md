<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Nadeesh | Java Developer</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Fira+Code:wght@400;600&family=Outfit:wght@300;400;600;800&display=swap" rel="stylesheet">
    
    <style>
        /* --- CSS Variables & Reset --- */
        :root {
            --bg-color: #1a1b26; /* Tokyo Night Background */
            --card-bg: #24283b;
            --text-primary: #c0caf5;
            --text-secondary: #a9b1d6;
            --accent-cyan: #7aa2f7;
            --accent-magenta: #bb9af7;
            --accent-green: #9ece6a;
            --accent-yellow: #e0af68;
            --transition-speed: 0.3s;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        html {
            scroll-behavior: smooth;
        }

        body {
            font-family: 'Outfit', sans-serif;
            background-color: var(--bg-color);
            color: var(--text-primary);
            overflow-x: hidden;
            line-height: 1.6;
        }

        /* --- Animated Background Canvas --- */
        #bg-canvas {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            opacity: 0.4;
        }

        /* --- Typography & Utilities --- */
        h1, h2, h3 {
            color: #fff;
            margin-bottom: 1rem;
        }

        .highlight {
            color: var(--accent-cyan);
        }

        .container {
            max-width: 1100px;
            margin: 0 auto;
            padding: 0 20px;
        }

        .section-title {
            font-size: 2.5rem;
            text-align: center;
            margin-bottom: 3rem;
            position: relative;
            display: inline-block;
            left: 50%;
            transform: translateX(-50%);
        }

        .section-title::after {
            content: '';
            display: block;
            width: 60px;
            height: 4px;
            background: linear-gradient(90deg, var(--accent-cyan), var(--accent-magenta));
            margin: 10px auto 0;
            border-radius: 2px;
        }

        /* --- Navigation --- */
        nav {
            position: fixed;
            top: 0;
            width: 100%;
            background: rgba(26, 27, 38, 0.9);
            backdrop-filter: blur(10px);
            z-index: 1000;
            padding: 1rem 0;
            border-bottom: 1px solid rgba(255,255,255,0.05);
        }

        .nav-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            font-weight: 800;
            font-size: 1.5rem;
            color: var(--accent-cyan);
            text-decoration: none;
            letter-spacing: 1px;
        }

        .nav-links a {
            color: var(--text-primary);
            text-decoration: none;
            margin-left: 2rem;
            font-weight: 500;
            transition: color var(--transition-speed);
        }

        .nav-links a:hover {
            color: var(--accent-magenta);
        }

        /* --- Hero Section --- */
        #hero {
            height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            position: relative;
            padding-top: 60px;
        }

        .hero-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 2rem;
            align-items: center;
        }

        .hero-text h1 {
            font-size: 3.5rem;
            line-height: 1.1;
            margin-bottom: 1rem;
        }

        .hero-text h2 {
            font-family: 'Fira Code', monospace;
            font-size: 1.5rem;
            color: var(--accent-green);
            margin-bottom: 2rem;
        }

        .typing-cursor {
            display: inline-block;
            width: 10px;
            background-color: var(--accent-green);
            animation: blink 1s infinite;
        }

        @keyframes blink {
            0%, 100% { opacity: 1; }
            50% { opacity: 0; }
        }

        .btn {
            display: inline-block;
            padding: 12px 30px;
            background: linear-gradient(45deg, var(--accent-cyan), var(--accent-magenta));
            color: #fff;
            text-decoration: none;
            border-radius: 30px;
            font-weight: 600;
            box-shadow: 0 4px 15px rgba(122, 162, 247, 0.3);
            transition: transform 0.2s, box-shadow 0.2s;
        }

        .btn:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 25px rgba(187, 154, 247, 0.4);
        }

        .hero-img-container {
            display: flex;
            justify-content: center;
            position: relative;
        }

        .hero-img {
            width: 350px;
            height: 350px;
            object-fit: cover;
            border-radius: 20px;
            /* Using the GIF provided */
            content: url('https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExcXQzcDR0dW9xcnZxeHM5cTJybnY1MHRtNm1jYnZ5b2RicTltaDY2MSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/qgQUggAC3Pfv687qPC/giphy.gif');
            background: var(--card-bg);
            box-shadow: 0 0 30px rgba(122, 162, 247, 0.2);
            animation: float 6s ease-in-out infinite;
            border: 2px solid rgba(255,255,255,0.1);
        }

        @keyframes float {
            0% { transform: translateY(0px); }
            50% { transform: translateY(-20px); }
            100% { transform: translateY(0px); }
        }

        /* --- Skills Section --- */
        #skills {
            padding: 6rem 0;
        }

        .skills-grid {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 2rem;
        }

        .skill-card {
            background: var(--card-bg);
            padding: 1.5rem 2rem;
            border-radius: 15px;
            display: flex;
            flex-direction: column;
            align-items: center;
            transition: transform 0.3s, border-color 0.3s;
            border: 1px solid rgba(255,255,255,0.05);
            width: 140px;
        }

        .skill-card:hover {
            transform: translateY(-10px);
            border-color: var(--accent-cyan);
            box-shadow: 0 10px 20px rgba(0,0,0,0.3);
        }

        .skill-card img {
            width: 60px;
            height: 60px;
            margin-bottom: 1rem;
            transition: transform 0.3s;
        }

        .skill-card:hover img {
            transform: scale(1.1);
        }

        .skill-name {
            font-weight: 600;
            font-size: 0.9rem;
        }

        /* --- Projects Section --- */
        #projects {
            padding: 6rem 0;
            background: rgba(0,0,0,0.1);
        }

        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 2.5rem;
        }

        .project-card {
            background: var(--card-bg);
            border-radius: 20px;
            overflow: hidden;
            border: 1px solid rgba(255,255,255,0.05);
            transition: transform 0.4s, box-shadow 0.4s;
            position: relative;
        }

        .project-card:hover {
            transform: translateY(-10px) scale(1.02);
            box-shadow: 0 20px 40px rgba(0,0,0,0.4);
        }

        .project-img {
            width: 100%;
            height: 200px;
            background-color: #2a2e40;
            display: flex;
            align-items: center;
            justify-content: center;
            overflow: hidden;
        }

        .project-img img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.5s;
        }

        .project-card:hover .project-img img {
            transform: scale(1.1);
        }

        .project-content {
            padding: 2rem;
        }

        .project-title {
            font-size: 1.5rem;
            margin-bottom: 0.5rem;
            color: var(--accent-cyan);
        }

        .project-desc {
            color: var(--text-secondary);
            font-size: 0.95rem;
            margin-bottom: 1.5rem;
        }

        .tags {
            display: flex;
            gap: 10px;
            flex-wrap: wrap;
        }

        .tag {
            font-size: 0.8rem;
            padding: 5px 12px;
            border-radius: 15px;
            background: rgba(122, 162, 247, 0.1);
            color: var(--accent-cyan);
            font-family: 'Fira Code', monospace;
        }

        /* --- Learning Section --- */
        #learning {
            padding: 6rem 0;
            text-align: center;
        }

        .learning-container {
            display: inline-flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 1.5rem;
            background: linear-gradient(135deg, rgba(255,255,255,0.03), rgba(255,255,255,0.01));
            padding: 3rem;
            border-radius: 20px;
            border: 1px dashed var(--accent-magenta);
        }

        .learning-item {
            display: flex;
            align-items: center;
            gap: 10px;
            font-size: 1.2rem;
            font-weight: 600;
            color: var(--text-primary);
        }

        .learning-item::before {
            content: '🚀';
        }

        /* --- Stats Section --- */
        #stats {
            padding: 4rem 0 6rem;
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        .stats-wrapper {
            display: flex;
            gap: 20px;
            flex-wrap: wrap;
            justify-content: center;
            opacity: 0;
            transform: translateY(20px);
            transition: opacity 0.8s ease-out, transform 0.8s ease-out;
        }

        .stats-wrapper.visible {
            opacity: 1;
            transform: translateY(0);
        }

        .stats-wrapper img {
            border-radius: 10px;
            border: 1px solid rgba(255,255,255,0.1);
            max-width: 100%;
        }

        /* --- Connect / Footer --- */
        footer {
            background: var(--card-bg);
            padding: 4rem 0 2rem;
            text-align: center;
            border-top: 1px solid rgba(255,255,255,0.05);
        }

        .social-links {
            display: flex;
            justify-content: center;
            gap: 2rem;
            margin-bottom: 2rem;
        }

        .social-btn {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            background: rgba(255,255,255,0.05);
            display: flex;
            align-items: center;
            justify-content: center;
            transition: all 0.3s;
            border: 1px solid rgba(255,255,255,0.1);
        }

        .social-btn img {
            width: 24px;
            height: 24px;
            filter: invert(1) sepia(1) saturate(0) hue-rotate(180deg); /* Make white/light */
            opacity: 0.7;
            transition: opacity 0.3s;
        }

        .social-btn:hover {
            background: var(--accent-cyan);
            transform: rotate(360deg);
        }

        .social-btn:hover img {
            opacity: 1;
            filter: none;
        }

        /* --- Animations on Scroll --- */
        .hidden-el {
            opacity: 0;
            transform: translateY(30px);
            transition: all 0.8s ease-out;
        }

        .show-el {
            opacity: 1;
            transform: translateY(0);
        }

        /* --- Responsive --- */
        @media (max-width: 768px) {
            .hero-grid {
                grid-template-columns: 1fr;
                text-align: center;
            }

            .hero-text h1 {
                font-size: 2.5rem;
            }

            .hero-img-container {
                margin-top: 2rem;
            }
            
            .hero-img {
                width: 250px;
                height: 250px;
            }

            .section-title {
                font-size: 2rem;
            }
        }
    </style>
</head>
<body>

    <!-- Interactive Background -->
    <canvas id="bg-canvas"></canvas>

    <!-- Navigation -->
    <nav>
        <div class="container nav-content">
            <a href="#" class="logo">&lt;Nadeesh/&gt;</a>
            <div class="nav-links">
                <a href="#projects">Projects</a>
                <a href="#skills">Skills</a>
                <a href="#contact">Contact</a>
            </div>
        </div>
    </nav>

    <!-- Hero Section -->
    <section id="hero">
        <div class="container hero-grid">
            <div class="hero-text hidden-el">
                <h3>Hi 👋, I'm</h3>
                <h1>Nadeesh</h1>
                <h2><span id="typewriter"></span><span class="typing-cursor"></span></h2>
                <p style="color: var(--text-secondary); margin-bottom: 2rem; max-width: 500px;">
                    Building scalable backend systems and interactive web experiences. Passionate about clean code and modern architecture.
                </p>
                <a href="#projects" class="btn">View My Work</a>
            </div>
            <div class="hero-img-container hidden-el">
                <!-- The GIF provided in the prompt -->
                <div class="hero-img"></div>
            </div>
        </div>
    </section>

    <!-- Skills Section -->
    <section id="skills">
        <div class="container">
            <h2 class="section-title hidden-el">Tech Stack</h2>
            <div class="skills-grid hidden-el">
                <!-- HTML5 -->
                <div class="skill-card">
                    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/html5/html5-original-wordmark.svg" alt="HTML5">
                    <span class="skill-name">HTML5</span>
                </div>
                <!-- CSS3 -->
                <div class="skill-card">
                    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/css3/css3-original-wordmark.svg" alt="CSS3">
                    <span class="skill-name">CSS3</span>
                </div>
                <!-- Java -->
                <div class="skill-card">
                    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/java/java-original-wordmark.svg" alt="Java">
                    <span class="skill-name">Java</span>
                </div>
                <!-- JavaScript -->
                <div class="skill-card">
                    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/javascript/javascript-original.svg" alt="JavaScript">
                    <span class="skill-name">JavaScript</span>
                </div>
                <!-- Python -->
                <div class="skill-card">
                    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/python/python-original-wordmark.svg" alt="Python">
                    <span class="skill-name">Python</span>
                </div>
            </div>
        </div>
    </section>

    <!-- Projects Section -->
    <section id="projects">
        <div class="container">
            <h2 class="section-title hidden-el">Projects</h2>
            <div class="projects-grid">
                
                <!-- Project 1 -->
                <article class="project-card hidden-el">
                    <div class="project-img">
                        <img src="https://picsum.photos/seed/library/600/400" alt="Library Help Desk">
                    </div>
                    <div class="project-content">
                        <h3 class="project-title">Library Help Desk</h3>
                        <p class="project-desc">A comprehensive management system for libraries to track books, manage user requests, and handle inquiries efficiently.</p>
                        <div class="tags">
                            <span class="tag">Java</span>
                            <span class="tag">Spring Boot</span>
                            <span class="tag">MySQL</span>
                        </div>
                    </div>
                </article>

                <!-- Project 2 -->
                <article class="project-card hidden-el" style="transition-delay: 0.1s;">
                    <div class="project-img">
                        <img src="https://picsum.photos/seed/property/600/400" alt="Property Selling Web">
                    </div>
                    <div class="project-content">
                        <h3 class="project-title">Property Selling Web</h3>
                        <p class="project-desc">A dynamic platform for real estate agents to list properties, featuring image galleries and search filters.</p>
                        <div class="tags">
                            <span class="tag">JavaScript</span>
                            <span class="tag">HTML/CSS</span>
                            <span class="tag">API</span>
                        </div>
                    </div>
                </article>

            </div>
        </div>
    </section>

    <!-- Learning Section -->
    <section id="learning">
        <div class="container hidden-el">
            <h2 class="section-title">What I'm Learning</h2>
            <div class="learning-container">
                <div class="learning-item">Spring Boot</div>
                <div class="learning-item">Advanced Java</div>
                <div class="learning-item">Kotlin</div>
            </div>
        </div>
    </section>

    <!-- GitHub Stats Section -->
    <section id="stats">
        <div class="container">
            <h2 class="section-title hidden-el">GitHub Stats</h2>
            <div class="stats-wrapper" id="stats-wrapper">
                <!-- Stats images from prompt -->
                <img 
                    src="https://github-readme-stats.vercel.app/api?username=naadesh369x&show_icons=true&theme=tokyonight&hide_border=true&count_private=true&include_all_commits=true" 
                    alt="Nadeesh's GitHub Stats"
                />
                <img 
                    src="https://github-readme-stats.vercel.app/api/top-langs/?username=naadesh369x&layout=compact&theme=tokyonight&hide_border=true" 
                    alt="Top Languages"
                />
            </div>
        </div>
    </section>

    <!-- Connect / Footer -->
    <footer id="contact">
        <div class="container">
            <h2 class="section-title">Connect With Me</h2>
            <div class="social-links">
                <a href="https://www.linkedin.com/in/YOUR_LINKEDIN_USERNAME" target="_blank" class="social-btn" aria-label="LinkedIn">
                    <img src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/linked-in-alt.svg" alt="LinkedIn">
                </a>
                <a href="mailto:your-email@gmail.com" class="social-btn" aria-label="Email">
                    <img src="https://cdn-icons-png.flaticon.com/512/281/281769.png" alt="Email">
                </a>
            </div>
            <p style="color: var(--text-secondary); font-size: 0.9rem;">
                &copy; 2023 Nadeesh. All rights reserved. <br>
                Designed with ❤️ and Code.
            </p>
        </div>
    </footer>

    <script>
        // --- 1. Typewriter Effect ---
        const textElement = document.getElementById('typewriter');
        const texts = ["Java Developer", "Backend Enthusiast", "Problem Solver"];
        let count = 0;
        let index = 0;
        let currentText = "";
        let letter = "";
        let isDeleting = false;

        (function type() {
            if (count === texts.length) {
                count = 0;
            }
            currentText = texts[count];

            if (isDeleting) {
                letter = currentText.slice(0, --index);
            } else {
                letter = currentText.slice(0, ++index);
            }

            textElement.textContent = letter;

            let typeSpeed = 100;
            if (isDeleting) typeSpeed /= 2;

            if (!isDeleting && letter.length === currentText.length) {
                typeSpeed = 2000; // Pause at end
                isDeleting = true;
            } else if (isDeleting && letter.length === 0) {
                isDeleting = false;
                count++;
                typeSpeed = 500;
            }

            setTimeout(type, typeSpeed);
        })();

        // --- 2. Scroll Animations (Intersection Observer) ---
        const observerOptions = {
            threshold: 0.1
        };

        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('show-el');
                    
                    // Specific check for stats wrapper to trigger image load animation if needed
                    if(entry.target.id === 'stats-wrapper') {
                        entry.target.classList.add('visible');
                    }
                    
                    observer.unobserve(entry.target);
                }
            });
        }, observerOptions);

        document.querySelectorAll('.hidden-el, #stats-wrapper').forEach((el) => {
            observer.observe(el);
        });

        // --- 3. Interactive Particle Background (Canvas) ---
        const canvas = document.getElementById('bg-canvas');
        const ctx = canvas.getContext('2d');
        
        let width, height;
        let particles = [];
        
        // Resize handling
        function resize() {
            width = canvas.width = window.innerWidth;
            height = canvas.height = window.innerHeight;
        }
        window.addEventListener('resize', resize);
        resize();

        // Mouse tracking
        const mouse = { x: null, y: null };
        window.addEventListener('mousemove', (e) => {
            mouse.x = e.x;
            mouse.y = e.y;
        });

        // Particle Class
        class Particle {
            constructor() {
                this.x = Math.random() * width;
                this.y = Math.random() * height;
                this.vx = (Math.random() - 0.5) * 0.5;
                this.vy = (Math.random() - 0.5) * 0.5;
                this.size = Math.random() * 2 + 1;
                this.color = '#7aa2f7'; // Cyan accent
            }

            update() {
                this.x += this.vx;
                this.y += this.vy;

                // Bounce off edges
                if (this.x < 0 || this.x > width) this.vx *= -1;
                if (this.y < 0 || this.y > height) this.vy *= -1;

                // Mouse interaction
                let dx = mouse.x - this.x;
                let dy = mouse.y - this.y;
                let distance = Math.sqrt(dx * dx + dy * dy);
                if (distance < 150) {
                    const angle = Math.atan2(dy, dx);
                    const force = (150 - distance) / 150;
                    const push = force * 0.5;
                    this.vx -= Math.cos(angle) * push * 0.5;
                    this.vy -= Math.sin(angle) * push * 0.5;
                }
            }

            draw() {
                ctx.beginPath();
                ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
                ctx.fillStyle = this.color;
                ctx.fill();
            }
        }

        // Init Particles
        function initParticles() {
            particles = [];
            const particleCount = Math.min(window.innerWidth / 10, 100); // Responsive count
            for (let i = 0; i < particleCount; i++) {
                particles.push(new Particle());
            }
        }
        initParticles();

        // Animation Loop
        function animate() {
            ctx.clearRect(0, 0, width, height);
            
            particles.forEach(p => {
                p.update();
                p.draw();
            });
            
            // Draw connections
            connect();
            requestAnimationFrame(animate);
        }

        function connect() {
            for (let a = 0; a < particles.length; a++) {
                for (let b = a; b < particles.length; b++) {
                    let dx = particles[a].x - particles[b].x;
                    let dy = particles[a].y - particles[b].y;
                    let distance = Math.sqrt(dx * dx + dy * dy);

                    if (distance < 120) {
                        ctx.strokeStyle = `rgba(122, 162, 247, ${1 - distance/120})`;
                        ctx.lineWidth = 1;
                        ctx.beginPath();
                        ctx.moveTo(particles[a].x, particles[a].y);
                        ctx.lineTo(particles[b].x, particles[b].y);
                        ctx.stroke();
                    }
                }
            }
        }

        animate();

    </script>
</body>
</html>
