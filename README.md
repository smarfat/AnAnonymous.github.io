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

        /* Header Styles */
        header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 20px 0;
            border-bottom: 1px solid var(--border-color);
            position: sticky;
            top: 0;
            background-color: var(--background-color);
            z-index: 100;
            backdrop-filter: blur(10px);
            background-color: rgba(248, 249, 250, 0.9);
        }

        .logo {
            font-size: 24px;
            font-weight: 700;
            color: var(--primary-color);
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .logo i {
            font-size: 28px;
        }

        .user-info {
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .user-avatar {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-weight: bold;
            box-shadow: 0 4px 8px rgba(108, 99, 255, 0.3);
            transition: transform 0.3s ease;
        }

        .user-avatar:hover {
            transform: scale(1.1);
        }

        .btn {
            padding: 10px 20px;
            border: none;
            border-radius: 30px;
            cursor: pointer;
            font-weight: 500;
            transition: all 0.3s ease;
            display: inline-flex;
            align-items: center;
            gap: 8px;
            position: relative;
            overflow: hidden;
            z-index: 1;
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
            background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
            color: white;
            box-shadow: 0 4px 15px rgba(108, 99, 255, 0.3);
        }

        .btn-primary:hover {
            transform: translateY(-2px);
            box-shadow: 0 6px 20px rgba(108, 99, 255, 0.4);
        }

        .btn-secondary {
            background-color: transparent;
            color: var(--primary-color);
            border: 1px solid var(--primary-color);
        }

        .btn-secondary:hover {
            background-color: rgba(108, 99, 255, 0.1);
            transform: translateY(-2px);
        }

        .btn-accent {
            background: linear-gradient(135deg, var(--accent-color), #ff5252);
            color: white;
            box-shadow: 0 4px 15px rgba(255, 107, 107, 0.3);
        }

        .btn-accent:hover {
            transform: translateY(-2px);
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
            border-radius: 15px;
            padding: 25px;
            box-shadow: var(--shadow);
            transition: all 0.3s ease;
        }

        .left-panel:hover, .right-panel:hover {
            box-shadow: var(--shadow-hover);
            transform: translateY(-5px);
        }

        .panel-title {
            font-size: 20px;
            margin-bottom: 20px;
            color: var(--primary-color);
            display: flex;
            align-items: center;
            gap: 10px;
            font-weight: 600;
        }

        .panel-title i {
            font-size: 24px;
        }

        /* Form Styles */
        .form-group {
            margin-bottom: 20px;
        }

        .form-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: 500;
            color: var(--text-secondary);
        }

        .form-control {
            width: 100%;
            padding: 12px 15px;
            border: 1px solid var(--border-color);
            border-radius: 10px;
            font-size: 16px;
            transition: all 0.3s ease;
        }

        .form-control:focus {
            outline: none;
            border-color: var(--primary-color);
            box-shadow: 0 0 0 3px rgba(108, 99, 255, 0.1);
        }

        textarea.form-control {
            resize: vertical;
            min-height: 120px;
        }

        /* Message List */
        .message-list {
            margin-top: 20px;
            max-height: 400px;
            overflow-y: auto;
        }

        .message-item {
            padding: 15px;
            border-radius: 10px;
            margin-bottom: 15px;
            background-color: var(--background-color);
            border-left: 4px solid var(--primary-color);
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        .message-item:hover {
            transform: translateX(5px);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
        }

        .message-header {
            display: flex;
            justify-content: space-between;
            margin-bottom: 8px;
            font-size: 14px;
            color: var(--text-secondary);
        }

        .message-sender {
            font-weight: 600;
            color: var(--primary-color);
        }

        .message-content {
            font-size: 16px;
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
            max-width: 450px;
            background-color: var(--card-color);
            border-radius: 20px;
            padding: 40px;
            box-shadow: var(--shadow);
            position: relative;
            overflow: hidden;
        }

        .auth-card:before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 5px;
            background: linear-gradient(90deg, var(--primary-color), var(--accent-color));
        }

        .auth-title {
            text-align: center;
            margin-bottom: 30px;
            color: var(--primary-color);
            font-size: 28px;
            font-weight: 700;
        }

        .auth-subtitle {
            text-align: center;
            margin-bottom: 30px;
            color: var(--text-secondary);
            font-size: 16px;
        }

        .auth-tabs {
            display: flex;
            margin-bottom: 30px;
            background-color: var(--background-color);
            border-radius: 10px;
            padding: 5px;
        }

        .auth-tab {
            flex: 1;
            padding: 12px;
            text-align: center;
            cursor: pointer;
            border-radius: 8px;
            transition: all 0.3s ease;
            font-weight: 500;
        }

        .auth-tab.active {
            background-color: var(--primary-color);
            color: white;
            box-shadow: 0 2px 10px rgba(108, 99, 255, 0.3);
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
            top: 20px;
            right: 20px;
            padding: 15px 25px;
            border-radius: 10px;
            color: white;
            box-shadow: var(--shadow);
            z-index: 1000;
            transform: translateX(120%);
            transition: transform 0.3s ease-in-out;
            display: flex;
            align-items: center;
            gap: 10px;
            max-width: 350px;
        }

        .notification.show {
            transform: translateX(0);
        }

        .notification.success {
            background: linear-gradient(135deg, var(--success-color), #27ae60);
        }

        .notification.error {
            background: linear-gradient(135deg, var(--accent-color), #e74c3c);
        }

        .notification.warning {
            background: linear-gradient(135deg, var(--warning-color), #e67e22);
        }

        /* Stats Section */
        .stats-container {
            display: flex;
            justify-content: space-between;
            margin-top: 20px;
            gap: 15px;
        }

        .stat-card {
            flex: 1;
            background-color: var(--background-color);
            border-radius: 10px;
            padding: 15px;
            text-align: center;
            transition: all 0.3s ease;
        }

        .stat-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
        }

        .stat-value {
            font-size: 24px;
            font-weight: 700;
            color: var(--primary-color);
        }

        .stat-label {
            font-size: 14px;
            color: var(--text-secondary);
            margin-top: 5px;
        }

        /* Public Message Form */
        .public-message-form {
            background-color: var(--card-color);
            border-radius: 15px;
            padding: 30px;
            box-shadow: var(--shadow);
            max-width: 600px;
            margin: 40px auto;
            text-align: center;
        }

        .public-recipient {
            font-size: 24px;
            font-weight: 600;
            color: var(--primary-color);
            margin-bottom: 20px;
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
                padding: 30px 20px;
            }
            
            .stats-container {
                flex-direction: column;
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
            box-shadow: 0 0 15px rgba(108, 99, 255, 0.6);
        }

        /* Gradient Text */
        .gradient-text {
            background: linear-gradient(90deg, var(--primary-color), var(--accent-color));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            background-clip: text;
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
                    </div>
                    <button type="submit" class="btn btn-primary" style="width: 100%;">
                        <i class="fas fa-user-plus"></i> Register
                    </button>
                </form>
                
                <div style="text-align: center; margin-top: 20px;">
                    <p style="color: var(--text-secondary); font-size: 14px;">
                        By signing up, you agree to our <a href="#" style="color: var(--primary-color);">Terms of Service</a> and <a href="#" style="color: var(--primary-color);">Privacy Policy</a>
                    </p>
                </div>
            </div>
        </div>
        
        <!-- Main App View -->
        <div id="app-view" class="container hidden">
            <header>
                <div class="logo">
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
                    
                    <div class="form-group" style="margin-top: 30px;">
                        <label>Your Unique Link</label>
                        <div style="display: flex; gap: 10px;">
                            <input type="text" id="user-link" class="form-control" readonly>
                            <button class="btn btn-secondary" onclick="copyLink()">
                                <i class="fas fa-copy"></i> Copy
                            </button>
                        </div>
                        <p style="font-size: 14px; color: var(--text-secondary); margin-top: 8px;">
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
        </div>
        
        <!-- Public Message Form -->
        <div id="public-message-form" class="public-message-form hidden">
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
            
            <div style="margin-top: 30px;">
                <p style="color: var(--text-secondary); font-size: 14px;">
                    Want to receive anonymous messages? 
                    <a href="#" onclick="showLoginForm()" style="color: var(--primary-color); font-weight: 500;">Create your own link</a>
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
            domain: "ananonymous.com"
        };
        
        // Mock database for demo purposes
        const mockUsers = [
            { id: 1, username: 'demo', email: 'demo@example.com', password: 'password123' },
            { id: 2, username: 'user1', email: 'user1@example.com', password: 'password123' },
            { id: 3, username: 'user2', email: 'user2@example.com', password: 'password123' }
        ];
        
        const mockMessages = [
            { id: 1, senderId: 2, recipientId: 1, content: 'This is a test message from user1 to demo', timestamp: new Date().toISOString() },
            { id: 2, senderId: null, recipientId: 1, content: 'This is an anonymous message', timestamp: new Date().toISOString() },
            { id: 3, senderId: 3, recipientId: 1, content: 'This is another message from user2', timestamp: new Date().toISOString() }
        ];
        
        // Mock stats
        const mockStats = {
            messagesReceived: 24,
            messagesSent: 18,
            profileViews: 142
        };
        
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
            
            const urlParams = new URLSearchParams(window.location.search);
            const recipient = urlParams.get('sendto');
            
            if (recipient) {
                // Check if recipient exists
                const userExists = mockUsers.some(u => u.username === recipient);
                
                if (userExists) {
                    if (!currentUser) {
                        // Show public message form
                        authView.classList.add('hidden');
                        appView.classList.add('hidden');
                        publicMessageForm.classList.remove('hidden');
                        document.getElementById('public-recipient').textContent = recipient;
                    } else {
                        // If user is logged in, prefill the recipient field
                        document.getElementById('recipient').value = recipient;
                    }
                } else {
                    showNotification('User not found', 'error');
                }
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
            
            // Find user in mock database
            const user = mockUsers.find(u => u.email === email && u.password === password);
            
            if (user) {
                currentUser = user;
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
            
            // Check if user already exists
            const userExists = mockUsers.some(u => u.email === email || u.username === username);
            
            if (userExists) {
                showNotification('User with this email or username already exists', 'error');
                return;
            }
            
            // Create new user
            const newUser = {
                id: mockUsers.length + 1,
                username,
                email,
                password
            };
            
            mockUsers.push(newUser);
            currentUser = newUser;
            
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
            const userLink = `https://${siteConfig.domain}/${currentUser.username}`;
            document.getElementById('user-link').value = userLink;
        }
        
        // Logout function
        function logout() {
            currentUser = null;
            appView.classList.add('hidden');
            authView.classList.remove('hidden');
            
            // Reset forms
            loginForm.reset();
            registerForm.reset();
            switchTab('login');
            
            showNotification('You have been logged out', 'success');
        }
        
        // Send message function
        function sendMessage() {
            if (!currentUser) {
                showNotification('You must be logged in to send messages', 'error');
                return;
            }
            
            const recipientUsername = document.getElementById('recipient').value;
            const messageContent = document.getElementById('message').value;
            
            if (!recipientUsername || !messageContent) {
                showNotification('Please fill in all fields', 'error');
                return;
            }
            
            // Find recipient
            const recipient = mockUsers.find(u => u.username === recipientUsername);
            
            if (!recipient) {
                showNotification('User not found', 'error');
                return;
            }
            
            // Create new message
            const newMessage = {
                id: mockMessages.length + 1,
                senderId: currentUser.id,
                recipientId: recipient.id,
                content: messageContent,
                timestamp: new Date().toISOString()
            };
            
            mockMessages.push(newMessage);
            
            // Update stats
            mockStats.messagesSent++;
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
            const messageContent = document.getElementById('public-message').value;
            
            if (!messageContent) {
                showNotification('Please enter a message', 'error');
                return;
            }
            
            // Find recipient
            const recipient = mockUsers.find(u => u.username === recipientUsername);
            
            if (!recipient) {
                showNotification('User not found', 'error');
                return;
            }
            
            // Create new message (anonymous)
            const newMessage = {
                id: mockMessages.length + 1,
                senderId: null, // null means anonymous
                recipientId: recipient.id,
                content: messageContent,
                timestamp: new Date().toISOString()
            };
            
            mockMessages.push(newMessage);
            
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
            if (!currentUser) return;
            
            const messageList = document.getElementById('message-list');
            messageList.innerHTML = '';
            
            // Get messages for current user
            const userMessages = mockMessages.filter(m => m.recipientId === currentUser.id);
            
            if (userMessages.length === 0) {
                messageList.innerHTML = '<p style="text-align: center; color: var(--text-secondary);">No messages yet.</p>';
                return;
            }
            
            // Sort messages by timestamp (newest first)
            userMessages.sort((a, b) => new Date(b.timestamp) - new Date(a.timestamp));
            
            // Display messages
            userMessages.forEach((message, index) => {
                const messageItem = document.createElement('div');
                messageItem.className = 'message-item';
                
                const sender = message.senderId ? mockUsers.find(u => u.id === message.senderId) : null;
                const senderName = sender ? sender.username : 'Anonymous';
                
                const date = new Date(message.timestamp);
                const formattedDate = date.toLocaleString();
                
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
            mockStats.messagesReceived = userMessages.length;
            updateStats();
        }
        
        // Update stats
        function updateStats() {
            document.getElementById('messages-received').textContent = mockStats.messagesReceived;
            document.getElementById('messages-sent').textContent = mockStats.messagesSent;
            document.getElementById('profile-views').textContent = mockStats.profileViews;
            
            // Simulate profile views increase
            if (Math.random() > 0.7) {
                mockStats.profileViews++;
            }
        }
        
        // Copy link function
        function copyLink() {
            const linkInput = document.getElementById('user-link');
            linkInput.select();
            document.execCommand('copy');
            showNotification('Link copied to clipboard!', 'success');
        }
        
        // Show notification
        function showNotification(message, type) {
            notificationText.textContent = message;
            notification.className = `notification ${type}`;
            notification.classList.add('show');
            
            // Update icon based on type
            const icon = notification.querySelector('i');
            if (type === 'success') {
                icon.className = 'fas fa-check-circle';
            } else if (type === 'error') {
                icon.className = 'fas fa-exclamation-circle';
            } else if (type === 'warning') {
                icon.className = 'fas fa-exclamation-triangle';
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
                    button.style.transform = 'translateY(-2px)';
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
