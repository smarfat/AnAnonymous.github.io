
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>An Anonymous - Anonymous Messaging</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary-color: #6c63ff;
            --secondary-color: #4a45b9;
            --accent-color: #ff6b6b;
            --success-color: #2ecc71;
            --warning-color: #f39c12;
            --background-color: #f8f9fa;
            --card-color: #ffffff;
            --text-color: #333333;
            --text-secondary: #6c757d;
            --border-color: #e1e4e8;
            --shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
            --shadow-hover: 0 15px 35px rgba(0, 0, 0, 0.15);
            --gradient-1: linear-gradient(135deg, #6c63ff, #4a45b9);
            --gradient-2: linear-gradient(135deg, #ff6b6b, #ff5252);
            --gradient-3: linear-gradient(135deg, #2ecc71, #27ae60);
        }
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Poppins', sans-serif;
        }
        body {
            background-color: var(--background-color);
            color: var(--text-color);
            line-height: 1.6;
            overflow-x: hidden;
            background-image: 
                radial-gradient(circle at 10% 20%, rgba(108, 99, 255, 0.05) 0%, transparent 20%),
                radial-gradient(circle at 90% 80%, rgba(255, 107, 107, 0.05) 0%, transparent 20%),
                radial-gradient(circle at 50% 50%, rgba(46, 204, 113, 0.05) 0%, transparent 30%);
            background-attachment: fixed;
        }
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }
        /* Animations */
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        @keyframes slideIn {
            from { transform: translateX(-100%); }
            to { transform: translateX(0); }
        }
        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.05); }
            100% { transform: scale(1); }
        }
        @keyframes float {
            0% { transform: translateY(0px); }
            50% { transform: translateY(-10px); }
            100% { transform: translateY(0px); }
        }
        @keyframes gradient {
            0% { background-position: 0% 50%; }
            50% { background-position: 100% 50%; }
            100% { background-position: 0% 50%; }
        }
        .fade-in {
            animation: fadeIn 0.5s ease forwards;
        }
        .slide-in {
            animation: slideIn 0.5s ease forwards;
        }
        .pulse {
            animation: pulse 2s infinite;
        }
        .float {
            animation: float 3s ease-in-out infinite;
        }
        .gradient-animation {
            background-size: 200% 200%;
            animation: gradient 3s ease infinite;
        }
        /* Header Styles */
        header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 20px 0;
            border-bottom: 1px solid var(--border-color);
            position: sticky;
            top: 0;
            background-color: rgba(248, 249, 250, 0.9);
            backdrop-filter: blur(10px);
            z-index: 100;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.05);
        }
        .logo {
            font-size: 28px;
            font-weight: 700;
            background: var(--gradient-1);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        .logo i {
            font-size: 32px;
            background: var(--gradient-1);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }
        .user-info {
            display: flex;
            align-items: center;
            gap: 15px;
        }
        .user-avatar {
            width: 45px;
            height: 45px;
            border-radius: 50%;
            background: var(--gradient-1);
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-weight: bold;
            box-shadow: 0 4px 15px rgba(108, 99, 255, 0.3);
            transition: all 0.3s ease;
        }
        .user-avatar:hover {
            transform: scale(1.1);
            box-shadow: 0 6px 20px rgba(108, 99, 255, 0.4);
        }
        .btn {
            padding: 12px 24px;
            border: none;
            border-radius: 30px;
            cursor: pointer;
            font-weight: 600;
            font-size: 16px;
            transition: all 0.3s ease;
            display: inline-flex;
            align-items: center;
            gap: 10px;
            position: relative;
            overflow: hidden;
            z-index: 1;
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }
        .btn:before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(255, 255, 255, 0.2);
            transform: translateX(-100%);
            transition: transform 0.3s ease;
            z-index: -1;
        }
        .btn:hover:before {
            transform: translateX(0);
        }
        .btn-primary {
            background: var(--gradient-1);
            color: white;
            box-shadow: 0 4px 15px rgba(108, 99, 255, 0.3);
        }
        .btn-primary:hover {
            transform: translateY(-3px);
            box-shadow: 0 6px 20px rgba(108, 99, 255, 0.4);
        }
        .btn-secondary {
            background-color: transparent;
            color: var(--primary-color);
            border: 2px solid var(--primary-color);
        }
        .btn-secondary:hover {
            background-color: rgba(108, 99, 255, 0.1);
            transform: translateY(-3px);
        }
        .btn-accent {
            background: var(--gradient-2);
            color: white;
            box-shadow: 0 4px 15px rgba(255, 107, 107, 0.3);
        }
        .btn-accent:hover {
            transform: translateY(-3px);
            box-shadow: 0 6px 20px rgba(255, 107, 107, 0.4);
        }
        /* Main Content */
        .main-content {
            display: flex;
            margin-top: 30px;
            gap: 30px;
        }
        .left-panel, .right-panel {
            flex: 1;
            background-color: var(--card-color);
            border-radius: 20px;
            padding: 30px;
            box-shadow: var(--shadow);
            transition: all 0.3s ease;
            border: 1px solid rgba(108, 99, 255, 0.1);
        }
        .left-panel:hover, .right-panel:hover {
            box-shadow: var(--shadow-hover);
            transform: translateY(-8px);
            border: 1px solid rgba(108, 99, 255, 0.2);
        }
        .panel-title {
            font-size: 24px;
            margin-bottom: 25px;
            background: var(--gradient-1);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            display: flex;
            align-items: center;
            gap: 12px;
            font-weight: 700;
        }
        .panel-title i {
            font-size: 28px;
            background: var(--gradient-1);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }
        /* Form Styles */
        .form-group {
            margin-bottom: 25px;
        }
        .form-group label {
            display: block;
            margin-bottom: 10px;
            font-weight: 600;
            color: var(--text-secondary);
            font-size: 16px;
        }
        .form-control {
            width: 100%;
            padding: 15px 20px;
            border: 2px solid var(--border-color);
            border-radius: 12px;
            font-size: 16px;
            transition: all 0.3s ease;
            background-color: rgba(248, 249, 250, 0.5);
        }
        .form-control:focus {
            outline: none;
            border-color: var(--primary-color);
            box-shadow: 0 0 0 4px rgba(108, 99, 255, 0.1);
            background-color: white;
        }
        textarea.form-control {
            resize: vertical;
            min-height: 140px;
        }
        /* Message List */
        .message-list {
            margin-top: 25px;
            max-height: 400px;
            overflow-y: auto;
            padding-right: 10px;
        }
        .message-list::-webkit-scrollbar {
            width: 6px;
        }
        .message-list::-webkit-scrollbar-track {
            background: rgba(0, 0, 0, 0.05);
            border-radius: 10px;
        }
        .message-list::-webkit-scrollbar-thumb {
            background: rgba(108, 99, 255, 0.3);
            border-radius: 10px;
        }
        .message-list::-webkit-scrollbar-thumb:hover {
            background: rgba(108, 99, 255, 0.5);
        }
        .message-item {
            padding: 20px;
            border-radius: 15px;
            margin-bottom: 20px;
            background-color: var(--background-color);
            border-left: 5px solid var(--primary-color);
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.03);
        }
        .message-item:hover {
            transform: translateX(8px);
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.08);
        }
        .message-item:before {
            content: '';
            position: absolute;
            top: 0;
            right: 0;
            width: 100px;
            height: 100px;
            background: var(--gradient-1);
            opacity: 0.05;
            border-radius: 50%;
            transform: translate(30px, -30px);
        }
        .message-header {
            display: flex;
            justify-content: space-between;
            margin-bottom: 12px;
            font-size: 14px;
            color: var(--text-secondary);
        }
        .message-sender {
            font-weight: 700;
            color: var(--primary-color);
            font-size: 16px;
        }
        .message-content {
            font-size: 16px;
            line-height: 1.6;
        }
        /* Authentication Styles */
        .auth-container {
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 80vh;
        }
        .auth-card {
            width: 100%;
            max-width: 500px;
            background-color: var(--card-color);
            border-radius: 25px;
            padding: 50px;
            box-shadow: var(--shadow);
            position: relative;
            overflow: hidden;
            border: 1px solid rgba(108, 99, 255, 0.1);
        }
        .auth-card:before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 8px;
            background: var(--gradient-1);
        }
        .auth-title {
            text-align: center;
            margin-bottom: 40px;
            font-size: 36px;
            font-weight: 700;
            background: var(--gradient-1);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
        }
        .auth-subtitle {
            text-align: center;
            margin-bottom: 40px;
            color: var(--text-secondary);
            font-size: 18px;
        }
        .auth-tabs {
            display: flex;
            margin-bottom: 40px;
            background-color: var(--background-color);
            border-radius: 15px;
            padding: 8px;
            box-shadow: inset 0 2px 4px rgba(0, 0, 0, 0.06);
        }
        .auth-tab {
            flex: 1;
            padding: 15px;
            text-align: center;
            cursor: pointer;
            border-radius: 12px;
            transition: all 0.3s ease;
            font-weight: 600;
            font-size: 16px;
            color: var(--text-secondary);
        }
        .auth-tab.active {
            background: var(--gradient-1);
            color: white;
            box-shadow: 0 4px 15px rgba(108, 99, 255, 0.3);
        }
        .auth-form {
            display: none;
        }
        .auth-form.active {
            display: block;
            animation: fadeIn 0.5s ease forwards;
        }
        /* Notification Styles */
        .notification {
            position: fixed;
            top: 30px;
            right: 30px;
            padding: 20px 30px;
            border-radius: 15px;
            color: white;
            box-shadow: var(--shadow);
            z-index: 1000;
            transform: translateX(120%);
            transition: transform 0.3s ease-in-out;
            display: flex;
            align-items: center;
            gap: 15px;
            max-width: 400px;
            font-weight: 500;
        }
        .notification.show {
            transform: translateX(0);
        }
        .notification.success {
            background: var(--gradient-3);
        }
        .notification.error {
            background: var(--gradient-2);
        }
        .notification.warning {
            background: var(--gradient-1);
        }
        .notification i {
            font-size: 24px;
        }
        /* Stats Section */
        .stats-container {
            display: flex;
            justify-content: space-between;
            margin-top: 30px;
            gap: 20px;
        }
        .stat-card {
            flex: 1;
            background-color: var(--background-color);
            border-radius: 15px;
            padding: 25px 15px;
            text-align: center;
            transition: all 0.3s ease;
            border: 1px solid rgba(108, 99, 255, 0.1);
        }
        .stat-card:hover {
            transform: translateY(-8px);
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.05);
            border: 1px solid rgba(108, 99, 255, 0.2);
        }
        .stat-value {
            font-size: 32px;
            font-weight: 800;
            background: var(--gradient-1);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            margin-bottom: 5px;
        }
        .stat-label {
            font-size: 16px;
            color: var(--text-secondary);
            font-weight: 500;
        }
        /* Public Message Form */
        .public-message-form {
            background-color: var(--card-color);
            border-radius: 25px;
            padding: 50px;
            box-shadow: var(--shadow);
            max-width: 700px;
            margin: 60px auto;
            text-align: center;
            border: 1px solid rgba(108, 99, 255, 0.1);
        }
        .public-message-form .panel-title {
            font-size: 32px;
            margin-bottom: 30px;
        }
        .public-recipient {
            font-size: 32px;
            font-weight: 700;
            background: var(--gradient-1);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            margin-bottom: 30px;
            padding: 15px;
            border-radius: 15px;
            background-color: var(--background-color);
            display: inline-block;
            min-width: 200px;
            border: 2px dashed rgba(108, 99, 255, 0.3);
        }
        /* Feature Cards */
        .features-section {
            margin-top: 60px;
            text-align: center;
        }
        .features-title {
            font-size: 32px;
            font-weight: 700;
            background: var(--gradient-1);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            margin-bottom: 50px;
        }
        .features-container {
            display: flex;
            justify-content: center;
            gap: 30px;
            flex-wrap: wrap;
        }
        .feature-card {
            flex: 1;
            min-width: 250px;
            max-width: 300px;
            background-color: var(--card-color);
            border-radius: 20px;
            padding: 30px;
            box-shadow: var(--shadow);
            transition: all 0.3s ease;
            border: 1px solid rgba(108, 99, 255, 0.1);
        }
        .feature-card:hover {
            transform: translateY(-10px);
            box-shadow: var(--shadow-hover);
            border: 1px solid rgba(108, 99, 255, 0.2);
        }
        .feature-icon {
            font-size: 48px;
            background: var(--gradient-1);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
            margin-bottom: 20px;
        }
        .feature-title {
            font-size: 22px;
            font-weight: 600;
            margin-bottom: 15px;
            color: var(--text-color);
        }
        .feature-description {
            color: var(--text-secondary);
            line-height: 1.6;
        }
        /* Footer */
        .footer {
            margin-top: 80px;
            padding: 40px 0;
            text-align: center;
            border-top: 1px solid var(--border-color);
            color: var(--text-secondary);
        }
        .footer-links {
            display: flex;
            justify-content: center;
            gap: 30px;
            margin-bottom: 20px;
        }
        .footer-links a {
            color: var(--primary-color);
            text-decoration: none;
            font-weight: 500;
            transition: all 0.3s ease;
        }
        .footer-links a:hover {
            color: var(--secondary-color);
        }
        /* Hidden Elements */
        .hidden {
            display: none;
        }
        /* Responsive Design */
        @media (max-width: 768px) {
            .main-content {
                flex-direction: column;
            }
            
            .auth-container {
                height: auto;
                padding: 20px 0;
            }
            
            .auth-card {
                padding: 40px 30px;
            }
            
            .stats-container {
                flex-direction: column;
            }
            
            .features-container {
                flex-direction: column;
                align-items: center;
            }
            
            .footer-links {
                flex-direction: column;
                gap: 15px;
            }
        }
        /* Loading Animation */
        .loader {
            width: 50px;
            height: 50px;
            border: 5px solid var(--background-color);
            border-top: 5px solid var(--primary-color);
            border-radius: 50%;
            animation: spin 1s linear infinite;
            margin: 20px auto;
        }
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
        /* Glow Effect */
        .glow {
            box-shadow: 0 0 20px rgba(108, 99, 255, 0.6);
        }
    </style>
</head>
<body>
    <div id="app">
        <!-- Authentication View -->
        <div id="auth-view" class="auth-container">
            <div class="auth-card fade-in">
                <h1 class="auth-title">
                    <i class="fas fa-user-secret"></i> An Anonymous
                </h1>
                <p class="auth-subtitle">Send and receive anonymous messages</p>
                
                <div class="auth-tabs">
                    <div class="auth-tab active" onclick="switchTab('login')">Login</div>
                    <div class="auth-tab" onclick="switchTab('register')">Register</div>
                </div>
                
                <!-- Login Form -->
                <form id="login-form" class="auth-form active">
                    <div class="form-group">
                        <label for="login-email">Email</label>
                        <input type="email" id="login-email" class="form-control" placeholder="Enter your email" required>
                    </div>
                    <div class="form-group">
                        <label for="login-password">Password</label>
                        <input type="password" id="login-password" class="form-control" placeholder="Enter your password" required>
                    </div>
                    <button type="submit" class="btn btn-primary" style="width: 100%;">
                        <i class="fas fa-sign-in-alt"></i> Login
                    </button>
                </form>
                
                <!-- Register Form -->
                <form id="register-form" class="auth-form">
                    <div class="form-group">
                        <label for="register-username">Username</label>
                        <input type="text" id="register-username" class="form-control" placeholder="Choose a username" required>
                    </div>
                    <div class="form-group">
                        <label for="register-email">Email</label>
                        <input type="email" id="register-email" class="form-control" placeholder="Enter your email" required>
                    </div>
                    <div class="form-group">
                        <label for="register-password">Password</label>
                        <input type="password" id="register-password" class="form-control" placeholder="Create a password" required>
                        <small style="color: var(--text-secondary); margin-top: 5px; display: block;">Password must be at least 6 characters</small>
                    </div>
                    <button type="submit" class="btn btn-primary" style="width: 100%;">
                        <i class="fas fa-user-plus"></i> Register
                    </button>
                </form>
                
                <div style="text-align: center; margin-top: 30px;">
                    <p style="color: var(--text-secondary); font-size: 14px;">
                        By signing up, you agree to our <a href="#" style="color: var(--primary-color);">Terms of Service</a> and <a href="#" style="color: var(--primary-color);">Privacy Policy</a>
                    </p>
                </div>
            </div>
        </div>
        
        <!-- Main App View -->
        <div id="app-view" class="container hidden">
            <header>
                <div class="logo float">
                    <i class="fas fa-user-secret"></i> An Anonymous
                </div>
                <div class="user-info">
                    <span id="user-username">User</span>
                    <div class="user-avatar" id="user-avatar">U</div>
                    <button class="btn btn-secondary" onclick="logout()">
                        <i class="fas fa-sign-out-alt"></i> Logout
                    </button>
                </div>
            </header>
            
            <div class="main-content">
                <!-- Left Panel - Send Message -->
                <div class="left-panel fade-in">
                    <h2 class="panel-title">
                        <i class="fas fa-paper-plane"></i>
                        Send Anonymous Message
                    </h2>
                    
                    <div class="form-group">
                        <label for="recipient">Recipient Username</label>
                        <input type="text" id="recipient" class="form-control" placeholder="Enter username">
                    </div>
                    
                    <div class="form-group">
                        <label for="message">Your Message</label>
                        <textarea id="message" class="form-control" rows="4" placeholder="Type your anonymous message here..."></textarea>
                    </div>
                    
                    <button class="btn btn-primary" onclick="sendMessage()">
                        <i class="fas fa-paper-plane"></i> Send Message
                    </button>
                    
                    <div class="form-group" style="margin-top: 40px;">
                        <label>Your Unique Link</label>
                        <div style="display: flex; gap: 15px;">
                            <input type="text" id="user-link" class="form-control" readonly>
                            <button class="btn btn-secondary" onclick="copyLink()">
                                <i class="fas fa-copy"></i> Copy
                            </button>
                        </div>
                        <p style="font-size: 14px; color: var(--text-secondary); margin-top: 10px;">
                            Share this link with others to receive anonymous messages
                        </p>
                    </div>
                    
                    <!-- Stats Section -->
                    <div class="stats-container">
                        <div class="stat-card">
                            <div class="stat-value" id="messages-received">0</div>
                            <div class="stat-label">Messages Received</div>
                        </div>
                        <div class="stat-card">
                            <div class="stat-value" id="messages-sent">0</div>
                            <div class="stat-label">Messages Sent</div>
                        </div>
                        <div class="stat-card">
                            <div class="stat-value" id="profile-views">0</div>
                            <div class="stat-label">Profile Views</div>
                        </div>
                    </div>
                </div>
                
                <!-- Right Panel - Inbox -->
                <div class="right-panel fade-in">
                    <h2 class="panel-title">
                        <i class="fas fa-inbox"></i>
                        Your Messages
                    </h2>
                    
                    <div id="message-list" class="message-list">
                        <!-- Messages will be loaded here -->
                        <div class="message-item">
                            <div class="message-header">
                                <span class="message-sender">Anonymous</span>
                                <span>Just now</span>
                            </div>
                            <div class="message-content">
                                Welcome to An Anonymous! This is a sample message.
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            
            <!-- Features Section -->
            <div class="features-section">
                <h2 class="features-title">Why Choose An Anonymous?</h2>
                <div class="features-container">
                    <div class="feature-card">
                        <div class="feature-icon">
                            <i class="fas fa-user-shield"></i>
                        </div>
                        <h3 class="feature-title">100% Anonymous</h3>
                        <p class="feature-description">
                            Send messages without revealing your identity. Your privacy is our top priority.
                        </p>
                    </div>
                    <div class="feature-card">
                        <div class="feature-icon">
                            <i class="fas fa-link"></i>
                        </div>
                        <h3 class="feature-title">Shareable Links</h3>
                        <p class="feature-description">
                            Get your unique link and share it anywhere for others to send you messages.
                        </p>
                    </div>
                    <div class="feature-card">
                        <div class="feature-icon">
                            <i class="fas fa-lock"></i>
                        </div>
                        <h3 class="feature-title">Secure & Private</h3>
                        <p class="feature-description">
                            Your messages are encrypted and only visible to you.
                        </p>
                    </div>
                </div>
            </div>
            
            <!-- Footer -->
            <div class="footer">
                <div class="footer-links">
                    <a href="#">About</a>
                    <a href="#">Privacy Policy</a>
                    <a href="#">Terms of Service</a>
                    <a href="#">Contact</a>
                </div>
                <p>&copy; 2023 An Anonymous. All rights reserved.</p>
            </div>
        </div>
        
        <!-- Public Message Form -->
        <div id="public-message-form" class="public-message-form hidden">
            <header style="position: static; margin-bottom: 30px; box-shadow: none; border: none;">
                <div class="logo" style="justify-content: center;">
                    <i class="fas fa-user-secret"></i> An Anonymous
                </div>
            </header>
            
            <h2 class="panel-title">
                <i class="fas fa-paper-plane"></i>
                Send Anonymous Message
            </h2>
            
            <div class="public-recipient" id="public-recipient">User</div>
            
            <div class="form-group">
                <label for="public-message">Your Message</label>
                <textarea id="public-message" class="form-control" rows="4" placeholder="Type your anonymous message here..."></textarea>
            </div>
            
            <button class="btn btn-primary pulse" onclick="sendPublicMessage()">
                <i class="fas fa-paper-plane"></i> Send Message
            </button>
            
            <div style="margin-top: 40px;">
                <p style="color: var(--text-secondary); font-size: 16px;">
                    Want to receive anonymous messages? 
                    <a href="#" onclick="showLoginForm()" style="color: var(--primary-color); font-weight: 600;">Create your own link</a>
                </p>
            </div>
        </div>
    </div>
    
    <!-- Notification -->
    <div id="notification" class="notification">
        <i class="fas fa-check-circle"></i>
        <span id="notification-text">Notification text</span>
    </div>
    
    <script>
        // Site configuration
        const siteConfig = {
            name: "An Anonymous",
            baseUrl: "https://smarfat.github.io/AnAnonymous.github.io"
        };
        
        // Initialize data from localStorage or use defaults
        function initializeData() {
            // Check if users data exists in localStorage
            let users = JSON.parse(localStorage.getItem('anonyUsers'));
            if (!users) {
                // Default users if none exist in localStorage
                users = [
                    { id: 1, username: 'demo', email: 'demo@example.com', password: 'password123' },
                    { id: 2, username: 'user1', email: 'user1@example.com', password: 'password123' },
                    { id: 3, username: 'user2', email: 'user2@example.com', password: 'password123' }
                ];
                localStorage.setItem('anonyUsers', JSON.stringify(users));
            }
            
            // Check if messages data exists in localStorage
            let messages = JSON.parse(localStorage.getItem('anonyMessages'));
            if (!messages) {
                // Default messages if none exist in localStorage
                messages = [
                    { id: 1, senderId: 2, recipientId: 1, content: 'This is a test message from user1 to demo', timestamp: new Date().toISOString() },
                    { id: 2, senderId: null, recipientId: 1, content: 'This is an anonymous message', timestamp: new Date().toISOString() },
                    { id: 3, senderId: 3, recipientId: 1, content: 'This is another message from user2', timestamp: new Date().toISOString() }
                ];
                localStorage.setItem('anonyMessages', JSON.stringify(messages));
            }
            
            // Check if stats data exists in localStorage
            let stats = JSON.parse(localStorage.getItem('anonyStats'));
            if (!stats) {
                // Default stats if none exist in localStorage
                stats = {
                    messagesReceived: 24,
                    messagesSent: 18,
                    profileViews: 142
                };
                localStorage.setItem('anonyStats', JSON.stringify(stats));
            }
            
            return {
                users: users,
                messages: messages,
                stats: stats
            };
        }
        
        // Save data to localStorage
        function saveData(data) {
            localStorage.setItem('anonyUsers', JSON.stringify(data.users));
            localStorage.setItem('anonyMessages', JSON.stringify(data.messages));
            localStorage.setItem('anonyStats', JSON.stringify(data.stats));
        }
        
        // Initialize app data
        let appData = initializeData();
        
        // Current user state
        let currentUser = null;
        
        // DOM elements
        const authView = document.getElementById('auth-view');
        const appView = document.getElementById('app-view');
        const publicMessageForm = document.getElementById('public-message-form');
        const loginForm = document.getElementById('login-form');
        const registerForm = document.getElementById('register-form');
        const notification = document.getElementById('notification');
        const notificationText = document.getElementById('notification-text');
        
        // Event listeners
        loginForm.addEventListener('submit', handleLogin);
        registerForm.addEventListener('submit', handleRegister);
        
        // Function to extract username from URL - improved for mobile
        function getUsernameFromURL() {
            let username = null;
            
            // Check for URL parameter first
            const urlParams = new URLSearchParams(window.location.search);
            const paramUsername = urlParams.get('sendto');
            if (paramUsername) {
                username = paramUsername;
            }
            
            // Check for hash-based username (e.g., #/username)
            if (!username) {
                const hash = window.location.hash;
                if (hash && hash.length > 1) {
                    const hashUsername = hash.substring(1); // Remove the #
                    // Check if it looks like a username
                    if (/^[a-zA-Z0-9_-]+$/.test(hashUsername)) {
                        username = hashUsername;
                    }
                }
            }
            
            // Try to extract from path (for GitHub Pages custom 404 page)
            if (!username) {
                const pathParts = window.location.pathname.split('/');
                // Remove empty parts and index.html if present
                const cleanParts = pathParts.filter(part => part && part !== 'index.html');
                
                // If we have a path part that could be a username
                if (cleanParts.length > 0) {
                    const potentialUsername = cleanParts[cleanParts.length - 1];
                    // Check if it looks like a username (alphanumeric, may include underscores or hyphens)
                    if (/^[a-zA-Z0-9_-]+$/.test(potentialUsername)) {
                        username = potentialUsername;
                    }
                }
            }
            
            // For mobile: check if the URL contains the baseUrl followed by a username
            if (!username && window.location.href.includes(siteConfig.baseUrl)) {
                const urlParts = window.location.href.split('/');
                const baseUrlParts = siteConfig.baseUrl.split('/');
                
                // Find where the baseUrl ends in the URL
                let startIndex = -1;
                for (let i = 0; i < baseUrlParts.length; i++) {
                    if (urlParts[i] !== baseUrlParts[i]) {
                        startIndex = i;
                        break;
                    }
                }
                
                // If we found the baseUrl, check the next part for a username
                if (startIndex === -1 && urlParts.length > baseUrlParts.length) {
                    const potentialUsername = urlParts[baseUrlParts.length];
                    if (/^[a-zA-Z0-9_-]+$/.test(potentialUsername)) {
                        username = potentialUsername;
                    }
                }
            }
            
            return username;
        }
        
        // Function to get or create a user by username
        function getOrCreateUser(username) {
            // Check if user already exists
            let user = appData.users.find(u => u.username === username);
            
            // If user doesn't exist, create a placeholder user
            if (!user) {
                user = {
                    id: appData.users.length + 1,
                    username: username,
                    email: `${username}@example.com`,
                    password: 'password123'
                };
                appData.users.push(user);
                saveData(appData);
            }
            
            return user;
        }
        
        // Check for saved user session on page load
        function checkUserSession() {
            const savedUserId = localStorage.getItem('anonyCurrentUserId');
            if (savedUserId) {
                const userId = parseInt(savedUserId);
                currentUser = appData.users.find(u => u.id === userId);
                if (currentUser) {
                    showAppView();
                    loadMessages();
                    updateStats();
                    return true;
                }
            }
            return false;
        }
        
        // Check URL parameters on page load
        window.addEventListener('DOMContentLoaded', () => {
            // Update page title
            document.title = siteConfig.name + " - Anonymous Messaging";
            
            // Update logo text
            const logoElements = document.querySelectorAll('.logo');
            logoElements.forEach(logo => {
                logo.innerHTML = `<i class="fas fa-user-secret"></i> ${siteConfig.name}`;
            });
            
            // Update auth title
            const authTitle = document.querySelector('.auth-title');
            if (authTitle) {
                authTitle.innerHTML = `<i class="fas fa-user-secret"></i> ${siteConfig.name}`;
            }
            
            // Check for saved user session first
            if (checkUserSession()) {
                return;
            }
            
            // Get username from URL
            const recipient = getUsernameFromURL();
            
            if (recipient) {
                // Always show the public message form, regardless of whether the user exists
                authView.classList.add('hidden');
                appView.classList.add('hidden');
                publicMessageForm.classList.remove('hidden');
                document.getElementById('public-recipient').textContent = recipient;
            }
        });
        
        // Switch between login and register tabs
        function switchTab(tab) {
            const tabs = document.querySelectorAll('.auth-tab');
            const forms = document.querySelectorAll('.auth-form');
            
            tabs.forEach(t => t.classList.remove('active'));
            forms.forEach(f => f.classList.remove('active'));
            
            if (tab === 'login') {
                tabs[0].classList.add('active');
                loginForm.classList.add('active');
            } else {
                tabs[1].classList.add('active');
                registerForm.classList.add('active');
            }
        }
        
        // Handle login form submission
        function handleLogin(e) {
            e.preventDefault();
            
            const email = document.getElementById('login-email').value;
            const password = document.getElementById('login-password').value;
            
            // Find user in database
            const user = appData.users.find(u => u.email === email && u.password === password);
            
            if (user) {
                currentUser = user;
                
                // Save user session
                localStorage.setItem('anonyCurrentUserId', user.id);
                
                showNotification('Login successful!', 'success');
                showAppView();
                loadMessages();
                updateStats();
                
                // Check if there's a stored recipient
                const storedRecipient = sessionStorage.getItem('recipient');
                if (storedRecipient) {
                    document.getElementById('recipient').value = storedRecipient;
                    sessionStorage.removeItem('recipient');
                }
            } else {
                showNotification('Invalid email or password', 'error');
            }
        }
        
        // Handle register form submission
        function handleRegister(e) {
            e.preventDefault();
            
            const username = document.getElementById('register-username').value;
            const email = document.getElementById('register-email').value;
            const password = document.getElementById('register-password').value;
            
            // Password validation
            if (password.length < 6) {
                showNotification('Password must be at least 6 characters long', 'error');
                return;
            }
            
            // Check if user already exists
            const userExists = appData.users.some(u => u.email === email || u.username === username);
            
            if (userExists) {
                showNotification('User with this email or username already exists', 'error');
                return;
            }
            
            // Create new user
            const newUser = {
                id: appData.users.length + 1,
                username,
                email,
                password
            };
            
            appData.users.push(newUser);
            saveData(appData);
            currentUser = newUser;
            
            // Save user session
            localStorage.setItem('anonyCurrentUserId', newUser.id);
            
            showNotification('Registration successful!', 'success');
            showAppView();
            loadMessages();
            updateStats();
        }
        
        // Show app view after login
        function showAppView() {
            authView.classList.add('hidden');
            publicMessageForm.classList.add('hidden');
            appView.classList.remove('hidden');
            
            // Update user info in header
            document.getElementById('user-username').textContent = currentUser.username;
            document.getElementById('user-avatar').textContent = currentUser.username.charAt(0).toUpperCase();
            
            // Generate and display user link with proper format
            const userLink = `${siteConfig.baseUrl}/?sendto=${currentUser.username}`;
            document.getElementById('user-link').value = userLink;
        }
        
        // Logout function
        function logout() {
            currentUser = null;
            localStorage.removeItem('anonyCurrentUserId');
            appView.classList.add('hidden');
            authView.classList.remove('hidden');
            
            // Reset forms
            loginForm.reset();
            registerForm.reset();
            switchTab('login');
            
            showNotification('You have been logged out', 'success');
        }
        
        // Send message function - fixed
        function sendMessage() {
            if (!currentUser) {
                showNotification('You must be logged in to send messages', 'error');
                return;
            }
            
            const recipientUsername = document.getElementById('recipient').value.trim();
            const messageContent = document.getElementById('message').value.trim();
            
            if (!recipientUsername || !messageContent) {
                showNotification('Please fill in all fields', 'error');
                return;
            }
            
            // Get or create recipient
            const recipient = getOrCreateUser(recipientUsername);
            
            // Create new message
            const newMessage = {
                id: appData.messages.length + 1,
                senderId: currentUser.id,
                recipientId: recipient.id,
                content: messageContent,
                timestamp: new Date().toISOString()
            };
            
            appData.messages.push(newMessage);
            saveData(appData);
            
            // Update stats
            appData.stats.messagesSent++;
            saveData(appData);
            updateStats();
            
            // Clear form
            document.getElementById('recipient').value = '';
            document.getElementById('message').value = '';
            
            showNotification('Message sent successfully!', 'success');
            
            // If recipient is current user, refresh messages
            if (recipient.id === currentUser.id) {
                loadMessages();
            }
            
            // Add animation to the send button
            const sendButton = event.target;
            sendButton.classList.add('pulse');
            setTimeout(() => {
                sendButton.classList.remove('pulse');
            }, 1000);
        }
        
        // Send public message function
        function sendPublicMessage() {
            const recipientUsername = document.getElementById('public-recipient').textContent;
            const messageContent = document.getElementById('public-message').value.trim();
            
            if (!messageContent) {
                showNotification('Please enter a message', 'error');
                return;
            }
            
            // Get or create recipient
            const recipient = getOrCreateUser(recipientUsername);
            
            // Create new message (anonymous)
            const newMessage = {
                id: appData.messages.length + 1,
                senderId: null, // null means anonymous
                recipientId: recipient.id,
                content: messageContent,
                timestamp: new Date().toISOString()
            };
            
            appData.messages.push(newMessage);
            saveData(appData);
            
            // Clear form
            document.getElementById('public-message').value = '';
            
            showNotification('Message sent successfully!', 'success');
            
            // Add animation to the send button
            const sendButton = event.target;
            sendButton.classList.add('pulse');
            setTimeout(() => {
                sendButton.classList.remove('pulse');
            }, 1000);
        }
        
        // Load messages for current user
        function loadMessages() {
            if (!currentUser) {
                return;
            }
            
            const messageList = document.getElementById('message-list');
            messageList.innerHTML = '';
            
            // Get messages for current user
            const userMessages = appData.messages.filter(m => m.recipientId === currentUser.id);
            
            if (userMessages.length === 0) {
                messageList.innerHTML = '<p style="text-align: center; color: var(--text-secondary);">No messages yet.</p>';
                return;
            }
            
            // Sort messages by timestamp (newest first) with better date handling
            userMessages.sort((a, b) => {
                const dateA = new Date(a.timestamp);
                const dateB = new Date(b.timestamp);
                return dateB - dateA;
            });
            
            // Display messages
            userMessages.forEach((message, index) => {
                const messageItem = document.createElement('div');
                messageItem.className = 'message-item';
                
                const sender = message.senderId ? appData.users.find(u => u.id === message.senderId) : null;
                const senderName = sender ? sender.username : 'Anonymous';
                
                const date = new Date(message.timestamp);
                const formattedDate = isNaN(date.getTime()) ? 'Invalid date' : date.toLocaleString();
                
                messageItem.innerHTML = `
                    <div class="message-header">
                        <span class="message-sender">${senderName}</span>
                        <span>${formattedDate}</span>
                    </div>
                    <div class="message-content">${message.content}</div>
                `;
                
                // Add animation with delay
                messageItem.style.animationDelay = `${index * 0.1}s`;
                messageItem.classList.add('fade-in');
                
                messageList.appendChild(messageItem);
            });
            
            // Update messages received stat
            appData.stats.messagesReceived = userMessages.length;
            saveData(appData);
            updateStats();
        }
        
        // Update stats
        function updateStats() {
            document.getElementById('messages-received').textContent = appData.stats.messagesReceived;
            document.getElementById('messages-sent').textContent = appData.stats.messagesSent;
            document.getElementById('profile-views').textContent = appData.stats.profileViews;
            
            // Simulate profile views increase
            if (Math.random() > 0.7) {
                appData.stats.profileViews++;
                saveData(appData);
            }
        }
        
        // Copy link function - updated to use modern Clipboard API
        function copyLink() {
            const linkInput = document.getElementById('user-link');
            
            if (navigator.clipboard) {
                // Modern approach
                navigator.clipboard.writeText(linkInput.value)
                    .then(() => {
                        showNotification('Link copied to clipboard!', 'success');
                    })
                    .catch(err => {
                        // Fallback to older method
                        linkInput.select();
                        document.execCommand('copy');
                        showNotification('Link copied to clipboard!', 'success');
                    });
            } else {
                // Fallback for older browsers
                linkInput.select();
                document.execCommand('copy');
                showNotification('Link copied to clipboard!', 'success');
            }
        }
        
        // Show notification - improved icon handling
        function showNotification(message, type) {
            notificationText.textContent = message;
            notification.className = `notification ${type}`;
            notification.classList.add('show');
            
            // Update icon based on type
            const icon = notification.querySelector('i');
            if (icon) {
                if (type === 'success') {
                    icon.className = 'fas fa-check-circle';
                } else if (type === 'error') {
                    icon.className = 'fas fa-exclamation-circle';
                } else if (type === 'warning') {
                    icon.className = 'fas fa-exclamation-triangle';
                }
            }
            
            setTimeout(() => {
                notification.classList.remove('show');
            }, 3000);
        }
        
        // Show login form
        function showLoginForm() {
            publicMessageForm.classList.add('hidden');
            authView.classList.remove('hidden');
        }
        
        // Add some interactive animations
        document.addEventListener('DOMContentLoaded', () => {
            // Add hover effect to buttons
            const buttons = document.querySelectorAll('.btn');
            buttons.forEach(button => {
                button.addEventListener('mouseenter', () => {
                    button.style.transform = 'translateY(-3px)';
                });
                
                button.addEventListener('mouseleave', () => {
                    button.style.transform = 'translateY(0)';
                });
            });
            
            // Add floating animation to logo
            const logo = document.querySelector('.logo');
            if (logo) {
                logo.classList.add('float');
            }
        });
    </script>
</body>
</html>
