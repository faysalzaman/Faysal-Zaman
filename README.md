<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Portfolio Showcase</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: #fff;
            line-height: 1.6;
            overflow-x: hidden;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 40px 20px;
        }

        .header {
            text-align: center;
            margin-bottom: 60px;
            animation: fadeInDown 1s ease;
        }

        .header h1 {
            font-size: 3em;
            margin-bottom: 10px;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
        }

        .header p {
            font-size: 1.2em;
            opacity: 0.9;
        }

        .projects-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
            gap: 30px;
            margin-bottom: 60px;
        }

        .project-card {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 30px;
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
            border: 1px solid rgba(255, 255, 255, 0.2);
            position: relative;
            overflow: hidden;
            animation: fadeInUp 0.8s ease forwards;
            opacity: 0;
        }

        .project-card:nth-child(1) { animation-delay: 0.1s; }
        .project-card:nth-child(2) { animation-delay: 0.2s; }
        .project-card:nth-child(3) { animation-delay: 0.3s; }
        .project-card:nth-child(4) { animation-delay: 0.4s; }
        .project-card:nth-child(5) { animation-delay: 0.5s; }
        .project-card:nth-child(6) { animation-delay: 0.6s; }
        .project-card:nth-child(7) { animation-delay: 0.7s; }
        .project-card:nth-child(8) { animation-delay: 0.8s; }

        .project-card::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.2), transparent);
            transition: left 0.5s;
        }

        .project-card:hover::before {
            left: 100%;
        }

        .project-card:hover {
            transform: translateY(-10px) scale(1.02);
            box-shadow: 0 20px 40px rgba(0,0,0,0.3);
            border-color: rgba(255, 255, 255, 0.4);
        }

        .project-icon {
            font-size: 3em;
            margin-bottom: 15px;
            display: inline-block;
            animation: bounce 2s infinite;
        }

        .project-card h3 {
            font-size: 1.5em;
            margin-bottom: 15px;
            color: #fff;
        }

        .project-card p {
            margin-bottom: 20px;
            opacity: 0.9;
            line-height: 1.6;
        }

        .project-link {
            display: inline-flex;
            align-items: center;
            gap: 8px;
            padding: 12px 24px;
            background: rgba(255, 255, 255, 0.2);
            border: 2px solid rgba(255, 255, 255, 0.3);
            border-radius: 50px;
            color: #fff;
            text-decoration: none;
            transition: all 0.3s ease;
            font-weight: 600;
        }

        .project-link:hover {
            background: rgba(255, 255, 255, 0.3);
            border-color: #fff;
            transform: scale(1.05);
        }

        .skills-section {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border-radius: 20px;
            padding: 40px;
            border: 1px solid rgba(255, 255, 255, 0.2);
            animation: fadeInUp 1s ease;
        }

        .skills-section h2 {
            font-size: 2.5em;
            margin-bottom: 30px;
            text-align: center;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
        }

        .skills-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 25px;
        }

        .skill-category {
            background: rgba(255, 255, 255, 0.1);
            padding: 25px;
            border-radius: 15px;
            border: 1px solid rgba(255, 255, 255, 0.2);
            transition: all 0.3s ease;
        }

        .skill-category:hover {
            background: rgba(255, 255, 255, 0.15);
            transform: translateY(-5px);
        }

        .skill-category h3 {
            font-size: 1.4em;
            margin-bottom: 15px;
            color: #ffd700;
        }

        .skill-tags {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
        }

        .skill-tag {
            background: rgba(255, 255, 255, 0.2);
            padding: 8px 16px;
            border-radius: 20px;
            font-size: 0.9em;
            border: 1px solid rgba(255, 255, 255, 0.3);
            transition: all 0.3s ease;
        }

        .skill-tag:hover {
            background: rgba(255, 255, 255, 0.3);
            transform: scale(1.1);
        }

        @keyframes fadeInDown {
            from {
                opacity: 0;
                transform: translateY(-30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(30px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes bounce {
            0%, 100% {
                transform: translateY(0);
            }
            50% {
                transform: translateY(-10px);
            }
        }

        @media (max-width: 768px) {
            .header h1 {
                font-size: 2em;
            }

            .projects-grid {
                grid-template-columns: 1fr;
            }

            .skills-grid {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>✨ Portfolio Showcase</h1>
            <p>Crafting Digital Experiences with Passion & Precision</p>
        </div>

        <div class="projects-grid">
            <div class="project-card">
                <div class="project-icon">📦</div>
                <h3>Picker App</h3>
                <p>Efficiently manage customer requests with this powerful tool designed for seamless workflow optimization.</p>
                <a href="https://play.google.com/store/apps/details?id=com.nartec.solitaire_picker" class="project-link" target="_blank">
                    <span>Download</span>
                    <span>→</span>
                </a>
            </div>

            <div class="project-card">
                <div class="project-icon">🏗</div>
                <h3>FATS System</h3>
                <p>Fixed Asset Tracking System for comprehensive company asset management with real-time monitoring capabilities.</p>
                <a href="https://play.google.com/store/apps/details?id=com.nartec.fats_system" class="project-link" target="_blank">
                    <span>View App</span>
                    <span>→</span>
                </a>
            </div>

            <div class="project-card">
                <div class="project-icon">🌐</div>
                <h3>CyberNexus</h3>
                <p>Modern React.js web application built with Vite & Tailwind for a dynamic drop-shipping business platform.</p>
                <a href="https://www.cybernexusllc.us/" class="project-link" target="_blank">
                    <span>Live Site</span>
                    <span>→</span>
                </a>
            </div>

            <div class="project-card">
                <div class="project-icon">📖</div>
                <h3>20,000+ Islamic Names (Urdu)</h3>
                <p>Comprehensive collection of Islamic names with detailed meanings in English & Urdu for parents and enthusiasts.</p>
                <a href="https://play.google.com/store/apps/details?id=com.namesapp.islamic_names_dictionary" class="project-link" target="_blank">
                    <span>Download</span>
                    <span>→</span>
                </a>
            </div>

            <div class="project-card">
                <div class="project-icon">📖</div>
                <h3>Arabic Names Collection</h3>
                <p>Extensive database of 20,000+ boys and girls names with meanings tailored for Arabic-speaking communities.</p>
                <a href="https://play.google.com/store/apps/details?id=com.sairatec.arabic_names" class="project-link" target="_blank">
                    <span>Download</span>
                    <span>→</span>
                </a>
            </div>

            <div class="project-card">
                <div class="project-icon">🏋</div>
                <h3>Motions Academy</h3>
                <p>Professional physiotherapy app featuring video-guided exercises for injury recovery and rehabilitation.</p>
                <a href="https://apps.apple.com/us/app/motions-academy/id6630384351?platform=iphone" class="project-link" target="_blank">
                    <span>App Store</span>
                    <span>→</span>
                </a>
            </div>

            <div class="project-card">
                <div class="project-icon">🍽️</div>
                <h3>Food Ordering App</h3>
                <p>Multi-category food ordering platform with Node.js backend and Flutter frontend for seamless dining experience.</p>
                <a href="#" class="project-link" style="opacity: 0.7; cursor: default;">
                    <span>In Development</span>
                </a>
            </div>

            <div class="project-card">
                <div class="project-icon">🔍</div>
                <h3>Just Search 8</h3>
                <p>Global B2B marketplace platform connecting suppliers and buyers worldwide, similar to Alibaba's ecosystem.</p>
                <a href="#" class="project-link" style="opacity: 0.7; cursor: default;">
                    <span>Coming Soon</span>
                </a>
            </div>
        </div>

        <div class="skills-section">
            <h2>🚀 Skills & Expertise</h2>
            <div class="skills-grid">
                <div class="skill-category">
                    <h3>Mobile Development</h3>
                    <div class="skill-tags">
                        <span class="skill-tag">Flutter</span>
                        <span class="skill-tag">Dart</span>
                        <span class="skill-tag">Firebase</span>
                        <span class="skill-tag">BLoC</span>
                        <span class="skill-tag">Provider</span>
                        <span class="skill-tag">API Integration</span>
                    </div>
                </div>

                <div class="skill-category">
                    <h3>Web Development</h3>
                    <div class="skill-tags">
                        <span class="skill-tag">React.js</span>
                        <span class="skill-tag">Vite</span>
                        <span class="skill-tag">Tailwind</span>
                        <span class="skill-tag">JavaScript</span>
                        <span class="skill-tag">HTML/CSS</span>
                        <span class="skill-tag">Bootstrap</span>
                    </div>
                </div>

                <div class="skill-category">
                    <h3>Backend & Database</h3>
                    <div class="skill-tags">
                        <span class="skill-tag">Node.js</span>
                        <span class="skill-tag">Firebase Firestore</span>
                        <span class="skill-tag">Local Storage</span>
                        <span class="skill-tag">RevenueCat</span>
                    </div>
                </div>

                <div class="skill-category">
                    <h3>Hardware Integration</h3>
                    <div class="skill-tags">
                        <span class="skill-tag">NFC</span>
                        <span class="skill-tag">QR Scanning</span>
                        <span class="skill-tag">Google Maps</span>
                        <span class="skill-tag">Camera</span>
                        <span class="skill-tag">Bluetooth</span>
                    </div>
                </div>

                <div class="skill-category">
                    <h3>UI/UX Design</h3>
                    <div class="skill-tags">
                        <span class="skill-tag">Figma to Flutter</span>
                        <span class="skill-tag">Pixel-Perfect</span>
                        <span class="skill-tag">Animations</span>
                        <span class="skill-tag">Responsive Design</span>
                    </div>
                </div>

                <div class="skill-category">
                    <h3>Tools & Collaboration</h3>
                    <div class="skill-tags">
                        <span class="skill-tag">Git</span>
                        <span class="skill-tag">GitHub</span>
                        <span class="skill-tag">Bitbucket</span>
                        <span class="skill-tag">Agile</span>
                        <span class="skill-tag">App Publishing</span>
                    </div>
                </div>
            </div>
        </div>
    </div>
</body>
</html>
