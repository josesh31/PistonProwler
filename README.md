<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Auto Evolution | Classic & Modern Cars</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        :root {
            --modern-color: #1a73e8;
            --classic-color: #d32f2f;
            --light-bg: #f8f9fa;
            --dark-text: #202124;
            --light-text: #5f6368;
            --card-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
            --transition: all 0.3s ease;
        }

        body {
            background-color: var(--light-bg);
            color: var(--dark-text);
            line-height: 1.6;
        }

        /* Header */
        header {
            background: linear-gradient(135deg, var(--dark-text) 0%, #3c4043 100%);
            color: white;
            padding: 2rem 1rem;
            text-align: center;
            position: relative;
            overflow: hidden;
        }

        header::before {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: url('data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" width="100" height="100" viewBox="0 0 100 100"><path d="M20,40 Q50,10 80,40 T100,60" stroke="rgba(255,255,255,0.05)" fill="none" stroke-width="2"/><path d="M0,70 Q30,40 60,70 T90,80" stroke="rgba(255,255,255,0.05)" fill="none" stroke-width="2"/></svg>');
            opacity: 0.3;
        }

        .logo {
            font-size: 2.8rem;
            font-weight: 700;
            margin-bottom: 0.5rem;
            position: relative;
            z-index: 1;
        }

        .logo span {
            color: var(--modern-color);
        }

        .tagline {
            font-size: 1.2rem;
            opacity: 0.9;
            max-width: 600px;
            margin: 0 auto 1.5rem;
            position: relative;
            z-index: 1;
        }

        /* Navigation */
        nav {
            display: flex;
            justify-content: center;
            background-color: white;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
            position: sticky;
            top: 0;
            z-index: 100;
        }

        .nav-container {
            display: flex;
            max-width: 1200px;
            width: 100%;
            justify-content: space-between;
            padding: 0 1rem;
        }

        .nav-links {
            display: flex;
            list-style: none;
        }

        .nav-links li {
            margin: 0;
        }

        .nav-links a {
            display: block;
            padding: 1rem 1.5rem;
            text-decoration: none;
            color: var(--dark-text);
            font-weight: 600;
            transition: var(--transition);
            border-bottom: 3px solid transparent;
        }

        .nav-links a:hover, .nav-links a.active {
            color: var(--modern-color);
            border-bottom: 3px solid var(--modern-color);
        }

        .time-period-selector {
            display: flex;
            align-items: center;
            gap: 1rem;
        }

        .time-period-selector button {
            padding: 0.5rem 1.5rem;
            border: none;
            background: var(--light-bg);
            border-radius: 30px;
            font-weight: 600;
            cursor: pointer;
            transition: var(--transition);
        }

        .time-period-selector button.active {
            background: var(--modern-color);
            color: white;
        }

        .time-period-selector button:nth-child(2).active {
            background: var(--classic-color);
        }

        /* Main Content */
        .container {
            max-width: 1200px;
            margin: 2rem auto;
            padding: 0 1rem;
        }

        .section-title {
            text-align: center;
            margin-bottom: 2.5rem;
            position: relative;
        }

        .section-title h2 {
            font-size: 2.2rem;
            display: inline-block;
            padding-bottom: 0.5rem;
        }

        .section-title h2::after {
            content: '';
            position: absolute;
            width: 80px;
            height: 4px;
            background: var(--modern-color);
            bottom: 0;
            left: 50%;
            transform: translateX(-50%);
        }

        .classic-title h2::after {
            background: var(--classic-color);
        }

        /* Car Cards */
        .car-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            gap: 2rem;
            margin-bottom: 3rem;
        }

        .car-card {
            background: white;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: var(--card-shadow);
            transition: var(--transition);
        }

        .car-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 12px 20px rgba(0, 0, 0, 0.15);
        }

        .car-img {
            height: 200px;
            overflow: hidden;
        }

        .car-img img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: var(--transition);
        }

        .car-card:hover .car-img img {
            transform: scale(1.05);
        }

        .car-info {
            padding: 1.5rem;
        }

        .car-year {
            display: inline-block;
            padding: 0.3rem 0.8rem;
            border-radius: 20px;
            font-size: 0.9rem;
            font-weight: 600;
            margin-bottom: 0.8rem;
        }

        .modern-year {
            background-color: rgba(26, 115, 232, 0.1);
            color: var(--modern-color);
        }

        .classic-year {
            background-color: rgba(211, 47, 47, 0.1);
            color: var(--classic-color);
        }

        .car-info h3 {
            font-size: 1.4rem;
            margin-bottom: 0.5rem;
        }

        .car-info p {
            color: var(--light-text);
            margin-bottom: 1.2rem;
            font-size: 0.95rem;
        }

        .car-specs {
            display: flex;
            justify-content: space-between;
            font-size: 0.9rem;
            border-top: 1px solid #eee;
            padding-top: 1rem;
        }

        .spec {
            text-align: center;
        }

        .spec i {
            display: block;
            font-size: 1.2rem;
            margin-bottom: 0.3rem;
            color: var(--modern-color);
        }

        .classic-card .spec i {
            color: var(--classic-color);
        }

        /* Comparison Section */
        .comparison {
            background: white;
            border-radius: 10px;
            padding: 2rem;
            box-shadow: var(--card-shadow);
            margin-bottom: 3rem;
        }

        .comparison-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 2rem;
            margin-top: 2rem;
        }

        .comparison-item {
            padding: 1.5rem;
            border-radius: 8px;
            transition: var(--transition);
        }

        .comparison-item:hover {
            transform: translateY(-5px);
        }

        .modern-comparison {
            border-top: 4px solid var(--modern-color);
            background-color: rgba(26, 115, 232, 0.05);
        }

        .classic-comparison {
            border-top: 4px solid var(--classic-color);
            background-color: rgba(211, 47, 47, 0.05);
        }

        .comparison-item h3 {
            font-size: 1.3rem;
            margin-bottom: 1rem;
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }

        .comparison-item ul {
            list-style-position: inside;
            color: var(--light-text);
        }

        .comparison-item li {
            margin-bottom: 0.5rem;
        }

        /* Footer */
        footer {
            background-color: var(--dark-text);
            color: white;
            padding: 3rem 1rem 1.5rem;
            text-align: center;
        }

        .footer-content {
            max-width: 1200px;
            margin: 0 auto;
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 2rem;
            margin-bottom: 2rem;
        }

        .footer-section h3 {
            font-size: 1.3rem;
            margin-bottom: 1.2rem;
            color: white;
        }

        .footer-section p {
            opacity: 0.8;
            margin-bottom: 1rem;
        }

        .social-icons {
            display: flex;
            justify-content: center;
            gap: 1rem;
            margin-top: 1rem;
        }

        .social-icons a {
            display: inline-flex;
            align-items: center;
            justify-content: center;
            width: 40px;
            height: 40px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 50%;
            color: white;
            text-decoration: none;
            transition: var(--transition);
        }

        .social-icons a:hover {
            background: var(--modern-color);
            transform: translateY(-3px);
        }

        .copyright {
            padding-top: 1.5rem;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
            opacity: 0.7;
            font-size: 0.9rem;
        }

        /* Responsive Design */
        @media (max-width: 768px) {
            .nav-container {
                flex-direction: column;
                align-items: center;
                padding: 0.5rem;
            }

            .nav-links {
                margin-bottom: 1rem;
            }

            .car-grid {
                grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
            }

            .logo {
                font-size: 2.2rem;
            }

            .section-title h2 {
                font-size: 1.8rem;
            }
        }

        @media (max-width: 480px) {
            .nav-links {
                flex-wrap: wrap;
                justify-content: center;
            }

            .nav-links a {
                padding: 0.8rem 1rem;
                font-size: 0.9rem;
            }

            .time-period-selector {
                flex-direction: column;
                width: 100%;
            }

            .time-period-selector button {
                width: 100%;
            }

            .car-grid {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <!-- Header -->
    <header>
        <div class="logo">Auto<span>Evolution</span></div>
        <p class="tagline">Explore the journey of automotive engineering from timeless classics to cutting-edge modern marvels</p>
    </header>

    <!-- Navigation -->
    <nav>
        <div class="nav-container">
            <ul class="nav-links">
                <li><a href="#" class="active">Home</a></li>
                <li><a href="#modern">Modern Cars</a></li>
                <li><a href="#classic">Classic Cars</a></li>
                <li><a href="#comparison">Comparison</a></li>
            </ul>
            <div class="time-period-selector">
                <button id="showAll" class="active">All Cars</button>
                <button id="toggleView">Show Classics Only</button>
            </div>
        </div>
    </nav>

    <!-- Main Content -->
    <div class="container">
        <!-- Modern Cars Section -->
        <section id="modern">
            <div class="section-title">
                <h2>Modern Cars</h2>
            </div>
            <div class="car-grid">
                <!-- Modern Car 1 -->
                <div class="car-card modern-card">
                    <div class="car-img">
                        <img src="https://images.unsplash.com/photo-1549399542-7e3f8b79c341?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=800&q=80" alt="Tesla Model S">
                    </div>
                    <div class="car-info">
                        <span class="car-year modern-year">2023</span>
                        <h3>Tesla Model S Plaid</h3>
                        <p>All-electric luxury sedan with groundbreaking acceleration, autonomous driving capabilities, and a minimalist interior design.</p>
                        <div class="car-specs">
                            <div class="spec">
                                <i class="fas fa-bolt"></i>
                                <span>1,020 hp</span>
                            </div>
                            <div class="spec">
                                <i class="fas fa-tachometer-alt"></i>
                                <span>200 mph</span>
                            </div>
                            <div class="spec">
                                <i class="fas fa-charging-station"></i>
                                <span>396 mi</span>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Modern Car 2 -->
                <div class="car-card modern-card">
                    <div class="car-img">
                        <img src="https://images.unsplash.com/photo-1553440569-bcc63803a83d?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=800&q=80" alt="Porsche Taycan">
                    </div>
                    <div class="car-info">
                        <span class="car-year modern-year">2023</span>
                        <h3>Porsche Taycan Turbo S</h3>
                        <p>High-performance electric sports sedan combining Porsche's legendary handling with zero-emission driving.</p>
                        <div class="car-specs">
                            <div class="spec">
                                <i class="fas fa-bolt"></i>
                                <span>750 hp</span>
                            </div>
                            <div class="spec">
                                <i class="fas fa-tachometer-alt"></i>
                                <span>162 mph</span>
                            </div>
                            <div class="spec">
                                <i class="fas fa-charging-station"></i>
                                <span>212 mi</span>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Modern Car 3 -->
                <div class="car-card modern-card">
                    <div class="car-img">
                        <img src="https://images.unsplash.com/photo-1555212697-194d092e3b8f?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=800&q=80" alt="Mercedes EQS">
                    </div>
                    <div class="car-info">
                        <span class="car-year modern-year">2023</span>
                        <h3>Mercedes-Benz EQS</h3>
                        <p>Luxury electric vehicle with the innovative Hyperscreen, exceptional range, and unparalleled comfort.</p>
                        <div class="car-specs">
                            <div class="spec">
                                <i class="fas fa-bolt"></i>
                                <span>516 hp</span>
                            </div>
                            <div class="spec">
                                <i class="fas fa-tachometer-alt"></i>
                                <span>130 mph</span>
                            </div>
                            <div class="spec">
                                <i class="fas fa-charging-station"></i>
                                <span>350 mi</span>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Classic Cars Section -->
        <section id="classic">
            <div class="section-title classic-title">
                <h2>Classic Cars</h2>
            </div>
            <div class="car-grid">
                <!-- Classic Car 1 -->
                <div class="car-card classic-card">
                    <div class="car-img">
                        <img src="https://images.unsplash.com/photo-1519641471654-76ce0107ad1b?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=800&q=80" alt="Ford Mustang">
                    </div>
                    <div class="car-info">
                        <span class="car-year classic-year">1967</span>
                        <h3>Ford Mustang Fastback</h3>
                        <p>American muscle car icon with a powerful V8 engine, sleek fastback design, and legendary status in automotive history.</p>
                        <div class="car-specs">
                            <div class="spec">
                                <i class="fas fa-gas-pump"></i>
                                <span>V8 6.4L</span>
                            </div>
                            <div class="spec">
                                <i class="fas fa-tachometer-alt"></i>
                                <span>120 mph</span>
                            </div>
                            <div class="spec">
                                <i class="fas fa-horse"></i>
                                <span>320 hp</span>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Classic Car 2 -->
                <div class="car-card classic-card">
                    <div class="car-img">
                        <img src="https://images.unsplash.com/photo-1593941707882-a5bba5338fe2?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=800&q=80" alt="Chevrolet Corvette">
                    </div>
                    <div class="car-info">
                        <span class="car-year classic-year">1963</span>
                        <h3>Chevrolet Corvette Stingray</h3>
                        <p>Second-generation Corvette with split rear window design, independent rear suspension, and fiberglass body.</p>
                        <div class="car-specs">
                            <div class="spec">
                                <i class="fas fa-gas-pump"></i>
                                <span>V8 5.4L</span>
                            </div>
                            <div class="spec">
                                <i class="fas fa-tachometer-alt"></i>
                                <span>130 mph</span>
                            </div>
                            <div class="spec">
                                <i class="fas fa-horse"></i>
                                <span>360 hp</span>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Classic Car 3 -->
                <div class="car-card classic-card">
                    <div class="car-img">
                        <img src="https://images.unsplash.com/photo-1552519507-da3b142c6e3d?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=800&q=80" alt="Mercedes 300SL">
                    </div>
                    <div class="car-info">
                        <span class="car-year classic-year">1954</span>
                        <h3>Mercedes-Benz 30
